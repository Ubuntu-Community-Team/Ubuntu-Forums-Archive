---
title: "How To Install Java Program?"
date: 2015-04-13
forum: General Help
---

### Post by Rick St. George on 2015-04-13
Running UbuntuStudio v14 LTS on 64bit AMD 8 core CPU with 16 GB Ram.
Have OpenJDK Java7 installed.

Broker sent me a file to install a Trading Platform right into Ubuntu (providing JAVA is installed). 
It ends in JNLP and when I choose OpenJDK JAVA7 Runtime to open and install, I get an ERROR.

< - - -   ERROR Msg. - - - >

  "The file '/home/stephen/Downloads/qst.jnlp' is not marked as executable.  
    If this was downloaded or copied from an untrusted source, it may be dangerous to run.  
    For more details, read about the executable bit."

< - - - END Msg. - - - >

So my question is, how can I mark? this file to be allowed to be opened / run / installed by JAVA?
Also tried this ....

```

sudo update-alternatives --config java
There is only one alternative in link group java (providing /usr/bin/java): /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
Nothing to configure.

```

Any help would be very appreciated. I'm trying to install this Trading Platform so I don't have to run it in VirtualBox / WinXP, which there are no available updates for JAVA within WinXP.

Thanks,
Rick

---

### Post by tjiagoM on 2015-04-13
If it is not marked as executable maybe you just have to mark it as executable? :)

```
 chmod +x [COLOR=#000000]qst.jnlp
```[/COLOR]

---

### Post by Rick St. George on 2015-04-13
Performed 
```

chmod +x '/home/stephen/Downloads/qst.jnlp'

```

No Error, then Right Click on file and selected "Open with OpenJDK Java7 Runtime" ....
but nothing happened ! ! ? ?

Did I do something wrong or should we try something else?
Note: I am trying to follow instructions from [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Probably need to install "IcedTea Java Web Start", as it is the implementation of the Java Network Launching Protocol (JNLP).

After install, under SETTINGS I see "IcedTea Web Control Panel". But when clicking it I get an Error Msg. - 

   Unable to start "/usr/bin/itweb-settings"
   Failed to execute child process "user/bin/itweb-settings"
   (no such file or directory)


Thanks
Rick

---

### Post by Holger_Gehrke on 2015-04-13
A file with the extension '.jnlp' is not a Java program but a xml file with instruction for Java web start. Use the command 'javaws /home/stephen/Downloads/qst.jnlp' to start the program; the program is not installed on your machine, it will be loaded from the net and executed in a similar way to an applet.

---

### Post by Rick St. George on 2015-04-13
Created a shortcut on Desktop by right clicking and selecting "Create Launcher". Input the command (mentioned above), Double Click the shortcut ...
and received this Error - 

   Failed to run "Ira Chart Launcher.destop"
   Failed to execute child process "javaws" (No such file or directory)

I am mising something ! ! ? ? 

Help!

---

### Post by CantankRus on 2015-04-13
Test the "javaws [COLOR="#696969"]/path/to/jnlp[/COLOR]" command in terminal first.

---

### Post by Rick St. George on 2015-04-13
Test what is in "Properties" regarding the Launch Icon on the desktop. Here is the printout;

```

stephen@stephen-evo-5723:~$ javaws "/home/stephen/.cache/icedtea-web/cache/0/http/lgp.linngroup.com/webstart/LGP-IraCharts/qst.jnlp"
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Unknown Main-Class. Could not determine the main class for this application.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:684)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:277)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.createInstance(JNLPClassLoader.java:351)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:418)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:462)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeExtensions(JNLPClassLoader.java:495)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:275)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.createInstance(JNLPClassLoader.java:351)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:418)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:394)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:781)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:529)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:911)

This application does not specify a Codebase in its manifest. Please verify with the applet's vendor. Continuing. See: http://docs.oracle.com/javase/7/docs/technotes/guides/jweb/security/no_redeploy.html for details.
This application does not specify a Codebase in its manifest. Please verify with the applet's vendor. Continuing. See: http://docs.oracle.com/javase/7/docs/technotes/guides/jweb/security/no_redeploy.html for details.
Application title was not found in manifest. Check with application vendor
Application title was not found in manifest. Check with application vendor
stephen@stephen-evo-5723:~$ 


```

Checking that page for info ....

---

### Post by CantankRus on 2015-04-13
Not a Java expert but in the past you had to install Oracle's java to run some web applications.
[**_[COLOR="#B22222"]INSTALL ORACLE JAVA 8 IN UBUNTU[/COLOR]_**]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")

Check default java...
```
java -version
```
eg```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] java -version**
java version "1.8.0_40"
Java(TM) SE Runtime Environment (build 1.8.0_40-b25)
Java HotSpot(TM) 64-Bit Server VM (build 25.40-b25, mixed mode)
```

After installing Oracle's java try running (assuming that's the **[COLOR="#FF0000"]right path to the jnlp[/COLOR]** file sent you) ...
```
javaws '**[COLOR="#FF0000"]/home/stephen/Downloads/qst.jnlp[/COLOR]**'
```

Also Oracle has beefed up security so you may have to whitelist the website being used if it is blocked.
[ATTACH=CONFIG]261270[/ATTACH]

Just run by itself ```
javaws
```
Close the cache viewer window and in the  security tab add your site.

---

### Post by Rick St. George on 2015-04-14
java -version
java version "1.7.0_75"
OpenJDK Runtime Environment (IcedTea 2.5.4) (7u75-2.5.4-1~trusty1)
OpenJDK 64-Bit Server VM (build 24.75-b04, mixed mode)

Please note -  Oracle Java 8 installer is considered in alpha and is offered without any guarantees! Use at your own risk.
Running the script places a shortcut icon for LGP Charts on the desktop. Double Clicking on that icon starts a Java Window, but then NOTHING.
Here is a printout of the Log;

< --- Log Printout --- >

[stephen][ITW-APPLET][WARNING_ALL][Mon Apr 13 17:18:29 EDT
2015][net.sourceforge.jnlp.util.logging.FileLog.<init>(FileLog.java:93)]
NETX Thread# 5b390546, name Output controller consumer daemon
System is already following XDG .cache and .config specifications
config: */home/stephen/*.config/icedtea-web file exists: true
cache: */home/stephen/*.cache/icedtea-web file exists:true
Loading User level properties from:
*/home/stephen/*.config/icedtea-web/deployment.properties
WARNING: key deployment.system.cachedir has no value, setting to default
value
WARNING: key deployment.system.cachedir has no value, skipping
Starting security dialog thread
Using firefox's profiles file: */home/stephen/*.mozilla/firefox/profiles.ini
Found preferences file:
*/home/stephen/*.mozilla/firefox/jwwnl2w3.default/prefs.js
Read 298 entries from Firefox's preferences
JNLP file location:
*/home/stephen/*.cach/icedtea-web/cache/0/http/lgp.linngroup.com/webstart/LGP-IraCharts/qst.jnlp
call privileged method: getCodeBase
        result: null
java.net.MalformedURLException: no protocol:
*/home/stephen/*.cach/icedtea-web/cache/0/http/lgp.linngroup.com/webstart/LGP-IraCharts/qst.jnlp
	at java.net.URL.<init>(URL.java:585)
	at java.net.URL.<init>(URL.java:482)
	at net.sourceforge.jnlp.runtime.Boot.getFileLocation(Boot.java:284)
	at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:246)
	at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:58)
	at java.security.AccessController.doPrivileged(Native Method)
	at net.sourceforge.jnlp.runtime.Boot.main(Boot.java:213)

netx: Invalid jnlp file
*/home/stephen/*.cach/icedtea-web/cache/0/http/lgp.linngroup.com/webstart/LGP-IraCharts/qst.jnlp

< --- END Printout --- >

Does this Help?

When testing the link in "Properties" regarding the Desktop Link,
this is what I get;

< --- Terminal Printout --- >
stephen@stephen-evo-5723:~$ javaws
"*/home/stephen/*.cache/icedtea-web/cache/0/http/lgp.linngroup.com/webstart/LGP-IraCharts/qst.jnlp"

net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error:
Unknown Main-Class. Could not determine the main class for this application.
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:684)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:277)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.createInstance(JNLPClassLoader.java:351)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:418)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:462)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeExtensions(JNLPClassLoader.java:495)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:275)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.createInstance(JNLPClassLoader.java:351)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:418)
    at
net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:394)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:781)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:529)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:911)

This application does not specify a Codebase in its manifest. Please
verify with the applet's vendor. Continuing. See:
[http://docs.oracle.com/javase/7/docs/technotes/guides/jweb/security/no_redeploy.html](http://docs.oracle.com/javase/7/docs/technotes/guides/jweb/security/no_redeploy.html)
for details.
This application does not specify a Codebase in its manifest. Please
verify with the applet's vendor. Continuing. See:
[http://docs.oracle.com/javase/7/docs/technotes/guides/jweb/security/no_redeploy.html](http://docs.oracle.com/javase/7/docs/technotes/guides/jweb/security/no_redeploy.html)
for details.
Application title was not found in manifest. Check with application vendor
< --- END Printout --- >

Any suggestions ? ? ?
Rick

---

### Post by CantankRus on 2015-04-14
Check your default java and javaws.
eg
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] sudo update-alternatives --config java**
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
[COLOR="#FF0000"]* 0            /usr/lib/jvm/java-8-oracle/jre/bin/java          1078      auto mode[/COLOR]
  1            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      manual mode
  2            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java    1070      manual mode
  3            /usr/lib/jvm/java-8-oracle/jre/bin/java          1078      manual mode

Press enter to keep the current choice[*], or type selection number: 

**[COLOR="#008000"]glen@Trusty:~$[/COLOR] sudo update-alternatives --config javaws**
There are 3 choices for the alternative javaws (providing /usr/bin/javaws).

  Selection    Path                                              Priority   Status
------------------------------------------------------------
**[COLOR="#FF0000"]* 0            /usr/lib/jvm/java-8-oracle/jre/bin/javaws          1078      auto mode[/COLOR]**
  1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/javaws   1061      manual mode
  2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/javaws   1071      manual mode
  3            /usr/lib/jvm/java-8-oracle/jre/bin/javaws          1078      manual mode

Press enter to keep the current choice[*], or type selection number:
```
When you say "Running the script places a shortcut icon for LGP Charts on the desktop." ...is this a script from your stockbroker?
May want to post it.

---

### Post by Rick St. George on 2015-04-14
It is the install "jnlp" file. Which Java uses to install. It then places an icon on the desktop to allow one to click on the icon and Run or Start the program which opens a Window streaming quotes etc., ie. the Trading Platform. And yes it came from my Futures Broker.

---

### Post by CantankRus on 2015-04-14
Ok.
As a test I googled for "LGP-IraCharts" and found [http://www.iraepstein.com](http://www.iraepstein.com) which offers a qnlp file to run **LGP-IraCharts** java software.
I downloaded the jnlp file to my home folder.
```
<jnlp codebase="http://lgp.linngroup.com/webstart/LGP-IraCharts/" href="qst.jnlp" spec="1.0+"> 

<information>
	<title>LGP-IraCharts</title>
	<vendor>Linn Group Platform</vendor>
	<icon href="QST.gif" />
	<shortcut online="true">
		<desktop />
		<menu submenu="LGP-IraCharts" />
	</shortcut>
	<homepage href="http://www.iraepstein.com" />
	<offline-allowed />
</information>

<security>
	<all-permissions />
</security>

<resources>
	<j2se href="http://java.sun.com/products/autodl/j2se" version="1.5+" />
	<jar href="loader.jar" />
	<extension href="installer.jnlp" name="LGP-IraCharts Installer" />
</resources>

<application-desc main-class="Loader.JarRunner">
	<argument>320</argument>
	<argument>-prod</argument>
	<argument>-Xms16m</argument>
	<argument>-Xss512k</argument>
	<argument>-XX:+UseParallelGC</argument>
	<argument>-Xcheck:jni</argument>
	<argument>-Xshare:off</argument>
</application-desc>

</jnlp>
```

As shown in [**_[COLOR="#B22222"]post #10[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2273465&p=13264758#post13264758")
I am using **java-8-oracle** as default.
I ran ....
```
/usr/bin/javaws /home/glen/qst.jnlp
```
which then proceeded to download the application from "lgp.linngroup.com" ...
[ATTACH=CONFIG]261298[/ATTACH]

and then I was presented with a password dialogue to use the application...
[ATTACH=CONFIG]261299[/ATTACH]

It appears to be the same java application you are trying to use.

---

### Post by Rick St. George on 2015-04-14
Yes, from my Broker - it was the Install program which placed the icon on the Desktop, and when clicking on the icon a window briefly pops up, but nothing happens. It is supposed to run the Trading Platform.

Just received an Email from them that I must install Oracle Java 7 or 8, as it only works with the Oracle version, not OpenJava.

Is it worth it ???  I thought Java opens a Security Breach ! ? !

---

### Post by CantankRus on 2015-04-14
> **Rick St. George said:**
> Yes, from my Broker - it was the Install program which placed the icon on the Desktop, and when clicking on the icon a window briefly pops up, but nothing happens. It is supposed to run the Trading Platform.

Just received an Email from them that I must install Oracle Java 7 or 8, as it only works with the Oracle version, not OpenJava.

Is it worth it ???  I thought Java opens a Security Breach ! ? !

From post #8
> **CantankRus said:**
> Not a Java expert but in the past you had to install Oracle's java to run some web applications.
[**_[COLOR="#B22222"]INSTALL ORACLE JAVA 8 IN UBUNTU[/COLOR]_**]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")

As I said not a java expert but I believe java security is better now where you need to allow things to run and whitelist sites.

---

### Post by Rick St. George on 2015-04-14
Thanks Guys ... One more Question?

Should I remove the previously installed;
  OpenJDK-7-jre (java runtime environment)
  OpenJDK-7-jdk (jave development kit)
  IcedTEA-7-plugin


Before installing Oracle JAVA JRE?

Thanks!

---

### Post by CantankRus on 2015-04-14
No not necessary ... after installing just set the default java and javaws as in post #10.

---

### Post by Rick St. George on 2015-04-14
That did it. The tech guy from my Broker finally emailed me - Install Oracle Java 7 or 8. Since 7 is now outdated, I installed v8 via these commands.

```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer

```

Then I ran the "qst.jnlp" file and it installed, ran the Login Screen for the Trading Platform. Now I am in business. Case Closed.

Thanks a Million!  
                  Ubuntu Rocks!      :guitar:

---

### Post by CantankRus on 2015-04-14
> **Rick St. George said:**
> 

Thanks a Million!  
                  Ubuntu Rocks!      :guitar:
When you become Gordon Gekko you can send me a million. :p

---

