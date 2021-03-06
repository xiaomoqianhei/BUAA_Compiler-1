## 算术表达式属性翻译程序

### 原文法

1. E→E+T@ADD
2. E→T
3. T→T*F@MULT
4. T→F
5. F→(E)
6. F→Id

由于文法中存在左递归，需要消除。

### 新文法

1. E→T{+T@ADD}
2. T→F{*F@MULT}
3. F→(E)|Id

### 功能

通过属性翻译程序，将in.txt中的算数表达式翻译成四元式，写入out.txt中。

### 输入

算数表达式。由于没有添加词法分析程序，Id应为单个的小写字母。算数符号为乘号(*)或加号(+)。

* 样例

a+b+c\*d+(e+f)\*g+h\*(i+j)

### 输出

四元式，格式为：运算符 @左操作数地址 @右操作数地址 @结果地址

* 样例

ADD @0		@4		@8

MULT@12	@16	@20

ADD @8		@20	@24

ADD @28	@32	@36

MULT@36	@40	@44

ADD @24	@44	@48

ADD @56	@60	@64

MULT@52	@64	@68

ADD @48	@68	@72