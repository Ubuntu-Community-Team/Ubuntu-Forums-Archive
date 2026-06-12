---
title: "Please help with few issues that make my system less attractive all the time"
date: 2006-09-17
forum: General Help
---

### Post by javierfh on 2006-09-17
Hello,

i have been using ubuntu since may, I started with a beta from Dapper and back them i was really excited, but that excitation has been going down lately with few issues i have been experiencing.
So I will number the issues i have been having and hopefully people can help with any of these(or all :D)

1.-Unstability of the whole system
This is probably the more difficult to reproduce and difficult to solve, but i hope that when installing the new release next month things get little bit more stable. What it happens currently, is that randomly the system crashes. The crash means that i cant basically interact with the windows, meaning i cant close windows, move them or type text. Only way to solve that, it is to CTRL+ALT+Backspace and then log back again. This it is quite annoying thing, because makes your system not very reliable and you feel scared starting delicate things, the system can crash in middle of the process as for example paying bills or burning cds or big batch work with photo editing software.
Any ideas or help will be more than appreciated.

2.-Problems with Compiz/XGL
I had installed compiz following the "one thread to rule them all" and it was wonderfull, everything worked just fine. I installed then the Quinn repositories and all was even better...until recently when they changed something. Now the situation it is so, that when my system boots, compiz it is not started and the upper part of the windows goes under the upper system bar. So first thing i need to do, it is to open console and type compiz-start. Other alternative it is to go to the compiz cube icon, in the top bar and switch to metacity (which is the only thing working now from the icon).
So anyone know any tricks how to get all to the previous state? In other words, to change the actions asociated to the cube icon so it launch the new ones and to launch compiz at startup.

3.-Problems with Firefox.
Firefox just crashes randomly and disappears. No idea why, but sudently it happens and no error report nor anything.

4.-Problems with Webcam and AMSN.
Until now had been working just fine, but lately i cant send the webcam, i can receive webcam from other side, but not send my image.

5.-Cant install JAlbum. 
I try to install JAlbum but then i get the following error.
```

javi@javi-desktop:~$ sh ./JAlbuminstall.bin Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError: ZeroGe
   at java.lang.Class.initializeClass(libgcj.so.7)
   at ZeroGd.<clinit>(DashoA8113)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.b(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
   at com.zerog.ia.installer.Main.main(DashoA8113)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at com.zerog.lax.LAX.launch(DashoA8113)
   at com.zerog.lax.LAX.main(DashoA8113)
Caused by: java.lang.ClassNotFoundException: com.apple.mrj.MRJOSType not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/tmp/install.dir.19790/InstallerData/,file:/tmp/install.dir.19790/InstallerData/installer.zip,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...9 more
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
javi@javi-desktop:~$

```

I have tried also to reinstall java, even tried to install it using easy ubuntu, but nothing works, not even easyubuntu. Any idea please, thats something i really would like to fix, Jalbum it is a wonderfull program.


Thanks in advance for all the help you can give me.

Javi

---

### Post by Lord Illidan on 2006-09-17
I wager that the main part of your probs are due to compiz + xgl, two alpha programs which are still in heavy development. Try uninstalling those, and see how you get on then.

---

### Post by javierfh on 2006-09-17
Hello,

thanks for the answer, but i think that shouldnt be reason. I suppose there are people with the system working and well i bet that the idea is that should work. In fact had been working properly until last month.

So which one are the ones that you think are alpha applications?

I really wish things get better, because ubuntu really promises to be a wonderfull operative system, but at the end, if the system it is not stable and you cant do things..soon or later people will get tired and go..as you can read from posts lately...more and more people are leaving.
But as i said, i still believe that this will be solved :D little by little.

So lets see if anyone there still knows how can i fix any of these things.
Any help?

Javi

---

### Post by orb9220 on 2006-09-17
Here Here if you want stability over eye candy than get rid of xgl/compwiz for awhile until it matures some.

Two your jalbum and java problems appear to be related. Go to Jalbum developers site and see what the specific requirements are and for insight what the problem may be.

Three are you using ati graphics? They are problematic.
Four installing .bin and or converting rpm to debs can also be problematic.
With deb's usally fine to install with gDebi package installer.

Next step is to verify jave installed and version with entering about:plugins in the address bar of firefox.

---

### Post by javierfh on 2006-09-17
Hello,

yes i know that maybe its better to disable xgl/compiz, but on the other hand ubuntu should be able to compete with Vista, so i bet that the idea is that XGL/compiz are stable enought to compete...maybe something just got screwed somewhere..its about to find the problem.

About JAlbum yes i know might be somethign to do with java and some people has reported similar problem...but others replied that by installing java again...it work..but in my case seems not to work...and it is very annoying.

And about my video card i have nvidia geforce 7600GT so it works just fine.
And about the plugins i have this is the result from the about:plugins

[HTML]
Totem Mozilla Plugin

    File name: libtotem_mozilla.so
    The Totem 1.4.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
video/divx 	AVI video 	divx 	Yes
audio/wav 	WAV audio 	wav 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.581 built with gcc 3.2.0 on Feb 1 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r63

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
[/HTML]

---

### Post by PriceChild on 2006-09-17
I've just realised that the latest version of compiz stopped me typing into boxes on ubuntuforums.org for example.

XGl/Compiz ARE alpha, and can very easily mess up other seemingly unrelated software.

It isn't stable, and if you're not up for a bit of fun fixing things then get rid of it.

---

### Post by javierfh on 2006-09-17
Anyone can give some hints about some of my problems??
Anyone can help?

Javi

---

### Post by astoltz on 2006-09-17
For problem number two.  They have changed the way that compiz should be started.  Do not use the scripts that are described in the various HOW TO's.  Instead use the command "compiz-start".  Put that command in your sessions startup and take out any other scripts you may have there already.

As for your stability issues, I'd agree with the other posters and say don't use compiz.  Even though compiz may have been stable for you in the past, it may not be stable now.

---

### Post by AndyCooll on 2006-09-17
> **javierfh said:**
> Anyone can give some hints about some of my problems??
Anyone can help?

Javi

Yes ...resolve your instability issues by uninstalling xgl/compiz. Whether you wish to hear this as an answer or not (and agree or not), as others have said this is the most likely reason for the majority of your problams.

:cool:

---

### Post by Belyel on 2006-09-17
I have had the same problem running xgl+compiz.  If compiz crashes, you lose your title bars, borders, effects, and some/all keyboard shortcuts.  If you installed xgl + compiz following that "one thread" steps, you should be able to change your session on the login screen to gnome.  I would be willing to bet at least a dollar that it would fix your problems.  I just had to tweak and putz to get mine stable using flglx (ati), and even then it still crashes once it awhile.  If you keep updating compiz, recently they changed how you had to launch compiz, so search these forums if it's not starting at all for directions to fix it.

---

### Post by Leeghoofd on 2006-09-18
1. Uninstall compiz for the time being. They will work on their unstable issues. You might be able to reinstall it without the programm causing your system to lock.

2. If your system continue's to crash, try to install an earlier version of ubuntu. There are a fair number of users that have simular issues. OR.. wait for the version of ubuntu to come online.

Not great solutions, I admit.

---

### Post by ouilsen on 2006-09-18
This is in case you have an ati card.

I had some stability issues with compiz lately. Moreover I had this bug on my system: 

[http://ati.cchtml.com/show_bug.cgi?id=239](http://ati.cchtml.com/show_bug.cgi?id=239) 

Now look at comment #61. As mentioned, I set my agp to 2x mode. The result was no more crash at relogging AND no more random compiz/Xgl system hang ups. Of course this is not a permanent solution.

---

### Post by javierfh on 2006-09-18
Thanks for all your replies.
I have disabled xgl/compiz so lets see if gets more stable.
About my video card, i have Nvidia and no problems with that.

Anyone knows anything about the JAlbum problem?
i cant make it work and well would be nice to get that application working.

Any help there??


Javi

---

### Post by Dinerty on 2006-09-18
> **javierfh said:**
> Hello,

2.-Problems with Compiz/XGL
I had installed compiz following the "one thread to rule them all" and it was wonderfull, everything worked just fine. I installed then the Quinn repositories and all was even better...until recently when they changed something. Now the situation it is so, that when my system boots, compiz it is not started and the upper part of the windows goes under the upper system bar. So first thing i need to do, it is to open console and type compiz-start. Other alternative it is to go to the compiz cube icon, in the top bar and switch to metacity (which is the only thing working now from the icon).
So anyone know any tricks how to get all to the previous state? In other words, to change the actions asociated to the cube icon so it launch the new ones and to launch compiz at startup.

Have you added "compiz-start" to your start up list?, I did hear "compiz-manager" is the new one now, but it did not work for me, also if "compiz-start" refuses to work then try adding /usr/bin/compiz-start

For some reason my xgl/compiz would not load if it just said "compiz-start" had to add /usr/bin/compiz-start

> 3.-Problems with Firefox.
Firefox just crashes randomly and disappears. No idea why, but sudently it happens and no error report nor anything.

Mine does this also, on Firefox 2 beta now, and for some reason it seems more stable then the firefox 1

---

### Post by javierfh on 2006-09-18
> **Dinerty said:**
> Have you added "compiz-start" to your start up list?, I did hear "compiz-manager" is the new one now, but it did not work for me, also if "compiz-start" refuses to work then try adding /usr/bin/compiz-start

For some reason my xgl/compiz would not load if it just said "compiz-start" had to add /usr/bin/compiz-start


Hello, it was added there... and still didnt work, i had at the end ".py" so i removed it now...hoping that maybe it works now, but to be honest not very confident.

About firefox, i hope it gets stable at some point.

Now i guess that the thing that i would like to fix the most would be to be able to install jalbum and also the webcam issue...eventhough have to try now with XGL/compiz disabled..

Javi

---

### Post by droazen on 2006-09-18
> **javierfh said:**
> 
Now i guess that the thing that i would like to fix the most would be to be able to install jalbum and also the webcam issue...eventhough have to try now with XGL/compiz disabled..


My suggestion would be to install the Sun Java SDK from the Penguin Liberation Front repository. Then update the symlinks in /etc/alternatives to point to the Sun binaries.

Eg., 

```

sudo update-alternatives --set java /usr/lib/j2sdk1.5-sun/bin/java

```

This has solved many Java-related problems for me. GNU's Java is still kinda flaky...

---

### Post by droazen on 2006-09-18
> **droazen said:**
> My suggestion would be to install the Sun Java SDK from the Penguin Liberation Front repository. Then update the symlinks in /etc/alternatives to point to the Sun binaries.


I should add, that you might ALREADY have the Sun SDK installed, but the "java" symlink in /etc/alternatives might still be pointing at GNU's java (seems to be the case from the installer output you pasted), in which case you need to run update-alternatives to point it at the Sun binary.

---

### Post by javierfh on 2006-09-19
> **droazen said:**
> I should add, that you might ALREADY have the Sun SDK installed, but the "java" symlink in /etc/alternatives might still be pointing at GNU's java (seems to be the case from the installer output you pasted), in which case you need to run update-alternatives to point it at the Sun binary.

Hi,
im currently at work and because the time difference, i saw your suggestion 6 hours late :D , but seems very interesting, i will test it as soon as i get home and post the results here.

Thanks a lot for your interest and i hope that this makes the trick.

Javi

---

### Post by javierfh on 2006-09-19
> **droazen said:**
> My suggestion would be to install the Sun Java SDK from the Penguin Liberation Front repository. Then update the symlinks in /etc/alternatives to point to the Sun binaries.

Eg., 

```

sudo update-alternatives --set java /usr/lib/j2sdk1.5-sun/bin/java

```

This has solved many Java-related problems for me. GNU's Java is still kinda flaky...

Hello...

to be honest im totally lost and dont know how to fix that one.

This is the content of my /usr/lib and cant find from there any way to write the command that you specified in the code you wrote 


```

javi@javi-desktop:/usr/lib$ ls j*
java:
swt3.1-gtk.jar  swt-gtk.jar  swt.jar

jni:
libswt-atk-gtk-3139.so    libswt-gnome-gtk-3139.so    libswt-pi-gtk-3139.so
libswt-awt-gtk-3139.so    libswt-gtk-3139.so
libswt-cairo-gtk-3139.so  libswt-mozilla-gtk-3139.so

jvm:
java-1.4.2-gcj-4.1-1.4.2.0  java-1.5.0-sun  java-1.5.0-sun-1.5.0.08  java-gcj
javi@javi-desktop:/usr/lib$


```

Any suggestion? 
Please consider me totally dumb :D 


Javi

---

### Post by droazen on 2006-09-19
> **javierfh said:**
> Hello...

to be honest im totally lost and dont know how to fix that one.

This is the content of my /usr/lib and cant find from there any way to write the command that you specified in the code you wrote 


The actual path to the Sun java runtime on your system may be different than in the command I gave you. The first step is to verify that the java symlink in /etc/alternatives is actually pointing at GNU's java and not Sun's:

```

cd /etc/alternatives
ls -l java

```

If it's pointing at GNU's java, then you need to find out where Sun's java is hiding on your system. On mine it is in /usr/lib/j2sdk1.5-sun/bin/java, but on yours it looks like it might be in /usr/lib/jvm/java-1.5.0-sun/bin/java or   /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/bin/java. 

Once you've found it, run that update-alternatives command I gave you, substituting in the correct path to Sun's java on your system. Eg.,

```

sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/bin/java

```

Assuming you find it in /usr/lib/jvm/java-1.5.0-sun/bin/java. Then re-run the installer and see if your error goes away

---

### Post by javierfh on 2006-09-19
> **droazen said:**
> The actual path to the Sun java runtime on your system may be different than in the command I gave you. The first step is to verify that the java symlink in /etc/alternatives is actually pointing at GNU's java and not Sun's:

```

cd /etc/alternatives
ls -l java

```

If it's pointing at GNU's java, then you need to find out where Sun's java is hiding on your system. On mine it is in /usr/lib/j2sdk1.5-sun/bin/java, but on yours it looks like it might be in /usr/lib/jvm/java-1.5.0-sun/bin/java or   /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/bin/java. 

Once you've found it, run that update-alternatives command I gave you, substituting in the correct path to Sun's java on your system. Eg.,

```

sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/bin/java

```

Assuming you find it in /usr/lib/jvm/java-1.5.0-sun/bin/java. Then re-run the installer and see if your error goes away




Hello, 

thanks for your quick answer.

This is the result of the first question you asked

```

javi@javi-desktop:~$ cd /etc/alternatives
javi@javi-desktop:/etc/alternatives$ ls -l java
lrwxrwxrwx 1 root root 34 2006-09-17 10:40 java -> /usr/lib/jvm/java-gcj/jre/bin/java
javi@javi-desktop:/etc/alternatives$


```

So how then i know where the Sun Java is hiding ? :D
Is there any way to check , verify or test the ones that you mentioned? Or what kind of files do i expect to see  there?

Javi

---

### Post by droazen on 2006-09-19
> **javierfh said:**
> 
This is the result of the first question you asked

```

javi@javi-desktop:~$ cd /etc/alternatives
javi@javi-desktop:/etc/alternatives$ ls -l java
lrwxrwxrwx 1 root root 34 2006-09-17 10:40 java -> /usr/lib/jvm/java-gcj/jre/bin/java
javi@javi-desktop:/etc/alternatives$

```


Ok, this verifies that your java symlink is pointing at GNU's java.

> 
So how then i know where the Sun Java is hiding ? :D
Is there any way to check , verify or test the ones that you mentioned? Or what kind of files do i expect to see  there?


I think the Sun java runtime is probably going to be hiding at /usr/lib/jvm/java-1.5.0-sun/jre/bin/java on your system. You can check by doing:

```

cd /usr/lib/jvm/java-1.5.0-sun/jre/bin/
ls -l java

```

If there's a file called java there that's around 60-70k, then you can safely do:

```

sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```

And see if your problem is fixed.

---

### Post by matrooswolf on 2006-09-19
For Compiz, there isn't a realy up to date guide I think, things change so fast.

The best place to look for recent information is [www.compiz.net](www.compiz.net)

And look and behold, some more rather big changes are under way, compiz is getting forked: compiz-quinnstorm becomes beryl ...

---

### Post by javierfh on 2006-09-19
Hi Droazen,

i have to say...you just jump right away to the hit parade of my heroes :D

It worked!!!!

im just amazed...it really worked.

Thanks, thanks, thanks :D  as you can see, someone here it is happy having that application running :D

Javi

---

### Post by javierfh on 2006-09-19
> **matrooswolf said:**
> For Compiz, there isn't a realy up to date guide I think, things change so fast.

The best place to look for recent information is [www.compiz.net](www.compiz.net)

And look and behold, some more rather big changes are under way, compiz is getting forked: compiz-quinnstorm becomes beryl ...


Hi,

very interesting...
do you have any pointers or links to that information?
I mean that thing about compiz forked ? i would like to read about it, to be aware.

Javi

---

### Post by matrooswolf on 2006-09-19
Hi,
yes, just go to [www.compiz.net](www.compiz.net), there is an announcement on top, "important news", and if you go to general notices, there are some threads with a lot of kudos, and possible artwork, 

(I read: possible release by the end of the week? ...)

They plan a stable release and an unstable one (with all the latest stuff), and they plan write a new howto, all good news ...

---

