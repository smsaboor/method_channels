# method_channels

A new Flutter project.

## Getting Started

Flutter Platform Channel

After completing this tutorial you will able to run android and Windows Platform specific code/api using Platform Channel.
What is Platform Channel?
Platform channels helps to communicate your Dart code with the platform-specific code/api (native side like android/iOS/windows/linux) in bidirectional way. Which  means we can expose a platform services in our host / native side and have it invoked from the Dart side. Or vice versa.. 
eg: if you build your flutter app for android devices so how to check  battery level of that android mobile because you want to notify your App user that device battery level is low. so it is possible with the help of Platform Channels.
How Platform channel works or Architectural overview?
Messages are passed between the client (UI) and host (platform: android/iOS/web/Windows) using platform channels. Messages and responses are passed asynchronously, to ensure the user interface remains responsive as illustrated in this diagram:
On the client side, MethodChannel enables sending messages that correspond to method calls. On the platform side, MethodChannel on Android (MethodChannelAndroid) and FlutterMethodChannel on iOS (MethodChanneliOS) enable receiving method calls and sending back a result. These classes allow you to develop a platform plugin with very little 'boilerplate' code.
Flutter's builtin platform-specific API support doesn't rely on code generation, but rather on a flexible message passing style. Alternatively, you can use the Pigeon package, Pigeon is a code generator tool to make communication between Flutter and the host platform type-safe, easier, and faster.
Types Of Platform Channel
There are three ways to set up a connection between Flutter and Native code.
Message Channel- This type exposes the raw data in the form of byte buffers and can pass Codec to a High-Level data structure like an Image.
Method Channel- This type invokes named methods, with or without arguments, between dart and Native code. This gives us result back in native code.
Event Channel-Event channel exposes data stream from platform to dart. It is a Continuous Steam of Data. Applicable to subscribed Event i.e Compass, barometer sensor etc.

Some platform-specific functionality is available through existing packages(try to search that package on pub.dev eg: device_info_plus plugin to get device information) or you can implement your own with the help of this tutorial.
How to code for Platform Channel?
you need to code on two side:
Platform side like android , iOS, windows, linux
Dart side in your flutter project

Flutter uses a flexible system that allows you to call platform-specific Code/APIs in a language that works directly with those APIs:
Kotlin or Java on Android
Swift or Objective-C on iOS
C++ on Windows
Objective-C on macOS
C on Linux

Platform channel data types

Dart                          Java                          Kotlin
null                          null                          null
bool                          java.lang.Boolean             Boolean
int                           java.lang.Integer             int
int,if 32 bits not enough     java.lang.Long                Long
double                        java.lang.Double              Double
String                        java.lang.String              String
Uint8List                     byte[]                        ByteArray
Int32List                     int[]                         IntArray
Int64List                     long[]                        IntArray
Float32List                   float[]                       FloatArray
Float64List                   double[]                      DoubleArray
List                          java.util.ArrayList           List
Map                           java.util.HashMap             HashMap

// here i show java and kotlin if you want for swift or c++ then goto
// https://docs.flutter.dev/platform-integration/platform-channels?tab=
android-channel-java-tab
The following code demonstrates how to call a platform-specific API to retrieve and display the current battery level. It uses the Android BatteryManager API, the iOS device.batteryLevel API, the Windows GetSystemPowerStatus API, and the Linux UPower API with a single platform message, getBatteryLevel().
Here I start to code Platform channel only for android and windows.
Setup for android Native
Step 1: Create a new flutter project with choosing any native language Kotlin/java.
Step 2: Create the Flutter platform client as Following:

Step 3: Now Add Android platform-specific code according to your choice he I provide both implementation if you initiate your project for Kotlin then use following code else use java code:
using Kotlin :
// find MainActivity.kt File in your computer flutter project my location:
F:\method_channels\android\app\src\main\kotlin\com\example\method_channels

or using Java:
// find MainActivity.java File in your computer flutter project my location:
D:\method_channels\android\app\src\main\java\com\example\method_channels

Step 4: run your project on any android device my output is:

Windows platform-specific Code:
Now if you want to build your project for windows then follow these steps:
first enable your project for windows
build your project for windows with command:

flutter build windows
3. Start Visual Studio:
4. Select Open a project or solution.
5. Goto File->Open-> Project/Solutions.. Navigate to the directory holding your Flutter app, then into the build folder, then the windows folder, then select the methodChannel.sln(as your project name here my project name is methodChannel) file. Click Open.
   Now Add the C++ implementation of the platform channel method:
5. Expand methodChannel> Source Files in the Solution Explorer and Open the file flutter_window.cpp.
6. Add following code in flutter_window.cpp file

7. You should now be able to run the application on Windows .
   If your device doesn't have a battery, it displays 'Battery level not available'
8. Now run method_channels.exe file from your computer my loction is:
   F:\method_channels\build\windows\runner\Release