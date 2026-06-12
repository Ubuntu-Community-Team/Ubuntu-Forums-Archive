---
title: "Tablet as a second display monitor in Linux?"
date: 2016-05-17
forum: General Help
---

### Post by lakeshore2985 on 2016-05-17
I was wondering are there any good software in Linux that extends the display to use tablet as a second monitor?

I know Windows has a pretty solid solution for this, a program called "Splashtop". But thing is I don't wanna go back to Windows anymore.

So has anyone any idea?

---

### Post by grahammechanical on 2016-05-18
The application that you refer to is actually Splashtop XDisplay. If you cannot find a Linux equivalent that does the same thing then you could try downloading the Android version and run it on Linux.

1) Install Google Chrome
2) Install a Google Chrome app called Arc Welder
3) Load Arc Welder and browse to the location of the downloaded apk file and open the apk file
4) Click Test and see what happens.

When you load the apk file this way you will get a dialog offering to remove the apk file. Accept the offer. Arc Welder stores a copy of the apk file every time we load the file and if we do not remove those file they quickly file up the partition. Once the Android app is running we can close it and then load it by clicking it icon. We do not need to run Arc Welder each time.

I have done with an Android apk on Ubuntu 16.04.

[https://apk-dl.com/splashtop-wired-xdisplay-free](https://apk-dl.com/splashtop-wired-xdisplay-free)

Regards.

---

### Post by lakeshore2985 on 2016-05-19
> **grahammechanical said:**
> The application that you refer to is actually Splashtop XDisplay. If you cannot find a Linux equivalent that does the same thing then you could try downloading the Android version and run it on Linux.

1) Install Google Chrome
2) Install a Google Chrome app called Arc Welder
3) Load Arc Welder and browse to the location of the downloaded apk file and open the apk file
4) Click Test and see what happens.

When you load the apk file this way you will get a dialog offering to remove the apk file. Accept the offer. Arc Welder stores a copy of the apk file every time we load the file and if we do not remove those file they quickly file up the partition. Once the Android app is running we can close it and then load it by clicking it icon. We do not need to run Arc Welder each time.

I have done with an Android apk on Ubuntu 16.04.

[https://apk-dl.com/splashtop-wired-xdisplay-free](https://apk-dl.com/splashtop-wired-xdisplay-free)

Regards.

Interesting approach, but I can't seem to find no "Arc Welder" extension for Chrome.

What is it anyway? And do you happen to have any working links to it?

---

### Post by bearlake on 2016-05-19
Did you try a quick search?

[http://ubuntuportal.com/2015/04/how-to-run-android-apps-with-app-runtime-for-chrome-arc-welder-in-ubuntu.html](http://ubuntuportal.com/2015/04/how-to-run-android-apps-with-app-runtime-for-chrome-arc-welder-in-ubuntu.html)

---

### Post by HermanAB on 2016-05-19
Uhmmm... how about running SSH on the tablet and connecting to the other machine SSHD?

---

