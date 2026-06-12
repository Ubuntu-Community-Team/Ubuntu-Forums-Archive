---
title: "Eclipse Kepler SDK Manager"
date: 2014-03-21
forum: General Help
---

### Post by novice_penguin on 2014-03-21
Hey all.  So just this past week for some reason I had a fatal error with my java jre that caused my Eclipse Juno to quit working.  I was unaware that the Kepler version of Eclipse was out so I thought it would be a perfect time to install it, since I was going to uninstall Juno and reinstall my JRE/JDK.  When I had the Juno version, I also had the Androit ADT plugin and the SDK installed to program Android apps.  Since installing the SDK, I am now unable to install the build tools and the different API's for the different versions of Android.  In fact, I can't even install any new software.  When I launch the Eclipse program, I get to messages right away.  "SDK Platform Tools component is missing!  Please use the SDK Manager to install it".  And "The Android SDK requires the new Build Tools component to be installed.  Open the SDK Manager to install it."  Problem is, when I try to install it from the SDK Manager, it acts as if it's about to install then I get this message:
     
"Preparing to install archives.
Download Android SDK Platform-tools, revision 19.0.1
Failed to create directory /opt/android-sdk-linux/temp
Skipping 'Android SDK Tools, Revision 22.6.1'; It depends on 'Android SDK-Platform-tools, revision 19.0.1', which was not installed
Done.  Nothing installed."

In the preferences menu under Window, my SDK location is /opt/android-sdk-linux, which is also where my eclipse is located.  I needed help installing the version of Eclipse and the Android SDK since I am still new to Ubuntu so here I will post the links at the end .  Please note that I had completely uninstalled all previous Eclipse versions I had before starting this install.  BTW I am running 12.04 32 bit Distro.

Link to install Eclipse Kepler IDE:     [http://www.krizna.com/ubuntu/install-eclipse-in-ubuntu-12-04/](http://www.krizna.com/ubuntu/install-eclipse-in-ubuntu-12-04/)
Link to install Android SDK:             [http://www.wikihow.com/Install-Android-on-Ubuntu-Linux-with-Eclipse-IDE](http://www.wikihow.com/Install-Android-on-Ubuntu-Linux-with-Eclipse-IDE)

---

### Post by jafojial on 2014-05-05
You must add write permission to /opt/android-sdk-linux/ directory for others. To do this, enter this command:
chmod -R o+w /opt/android-sdk-linux/
By default, this directory have all others permissions

---

