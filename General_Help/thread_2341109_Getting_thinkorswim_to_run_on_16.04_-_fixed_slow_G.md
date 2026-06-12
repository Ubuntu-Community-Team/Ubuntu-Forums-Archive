---
title: "Getting thinkorswim to run on 16.04 - fixed slow GUI"
date: 2016-10-24
forum: General Help
---

### Post by GouZi on 2016-10-24
A follow up of [getting thinkorswim to run on 12.04]("https://ubuntuforums.org/showthread.php?t=2044006").

Very similar to what was done on 14.04:
You'd still need oracle java installer:

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer

mkdir $HOME/TOS
chmod 755 thinkorswim_installer.sh
./thinkorswim_installer.sh
./TOS/thinkorswim/thinkorswim

```


It works with gnome-session-fallback, Ubuntu Classic (Metacity) session, works also with Compiz (should also work in Unity).

If you have a lot of windows, tweaking the vm options can give you more room performance wise:
edit TOS/thinkorswim/thinkorswim.vmoptions

Replace the lines containing:
```
-Xmx512m
-XX:MaxPermSize=128m

```

by:
```
-Xmx2048m
-XX:MaxPermSize=256m

```

Now since java8, you may be plagued by a very slow GUI.

The issue seems to be a fallout of a change in X11GraphicsEnvironment.java per:
[https://bugs.openjdk.java.net/browse/JDK-8068529](https://bugs.openjdk.java.net/browse/JDK-8068529)

To get a fast GUI back you may want to add the following to TOS/thinkorswim/thinkorswim.vmoptions:
```
-Dsun.java2d.xrender=false

```

---

