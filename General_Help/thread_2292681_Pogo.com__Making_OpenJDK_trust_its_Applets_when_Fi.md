---
title: "Pogo.com : Making OpenJDK trust its Applets when Firefox runs them"
date: 2015-08-30
forum: General Help
---

### Post by Joe88 on 2015-08-30
Hi,

The proprietary Java in Windows/Ubuntu comes with a control panel GUI and [Pogo.com]("http://pogo.com")'s address can simply be added to an exception list.

I know the OpenJDK used to have a exception.list file in: ~/.java/deployment/security but this file and its parent directories don't exist in my Ubuntu 15.04 64 bit home directory. I've tried creating them.

Having not been able to find this file I've tried using the OpenJDK policy editor in the IcedTea Firefox plugin's control panel but I've not been able to configure OpenJDK to trust Pogo.com's "High Stakes Pool" applet which is the game which makes me use this Java games website because its the only web browser pool game I've found which supports 3 player cuthroat pool. Here are my current policy editor settings:
[[IMG]https://www.mediafire.com/convkey/f1f7/h1ryc3qpcf3ssne6g.jpg[/IMG]](https://www.mediafire.com/view/?h1ryc3qpcf3ssne)

Can someone please help me by either telling me where I can find another non Java cuthroat pool browser game or how I can configure OpenJDK policies to make it trust pogo.com applets?

---

### Post by Joe88 on 2015-08-31
I'm using the proprietary Java JRE now, its permission prompt simply asks if [http://game3.pogo.com](http://game3.pogo.com) should be allowed to execute applets and can be told to remember your answer & not ask again. I uninstalled the openJDK JRE and the IceTea firefox plugin using the synaptic package manager and then I installed Java 8 from a PPA using [these instructions]("http://askubuntu.com/questions/56104/how-can-i-install-sun-oracles-proprietary-java-jdk-6-7-8-or-jre") (see "The easy way").

---

