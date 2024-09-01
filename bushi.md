% This LaTeX document needs to be compiled with XeLaTeX.  
\\documentclass\[10pt\]{article}  
\\usepackage\[utf8\]{inputenc}  
\\usepackage{amsmath}  
\\usepackage{amsfonts}  
\\usepackage{amssymb}  
\\usepackage\[version=4\]{mhchem}  
\\usepackage{stmaryrd}  
\\usepackage{graphicx}  
\\usepackage\[export\]{adjustbox}  
\\graphicspath{ {./images/} }  
\\usepackage{hyperref}  
\\hypersetup{colorlinks=true, linkcolor=blue, filecolor=magenta, urlcolor=cyan,}  
\\urlstyle{same}  
\\usepackage\[fallback\]{xeCJK}  
\\usepackage{polyglossia}  
\\usepackage{fontspec}  
\\setCJKmainfont{Noto Serif CJK JP}

\\setmainlanguage{english}  
\\setmainfont{CMU Serif}

\\title{マクローリン展開を使ってsinの近似値 }

\\author{}  
\\date{}

\\begin{document}  
\\maketitle  
\\section\*{を求める関数を実装する\!}  
\\section\*{はじめに}  
私は今回初めて部誌を書くのですが、マクローリン展開がとても面白い と思ったので今回書いてみました。できるだけ、数学が分からない人でも 読んでマクローリン展開の面白さや凄さが伝えられるようにしたいと思い ます。\\\\  
さて、これから色々な数式が出てくるのですが、最初に出てくる記号等 の補足を入れたいと思います。知っている人は読み飛ばしてください。 $f(x)$ とは、 $x$ の関数を意味しています。\\\\  
$\\sum\_{k=0}^{a} f(k)$ とは、 $f(k)$ において $k=0$ から $a$ まで代入したときの総和を表しています。\\\\  
なので、 $\\sum\_{k=0}^{a} f(k)=f(0)+f(1)+\\ldots .+f(a)$ ということになります。\\\\  
$f^{(n)}(x)$ とは $f(x)$ の第 $n$ 次導関数を意味していて、 $f(x)$ の $n$ 階微分ともいいます。\\\\  
$n\!$ とは非負整数（負ではない整数つまり $0,1,2 \\ldots$ ）\\\\  
$n$ に対して1から $n$ までの積の値で、 $n$ の階乗\\\\  
です。つまり、 $n\!=1 \* 2 \* 3 \* \\ldots \* n$ となります。\\\\  
（ $n$ の階乗もガンマ関数で定義することで非負整数から正の実数まで拡\\\\  
張することができ、面白いのですがここでは取り扱いません)\\\\  
区間 $\[a, b\]$ とは閉区間\[a,b\]ともいい、a以上b以下の数の集合です。

\\section\*{マクローリン展開とは?}  
$f(x)=\\sum\_{k=0}^{\\infty} f^{(k)}(0) \\frac{x^{k}}{k\!}$\\\\  
下の式は無限回微分可能で右辺の級数が収束するような関数 $f(x)$ につ いて成立する式です。\\\\  
マクローリン展開とはこの式において、 $f(x)$ を左辺のように展開すること です。この無限級数を途中まで計算すると、多項式になり $f(x)$ を多項式 で近似することができます。マクローリン展開の面白いところは、複雑な 関数で表された曲線を多項式で近似できるところです。\\\\  
$\\operatorname{sinx}$ を実際にマクローリン展開してみる\\\\  
① だとよく分からないかもしれない人もいるかもしれないので、まず（1）の 右辺の級数を展開をしてみましょう。\\\\  
$f(x)=f^{\\prime}(0) \\frac{x}{1\!}+f^{\\prime \\prime}(0) \\frac{x^{2}}{2\!}+f^{\\prime \\prime \\prime}(0) \\frac{x^{3}}{3\!}+\\ldots \\ldots$.\\\\  
と、右辺はなっています。\\\\  
ここで、 $\\sin x$ のn階導関数を求めると、\\\\  
$\\sin x$ を微分していくと $\\cos x,-\\sin x,-\\cos x, \\sin x, \\ldots$. となるので、

$$  
\\begin{aligned}  
\\sin ^{(n)} x= & \\{\\cos x(n=1,5,9 \\ldots \\text { のとき }),-\\sin x(n=2,6,10 \\ldots \\text { のとき }),), \\\\  
& \-\\cos x(n=3,7,11 \\ldots) \\text { のとき、 } \\sin x(n=4,8,12 \\ldots \\text { のとき })\\}  
\\end{aligned}  
$$

なります。\\\\  
よって、 $\\sin x$ のマクローリン展開は次のようになります。

$$  
\\begin{aligned}  
& \\sin x=\\cos 0 \\frac{x}{1\!}-\\sin 0 \\frac{x^{2}}{2\!}-\\cos 0 \\frac{x^{3}}{3\!}+\\sin 0 \\frac{x^{4}}{4\!}+\\cos 0 \\frac{x^{5}}{5\!}+\\ldots . \\\\  
& \=x-\\frac{x^{3}}{3\!}+\\frac{x^{5}}{5\!}+\\ldots . . \\\\  
& \=\\sum\_{k=0}^{\\infty}(-1)^{k} \\frac{x^{2 k+1}}{(2 k+1)\!} \\cdots \\text { (2) }  
\\end{aligned}  
$$

JavaScriptで実際に実装してみる\\\\  
$\\operatorname{sinx}$ のマクローリン展開が出来たので実際にJavaScriptを使って実装してみようと思 コードは以下のようになります。

\\begin{center}  
\\includegraphics\[max width=\\textwidth\]{2024\_09\_01\_7adb9b1302790f0c8e16g-3}  
\\end{center}

コンソールに出カした結果 $\\downarrow$

\\section\*{$\\sin (0)=0$ \\\\  
 $\\sin (\\pi / 6)=0.49999999999999994$ \\\\  
 $\\sin (\\pi / 4)=0.7071067811865475$}  
ということで、実際の値は\\\\  
$\\sin 0=0, \\sin \\frac{\\pi}{6}=0.5, \\sin \\frac{\\pi}{4}=\\frac{\\sqrt{2}}{2}=0.707106781187 . .$. となるので\\\\  
（2）で $k=50$ まで計算するだけでもかなりの精度があり、よく近似出来て いることが分かります。例えば、 $\\sin \\frac{\\pi}{4}$ では小数点第 11 桁まで正しい値に なっています。\\\\  
このコードではfactorize関数で階乗の値を求め、 $\\sin (x)$ 関数で $\\sin (x)$ の 値をマクローリン展開にk=50まで代入して近似しています。次から、ロルの定理 $\\rightarrow$ テイラ一の定理 $\\rightarrow$ テイラ一展開 $\\rightarrow$ マクローリン展開の順に証明したいと思います。

\\section\*{ロルの定理}  
\\section\*{ロルの定理の前に最大値の定理は認めたいと思います。}  
\\section\*{最大値の定理}  
区間 $\[a, b\]$ で連続な関数 $f(x)$ は最大値を持つ

\\section\*{ここから実際に証明に入ります。}  
\\section\*{ロルの定理}  
\\section\*{区間\[a,b\]で連続、(a,b)で微分可能で}  
$f(a)=f(b)$ となる関数 $f(x)$ において\\\\  
$f^{\\prime}(c)=0$ かつ $a\<c\<b$ を満たす $c$ が存在する\\\\  
(証明)\\\\  
( i ) $f(x)$ が区間内で定数関数のとき\\\\  
$a\<c\<b$ を満たす、すべての $c$ において $f^{\\prime}(c)=0$ が成り立つ\\\\  
( ii ) $f(x)$ が区間内で定数関数ではないとき\\\\  
$f(x)$ が区間内で定数関数でないので\\\\  
$f(k)\>f(a), a\<k\<b$ を満たす $k$ が存在するとき\\\\  
最大値の定理より $a\<c\<b$ を満たし $f(c)$ が区間内で最大になるような $c$ が存在する。 これから $f^{\\prime}(c)$ を証明する。 $\\forall x \\in\[a, b\]$ に対して $f(c) \\geq f(x)$ なので、\\\\  
$\\lim \_{h \\rightarrow+0} \\frac{f(c+h)-f(c)}{h} \\leq 0, \\lim \_{h \\rightarrow-0} \\frac{f(c+h)-f(c)}{h} \\geq 0$ が成り立ち、\\\\  
$f(c)$ で微分可能なので $\\lim \_{h \\rightarrow+0} \\frac{f(c+h)-f(c)}{h}=\\lim \_{h \\rightarrow-0} \\frac{f(c+h)-f(c)}{h}$ が成り立つ

よって、 $\\lim \_{h \\rightarrow 0} \\frac{f(c+h)-f(c)}{h}=0$ となるので $f^{\\prime}(c)=0$ が成り立つ。\\\\  
$f(k)\<f(a), a\<k\<b$ を満たす $k$ が存在するときは最小値を考え同様にできる\\\\  
(Q.E.D)

\\section\*{テイラーの定理}  
閉区間 $\[a, x\]$ で $n$ 回微分可能な関数 $f(x)$ について、\\\\  
$f(x)=\\sum\_{k=0}^{n-1} f^{(k)}(a) \\frac{(x-a)^{k}}{k\!}+f^{(n)}(c) \\frac{(x-a)^{n}}{n\!}$

\\section\*{を満たす $a\<c\<x$ が存在する}  
(証明)\\\\  
$f(b)=\\sum\_{k=0}^{n-1} f^{(k)}(a) \\frac{(b-a)^{k}}{k\!}+A \\frac{(b-a)^{n}}{n\!}$ となるような定数 $A$ をおく。\\\\  
ここで、

$$  
\\begin{aligned}  
g(x) & \=f(b)-f(x)-\\sum\_{k=1}^{n-1} f^{(k)}(x) \\frac{(b-x)^{k}}{k\!}-A \\frac{(b-x)^{n}}{n\!} \\text { とおくと } \\\\  
g(a) & \=f(b)-f(a)-\\sum\_{k=1}^{n-1} f^{(k)}(a) \\frac{(b-a)^{k}}{k\!}-A \\frac{(b-a)^{n}}{n\!} \\\\  
& \=f^{(0)}(a) \\frac{(b-a)^{0}}{0\!}-f(a) \\\\  
& \=0  
\\end{aligned}  
$$

$$  
\\begin{aligned}  
g(b) & \=f(b)-f(b)-\\sum\_{k=1}^{n-1} f^{(k)}(b) \\frac{(b-b)^{k}}{k\!}-A \\frac{(b-b)^{n}}{n\!} \\\\  
& \=0  
\\end{aligned}  
$$

よつて、ロルの定理より $g^{\\prime}(c)=0$ かつ $a\<c\<b$ となる $c$ が存在する。\\\\  
$a\<x\<b$ において $g(x)$ を微分すると

$$  
\\begin{aligned}  
g^{\\prime}(x) & \=-f^{\\prime}(x)-\\sum\_{k=1}^{n-1}\\left(f^{(k+1)}(x) \\frac{(b-x)^{k}}{k\!}-f^{(k)}(x) k \\frac{(b-x)^{k-1}}{k\!}\\right)+A n \\frac{(b-x)^{n-1}}{n\!} \\\\  
& \=-f^{(0+1)}(x) \\frac{(b-x)^{0}}{0\!}-\\sum\_{k=1}^{n-1} f^{(k+1)}(x) \\frac{(b-x)^{k}}{k\!}+\\sum\_{k=1}^{n-1} f^{(k)}(x) \\frac{(b-x)^{k-1}}{(k-1)\!}+A \\frac{(b-x)^{n-1}}{(n-1)\!} \\\\  
& \=-\\sum\_{k=0}^{n-1} f^{(k+1)}(x) \\frac{(b-x)^{k}}{k\!}+\\sum\_{k=1}^{n-1} f^{(k)}(x) \\frac{(b-x)^{k-1}}{(k-1)\!}+A \\frac{(b-x)^{n-1}}{(n-1)\!} \\\\  
& \=-f^{(n)}(x) \\frac{(b-x)^{n-1}}{(n-1)\!}+A \\frac{(b-x)^{n-1}}{(n-1)\!} \\\\  
& \=\\frac{(b-x)^{n-1}}{(n-1)\!}\\left(A-f^{(n)}(x)\\right)  
\\end{aligned}  
$$

また、 $g^{\\prime}(c)=0$ より $\\frac{(b-c)^{n-1}}{(n-1)\!}\\left(A-f^{(n)}(c)\\right)=0$ が成り立ち\\\\  
$c\<b$ より $b-c \\neq 0$ なので $\\frac{(b-c)^{n-1}}{(n-1)\!} \\neq 0$ より $A=f^{(n)}(c)$\\\\  
よって、閉区間 $\[a, x\]$ で $n$ 回微分可能な関数 $f(x)$ について、\\\\  
$f(x)=\\sum\_{k=0}^{n-1} f^{(k)}(a) \\frac{(x-a)^{k}}{k\!}+f^{(n)}(c) \\frac{(x-a)^{n}}{n\!}$\\\\  
を満たす $a\<c\<x$ が存在する\\\\  
(Q.E.D)

\\section\*{テイラ一展開}  
テイラーの定理において、 $n \\rightarrow \\infty$ のときを考えると、\\\\  
$f(x)=\\sum\_{k=0}^{\\infty} f^{(k)}(a) \\frac{(x-a)^{k}}{k\!}+f^{(n)}(c) \\frac{(x-a)^{n}}{n\!}$ は、\\\\  
シグマの部分は $n-1$ 次の多項式となっていて、\\\\  
誤差 $R\_{n}=\\frac{f^{(n)}(c)}{n\!}(x-a)^{n}$ とすると\\\\  
n階微分がべき乗で抑えられるすなわち、\\\\  
$A$ ， $B$ を定数として、すべての $n と x$ について $f^{(n)}\\left(x\_{0}\\right) \\leq A B^{n}$ が成り立つと き、\\\\  
$R\_{n}=\\frac{f^{(n)}(c)}{n\!}(x-a)^{n} \\leq \\frac{A B^{n}}{n\!}(x-a)^{n}=A \\frac{(B(x-a))^{n}}{n\!}$ となり、\\\\  
一般に $\\frac{m^{n+1}}{m^{n}}=m, \\frac{(n+1)\!}{n\!}=n$ より $n \\rightarrow \\infty$ において、階乗の方が指数関数 よりも発散速度が速いので $\\lim \_{n \\rightarrow \\infty} R\_{n}=0$ となります。\\\\  
よって、 $A, B$ を定数として、すべての $n$ と $x\_{0}$ について $f^{(n)}\\left(x\_{0}\\right) \\leq A B^{n}$ が成 り立つとき、\\\\  
$f(x)=\\sum\_{k=0}^{\\infty} f^{(k)}(a) \\frac{(x-a)^{k}}{k\!}$ が成り立つ。

\\section\*{マクローリン展開}  
テイラー展開において $a=0$ とすると、\\\\  
$f(x)=\\sum\_{k=0}^{\\infty} f^{(k)}(0) \\frac{x^{k}}{k\!}$ が成り立つ。これがマクローリン展開です。\\\\  
ここで、 $\\sin x$ のマローリン展開ができるかどうか、すなわち、\\\\  
$A, B$ を定数として、すべての $n$ について $f^{(n)}(0) \\leq A B^{n}$ が成り立つかどう か確認してみましょう。

すべての非負整数 $n$ と $x$ に対して $\\left|\\sin ^{(n)} x\\right| \\leq 1$ より\\\\  
マクローリン展開ができることが分かる。

\\section\*{最後に}  
今回、色々確認、参考にしながら書いたのですが、書いていてなかなか初学の人には説明が分 かりにくいところも多くあり、式変形などを詳しく書いたつもりなのですが、理解できたでしょうか？文章も拙いところもありますが、最後まで長々読んでくださりありがとうございました。

\\section\*{参考文献}  
\\href{https://manabitimes.jp/math/570\#2}{https://manabitimes.jp/math/570\\\#2}\\\\  
\\href{https://manabitimes.jp/math/1001\#3}{https://manabitimes.jp/math/1001\\\#3}\\\\  
\\href{https://manabitimes.jp/math/1158}{https://manabitimes.jp/math/1158}

\\end{document}