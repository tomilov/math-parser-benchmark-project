# The Great C++ Mathematical Expression Parser Benchmark #


This is a benchmark suite for different implementations of open source math expression parsers and evaluators written in C++. Currently the following expression parsers are part of this benchmark:


| **#** | **Library** | **Author** | **License** |
|:------|:------------|:-----------|:------------|
|00     | [ATMSP](http://sourceforge.net/projects/atmsp/)     | Heinz von Saanen | [GPL v3](http://www.opensource.org/licenses/gpl-3.0.html) |
|01     | [ExprTk](http://www.partow.net/programming/exprtk/) | Arash Partow     | [CPL v1.0](http://www.opensource.org/licenses/cpl1.0.php) |
|02     | [FParser](http://warp.povusers.org/FunctionParser/) | Juha Nieminen & Joel Yliluoma | [LGPL](http://www.gnu.org/copyleft/lesser.html) |
|03     | [Lepton](https://simtk.org/home/lepton)    | Peter Eastman |[MIT](http://www.opensource.org/licenses/mit-license.php) |
|04     | [MathExpr](http://www.yann-ollivier.org/mathlib/mathexpr)  | Yann Ollivier | [Copyright Notice 1997-2000](http://www.yann-ollivier.org/mathlib/mathexpr#C) |
|05     | [MTParser](http://www.codeproject.com/Articles/7335/An-extensible-math-expression-parser-with-plug-ins)  | Mathieu Jacques | [CPOL](http://www.codeproject.com/info/cpol10.aspx) |
|06     | [muParser](http://muparser.beltoforion.de/)  | Ingo Berg  | [MIT](http://www.opensource.org/licenses/mit-license.php) |
|07     | [muParserX](http://muparserx.beltoforion.de/) | Ingo Berg  | [MIT](http://www.opensource.org/licenses/mit-license.php) |



**Note:** This archive is not meant as a primary source for any of the libraries listed above as it may contain outdated versions of said libraries.


---


# Explanation #

## The Setup ##
The benchmark takes two parameters:
  1. Number of iterations (N)
  1. Benchmark Test File

The benchmark files are as follows:

  * [bench\_expr.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr.txt)
  * [bench\_expr\_all.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr_all.txt)
  * [bench\_expr\_all\_permutations.txt](https://math-parser-benchmark-project.googlecode.com/svn/trunk/bench_expr_all_permutations.txt)
  * [bench\_expr\_complete.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr_complete.txt)
  * [bench\_expr\_extensive.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr_extensive.txt)
  * [bench\_expr\_precedence.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr_precedence.txt)
  * [bench\_expr\_random\_with\_functions.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr_random_with_functions.txt)
  * [bench\_expr\_random\_without\_functions.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr_random_without_functions.txt)
  * [bench\_expr\_weird.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr_weird.txt)

As an example, the following execution will use the _"[bench\_expr\_all.txt](http://code.google.com/p/math-parser-benchmark-project/source/browse/trunk/bench_expr_all.txt)"_ set of expressions, executing each expression 100000 times.

```
ParserBench.exe 100000 bench_expr_all.txt
```


## The Rounds ##
For every expression in the benchmark file, every parser evaluates the given expression N times, this is known as a round. The total time each parser takes to evaluate the expression N times is recorded. Ranking of the parsers for the round is done from the fastest to the slowest.

Parsers that can't parse the expression or produce a result different to the expected result _(based on a normalized epsilon approach)_ are disqualified for the round and do not participate in point accumulation.

## The Summary ##
Once all the expressions have been completed, a summary is provided, that includes information relating to the build parameters of the benchmark binary, the architecture which the benchmark was run upon, a final ranking of the parsers, and a listing of expressions per parser that were deemed as disqualified during the benchmark.

## The Results ##
The summaries of runs of the benchmark suite upon various architectures can be found here: [Results](https://code.google.com/p/math-parser-benchmark-project/source/browse/#svn/trunk/logs).


---


# Example Results #

The following is a chart depicting the results as executions per second obtained by running the ['bench\_expr\_random\_without\_functions.txt'](http://math-parser-benchmark-project.googlecode.com/svn/trunk/bench_expr_random_without_functions.txt) benchmark, using the _double_ type, 500000 iterations per expression on an Intel Xeon W3680 3GHz. The horizontal measure on the chart is the length of the expression in bytes.

![http://www.partow.net/experimental/images/benchmark_result.png](http://www.partow.net/experimental/images/benchmark_result.png)

**Note:** The parsers muParserSSE and ExprTKFloat were excluded due to their use of the _float_ type, and the Lepton and muParserX parsers were excluded due to the fact that their results were consistently 2-3 orders of magnitude slower than all the others.