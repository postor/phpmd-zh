# PHPMD 规则中文说明

## 当前 Rulesets

- Clean Code Rules: 确保代码整洁. This includes rules from SOLID and object calisthenics.

- Code Size Rules: 找出代码大小的问题.

- Controversial Rules: 规范风格.

- Design Rules: 设计问题.

- Naming Rules: 命名问题 - 太长太短之类.

- Unused Code Rules: 未使用的代码.

## Clean Code Rules

### BooleanArgumentFlag: 布尔值参数

布尔标志参数是违反单一责任原则（SRP）的可靠指标。 您可以通过将布尔标志中的逻辑提取到自己的类或方法中来解决此问题。

### ElseExpression: 使用了else

带有else分支的if表达式永远不是必需的。 您可以以不需要else的方式重写条件，并且代码变得更易于阅读。 要实现这一点，请尽早使用return语句。 要实现这一点，您可能需要将代码拆分为几个较小的方法。 对于非常简单的分配，您还可以使用三元运算。

### StaticAccess: 修改静态变量

静态访问导致对其他类的不可更改的依赖性，并导致难以测试代码。 不惜一切代价避免使用静态访问，而是通过构造函数注入依赖项。 静态访问可接受的唯一情况是用于工厂方法。

## Code Size Rules

### CyclomaticComplexity: 循环复杂度

复杂性由方法中的决策点数加上方法条目的决策点数决定。 决策点是'if'，'while'，'for'和'case labels'。 通常，1-4是低复杂度，5-7表示中等复杂度，8-10表示高复杂度，11 +表示非常高的复杂度。

### NPathComplexity: 非循环复杂度

方法的NPath复杂性是通过该方法的非循环执行路径的数量。 通常认为阈值200应该采取措施来降低复杂性。

### ExcessiveMethodLength: 过长的方法

违反此规则通常表明该方法做得太多。 尝试通过创建辅助方法并删除任何复制/粘贴代码来减小方法大小。

### ExcessiveClassLength: 过长的类

长类文件表明该类可能试图做太多。 尝试将其分解，并将大小缩小到可管理的范围。

### ExcessiveParameterList: 过长的参数列表

长参数列表可以指示应创建新对象以包装众多参数。 基本上，尝试将参数组合在一起。

### ExcessivePublicCount: 过多的共有变量或方法

在类中声明的大量公共方法和属性可以指示该类可能需要被分解，因为需要更多的努力来彻底测试它。

### TooManyFields: 过多字段

可以通过对某些信息的某些嵌套对象分组来重新设计具有太多字段的类以具有更少的字段。 例如，具有city / state / zip字段的类可以改为具有一个Address字段。

### TooManyMethods: 过多方法

具有太多方法的类可能是重构的一个很好的嫌疑，以降低其复杂性并找到一种方法来获得更细粒度的对象。 默认情况下，它会忽略以“get”或“set”开头的方法。 在PHPMD 2.3中，默认值从10更改为25。

### TooManyPublicMethods: 过多共有方法

具有太多公共方法的类可能是重构的一个很好的嫌疑，以减少其复杂性并找到一种方法来获得更细粒度的对象。 默认情况下，它会忽略以“get”或“set”开头的方法。

### ExcessiveClassComplexity: 类复杂度过高

类的加权方法计数（WMC）可以很好地指示修改和维护此类所需的时间和精力。 WMC度量标准定义为类中声明的所有方法的复杂度之和。 大量方法也意味着此类对派生类具有更大的潜在影响。

## Controversial Rules

### Superglobals: 直接使用全局变量

直接访问超全局变量被认为是一种不好的做法。 例如，这些变量应该封装在框架提供的对象中。

### CamelCaseClassName: 驼峰命名类

使用CamelCase表示法命名类被认为是最佳实践。

### CamelCasePropertyName: 驼峰命名属性

使用camelCase表示法命名属性被认为是最佳实践。

### CamelCaseMethodName: 驼峰命名方法

使用camelCase表示法命名方法被认为是最佳实践。

### CamelCaseParameterName: 驼峰命名参数

使用camelCase表示法命名参数被认为是最佳实践。

### CamelCaseVariableName: 驼峰命名变量

使用camelCase表示法命名变量被认为是最佳实践。

## Design Rules

### ExitExpression: 使用exit

常规代码中的退出表达式是不可测试的，因此应该避免使用它。 建议将exit-expression移动到某种启动脚本中，其中将错误/异常代码返回给调用环境。

### EvalExpression: 使用eval

eval-expression是不可测试的，存在安全风险和不良做法。 因此应该避免。 考虑用常规代码替换eval-expression。

### GotoStatement: 使用goto

Goto使代码更难阅读，并且几乎不可能理解使用该语言构造的应用程序的控制流。 因此应该避免。 考虑用常规控制结构和单独的方法/功能替换Goto，这些更容易阅读。

### NumberOfChildren: 过多子类
 
具有过多子项的类是不平衡类层次结构的指示符。 您应该考虑重构此类层次结构。

### DepthOfInheritance: 继承层级

具有许多父项的类是不平衡和错误的类层次结构的指示符。 您应该考虑重构此类层次结构。

### CouplingBetweenObjects: 耦合

具有过多依赖性的类会对类的多个质量方面产生负面影响。 这包括稳定性，可维护性和可理解性等质量标准

### DevelopmentCodeFragment: 调试代码

var_dump（），print_r（）等函数通常仅在开发期间使用，因此生产代码中的此类调用是一个很好的指示，它们只是被遗忘。

## Naming Rules

### ShortVariable: 过短的名字

检测字段，本地或参数何时具有非常短的名称。

### LongVariable: 过长的名字

Detects when a field, formal or local variable is declared with a long name.

### ShortMethodName: 过短的方法名

Detects when very short method names are used.

### ConstructorWithNameAsEnclosingClass: 使用类名做构造方法

构造函数方法不应与封闭类具有相同的名称，请考虑使用PHP 5 __construct方法。

### ConstantNamingConventions: 常量全大写

类/接口中常量名称应始终以大写形式定义。

### BooleanGetMethodName: getX返回布尔值

查找名为'getX（）'的方法，并将'boolean'作为返回类型。 惯例是将这些方法命名为'isX（）'或'hasX（）'。

## Unused Code Rules

### UnusedPrivateField: 未使用的字段

Detects when a private field is declared and/or assigned a value, but not used.

### UnusedLocalVariable: 未使用的变量

Detects when a local variable is declared and/or assigned, but not used.

### UnusedPrivateMethod: 未使用的方法

Unused Private Method detects when a private method is declared but is unused.

### UnusedFormalParameter: 未使用的参数

Avoid passing parameters to methods or constructors and then not using those parameters.
