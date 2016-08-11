
# uiautomatorviewer

UI Automator 测试框架提供了一组api来构建UI测试执行用户程序和系统程序交互。
UI Automator api允许您执行操作,如打开设置菜单或应用程序启动器在测试设备。UI Automator测试框架非常适合写黑box-style自动化测试,测试代码不依赖于目标应用程序的内部实现细节。

UI Automator测试框架的关键特性包括:

1.一个查看器(viewer),检查布局层次结构;

2.一个API,来检索状态信息,在目标设备上执行操作;

3.apis支持cross-app UI测试;

4.需要安卓4.3(API级别18)或更高。


#  UI Automator Viewer /UI Automator 查看器
uiautomatorviewer工具提供了一个方便的GUI来扫描和分析当前Android设备上显示的UI组件。您可以使用这个工具来检查布局层次结构和显示在设备前景的视图UI组件的属性。这个信息可以让你使用UI Automator创建更细粒度的测试,例如通过创建一个UI选择器匹配一个特定的可见属性。
uiautomatorviewer工具位于 <android-sdk>/tools/ 路径下，如果你已经把该路径添加到path系统变量下，在控制台直接输入 uiautomatorviewer 命令就可打开该工具。

#Access to device state /访问设备状态
UI Automator测试框架提供了一个UiDevice类来访问以及在设备上执行操作。您可以调用它的方法来访问设备属性。UiDevice类也让您进行如下操作:
1.改变设备的旋转模式
2.按D-pad（方向键）按钮
3.按‘返回’，‘主页’或者‘菜单’按钮
4.打开隐藏通知栏
5.对当前窗口截图
例如,模拟一个‘主页’按钮按下,调用UiDevice.pressHome()方法。

#UI Automator APIs /UI Automator应用程序接口
UI Automator apis 允许您编写健壮的测试,而不需要知道您锁定的应用程序的实现细节。您可以使用这些api来捕获和操纵跨多个应用程序的UI组件:
UiCollection:列举一个容器的UI元素可以来计数,或获得特定子元素通过其可见文本或内容描述属性。
UiObject:代表一个UI元素是可见的在设备上。
UiScrollable:支持在可滚动的UI容器中寻找元素。
UiSelector:代表对一个或多个在设备上的目标UI元素的查询。
Configurator:允许你设置运行UI Automator测试的关键参数。


如下代码展示如何来写一个测试脚本，该脚本实现设备上的默认APP的启动

// Initialize UiDevice instance
mDevice = UiDevice.getInstance(getInstrumentation());

// Perform a short press on the HOME button
mDevice.pressHome();

// Bring up the default launcher by searching for
// a UI component that matches the content-description for the launcher button
UiObject allAppsButton = mDevice
        .findObject(new UiSelector().description("Apps"));

// Perform a click on the button to bring up the launcher
allAppsButton.clickAndWaitForNewWindow();
To learn more about using UI Automator, see the API reference and Testing UI for Multiple Apps training


