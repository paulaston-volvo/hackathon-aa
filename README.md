#Android Automotive

##Step 1 - Enable Automotive features in Android Studio

Install Android Studio 3.5 or higher (currently in preview).

[_https://developer.android.com/studio/preview_](https://developer.android.com/studio/preview)

Follow the instructions in the link to enable automotive features:

[_https://developer.android.com/training/cars/start#enable-automotive-flag_](https://developer.android.com/training/cars/start#enable-automotive-flag)



##Step 2 - Add emulator URL to Android Studio

Open the Android SDK Manager and click the _SDK Update Sites_ tab.

\&lt;!—IMAGE

Click + and enter the URL to the emulator xml file. Enter your CDSID and password.

_https://swf1.artifactory.cm.volvocars.biz/artifactory/artinfo-emulator/volvo/volvo\_emulator\_car.xml_

\&lt;!—IMAGE

##Step 3 - Create an Android Virtual Device

Open the AVD Manager. Click _+ Create Virtual Device_. Choose the _Automotive_ tab. If you don&#39;t see the Automotive tab, check Step 1.

Choose a hardware profile or create a New Hardware Profile. A hardware profile defines the screen size and resolution and potentially a skin (device frame). If creating a new hardware profile then be sure to choose _Automotive_ in the dropdown menu and not _Phone/Tablet_. Volvo CSD specs are size:9.0 resolution:768x1024. Click Next.

\&lt;!—IMAGE



Select a system image by choosing the _x86 Images_ tab. Choose the emulator version added in Step 2.

\&lt;!—IMAGE



Click Next and then Finish.

##Step 4 - Run the sample app

Open the sample app in Android Studio. Choose the newly created AVD in the drop down e.g. Volvo CSD API 28. Click the play button.

\&lt;!—IMAGE



The emulator will launch a CSD and a cluster window.

\&lt;!—IMAGE



Clicking the three horizontal dots, followed by the _Car data_ section reveals the following controls. You can control some vehicle properties such as speed and gear. Other sections allow you to control other sensors such as GPS.

\&lt;!—IMAGE

The properties tab in the sample app shows how to read some basic vehicle information such as speed and parking brake state. These are accessed using the _CarPropertyManager_ API. It also shows how to read the current UX Restrictions, using _CarUxRestrictionsManager_. Apps should heed this information to decide what is appropriate UI to show at a given time.

\&lt;!—IMAGE



The cluster tab shows how to display an Android Activity in the cluster window.

\&lt;!—IMAGE

##Next Steps

Consult the commented source code for more information on car APIs.

It is possible to use ADB commands to control the Vehicle HAL in many more ways than is possible through the &quot;Car data&quot; tab in the Android emulator. Better documentation needed.

_To go to Parked State_

_# speed to 0 and switch gear to park._

_adb shell dumpsys activity service com.android.car inject-vhal-event 0x11600207 0 &amp;&amp; adb shell dumpsys activity service com.android.car_

_inject-vhal-event 0x11400400 4_

_To go to Moving State:_

_# switch gear to drive and speed to 30_

_adb shell dumpsys activity service com.android.car inject-vhal-event 0x11400400 8 &amp;&amp; adb shell dumpsys activity service com.android.car_

_inject-vhal-event 0x11600207 30_

_To go to Idling State:_

_# switch gear to drive and speed to 30_

_adb shell dumpsys activity service com.android.car inject-vhal-event 0x11400400 8 &amp;&amp; adb shell dumpsys activity service com.android.car_

_inject-vhal-event 0x11600207 0_
