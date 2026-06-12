---
title: "Error Usingn  Avocent DSView 3"
date: 2007-09-19
forum: General Help
---

### Post by argabudy on 2007-09-19
Hii

I'm using ubuntu 7.04 and accessing  Avocent DSView 3 device.

I need help. Thx

it's use java application and ahve error like this

Launch File:






<?xml version="1.0" encoding="utf-8"?>

<!-- JNLP File for Java Video Viewer Application -->

<jnlp spec="1.0+" codebase="http://115.255.0.200:443/dsview/applets">

   <information>

      <title>Avocent Video Viewer Application</title>

      <vendor>Avocent Corp.</vendor>

      <icon href="viewer-icon.gif"/>

      <icon kind="splash" href="video-viewer-splash.gif"/>

   </information>



   <security>

      <all-permissions/>

   </security>



   <resources os="Windows" arch="x86">

      <j2se version="1.5" href="http://115.255.0.200:443/dsview/common/installjre.jsp" initial-heap-size="64m" max-heap-size="256m" java_vm_args="-Xincgc"/>

      <jar href="avctvideoviewer.jar"/>

      <nativelib href="avctvideoviewer-win32.jar"/>

   </resources>

      

   <resources os="Linux" arch="i386">

      <j2se version="1.5" href="http://115.255.0.200:443/dsview/common/installjre.jsp" initial-heap-size="64m" max-heap-size="256m" java_vm_args="-Xincgc"/>

      <jar href="avctvideoviewer.jar"/>

      <nativelib href="avctvideoviewer-linux.jar"/>

   </resources>

   

   <resources os="SunOS" arch="sparc">

      <j2se version="1.5" initial-heap-size="64m" max-heap-size="256m" java_vm_args="-Xincgc"/>

      <jar href="avctvideoviewer.jar"/>

      <nativelib href="avctvideoviewer-solaris.jar"/>

   </resources>



   <application-desc main-class="com.avocent.video.videoViewer">

      

        <argument>title=iSeries HMC DRC - Avocent Session Viewer</argument>

      

        <argument>cert=1</argument>

      

        <argument>ifaceviewer3=com.avocent.dsview.client.viewer.InterfaceViewer3Impl</argument>

      

        <argument>tdid=2520066</argument>

      

        <argument>sessioncookie=JSESSIONID=13ebvekhbr6y9; navState=units.units.device,_0_; JSESSIONID=628j768os6bus</argument>

      

        <argument>tdnames=iSeries HMC DRC</argument>

      

        <argument>url=https://115.255.0.200:443/dsview/protected/viewer.do</argument>

      

        <argument>viewerType=video</argument>

      

        <argument>sessionType=NORMAL</argument>

      

        <argument>application_name=dsview</argument>

      

        <argument>httpsCertificate=MIICPTCCAaagAwIBAgIERUh7oTANBgkqhkiG9w0BAQQFADBjMQswCQYDVQQGEwJJTjESMBAGA1UECBMJSW5kb25lc2lhMRAwDgYDVQQHEwdKYWthcnRhMQswCQYDVQQLEwJJVDEMMAoGA1UEChMDQlJJMRMwEQYDVQQDEwpEU1ZJRVctRFJDMB4XDTA2MTEwMTEwNDkwNVoXDTE2MTAyOTEwNDkwNVowYzELMAkGA1UEBhMCSU4xEjAQBgNVBAgTCUluZG9uZXNpYTEQMA4GA1UEBxMHSmFrYXJ0YTELMAkGA1UECxMCSVQxDDAKBgNVBAoTA0JSSTETMBEGA1UEAxMKRFNWSUVXLURSQzCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEAx4P2IkdC8/jmgaVDZvMLyc77pKY9tk6o+Sy3a+c5GZcr0S/KNGW/sGCYICTDokr+RT5WDmyOk8YrMbrSln3TrFXx1Ud5u7epSopVHS0fPJVsWUX84oFDznlPs7NqnUu9HgYFU6ST8RpEHntV5rb+CVgHsoIxrzLRknU0CvhPnB8CAwEAATANBgkqhkiG9w0BAQQFAAOBgQANXIVOikZoUwQoZXRhz4qqaXahLAG4N/KdZW7oNRvQSncfg27vZcebEt/HyzMfj3lJ8/4ZluPxxn9Z0YPrEJfln1xpBWJvnBQiYd+WLFANcPIDQi2NILQayx6SXlz+Bl++nDLAvhmGE84DP68ny0yUwyyZKnq+d13ps6rtrRfiOA==</argument>

      

        <argument>sid=2BAFB8AE0E3D2B269A0C5A908065501D55DA7102</argument>

      

        <argument>fid=/tmp/dsv2BAFB8AE0E3D2B269A0C5A908065501D55DA7102.tmp</argument>

      

   </application-desc>

</jnlp>



Exception:
NLParseException[ Could not parse launch file. Error at line 0.]
	at com.sun.javaws.jnl.XMLFormat.parse(XMLFormat.java:51)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:52)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:64)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:72)
	at com.sun.javaws.LaunchDownload.downloadJRE(LaunchDownload.java:658)
	at com.sun.javaws.Launcher.downloadJREResource(Launcher.java:1053)
	at com.sun.javaws.Launcher.prepareLaunchFile(Launcher.java:451)
	at com.sun.javaws.Launcher.prepareToLaunch(Launcher.java:165)
	at com.sun.javaws.Launcher.launch(Launcher.java:95)
	at com.sun.javaws.Main.launchApp(Main.java:299)
	at com.sun.javaws.Main.continueInSecureThread(Main.java:209)
	at com.sun.javaws.Main$1.run(Main.java:106)
	at java.lang.Thread.run(Thread.java:619)


Wrapped Exception:
java.io.EOFException: encoding.error.not.xml
	at com.sun.deploy.xml.XMLEncoding.decodeXML(XMLEncoding.java:48)
	at com.sun.javaws.jnl.XMLFormat.parse(XMLFormat.java:49)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:52)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:64)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:72)
	at com.sun.javaws.LaunchDownload.downloadJRE(LaunchDownload.java:658)
	at com.sun.javaws.Launcher.downloadJREResource(Launcher.java:1053)
	at com.sun.javaws.Launcher.prepareLaunchFile(Launcher.java:451)
	at com.sun.javaws.Launcher.prepareToLaunch(Launcher.java:165)
	at com.sun.javaws.Launcher.launch(Launcher.java:95)
	at com.sun.javaws.Main.launchApp(Main.java:299)
	at com.sun.javaws.Main.continueInSecureThread(Main.java:209)
	at com.sun.javaws.Main$1.run(Main.java:106)
	at java.lang.Thread.run(Thread.java:619)


Console:
Java Web Start 1.6.0
Using JRE version 1.6.0 Java HotSpot(TM) Client VM
User home directory = /home/briosd02
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
0-5: set trace level to <n>
----------------------------------------------------
#### Java Web Start Error:
#### Could not parse launch file. Error at line 0.

---

### Post by arpad9 on 2008-01-03
I'm having *exactly* the same problem using 7.10 and Firefox 2.0.0.11 and java 1.5.0.

Have you had any luck?  Otherwise, I have to continue to find a Windows machine to access my servers. :-(

---

### Post by Dubolomov on 2008-05-07
I fix this problem by installing SUN JRE 1.6. You may check it by enter about:plugins in FireFox's address bar.
But it works only in FireFox 2. Now i'm using Ubuntu 8.04 with FireFox 3 Beta 5. DSView KVM Session doesn't work in it.

---

