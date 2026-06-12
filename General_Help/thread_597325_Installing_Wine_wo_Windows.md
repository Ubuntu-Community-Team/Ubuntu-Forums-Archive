---
title: "Installing Wine w/o Windows"
date: 2007-10-30
forum: General Help
---

### Post by New to Linux on 2007-10-30
I am new to Linux and I have installed Ubuntu on a desktop system without windows.  _This is  a new hard drive with no windows partition_.

Ubuntu has a source for wine and it appears to install just fine.  However, it does not work, it just hangs (the wine config utility hangs, notepad example hangs, solsuite.exe hangs).

Does wine know how to install without a windows partition, or do I have to tweak it to make this work ?

Keep in mind that I have little knowledge of Linux, and even the file structure looks strange to me.

---

### Post by Green_Star on 2007-10-30
There is no need for Windows or Windows partion for wine, but any way wine has its limitation executing windows programs. I do not use wine except for IE to read couple of our reagional websites which works only in IE.

You may want to read wine documentation at following link ( you may need to start from 3. Configuring Wine, because you already installed wine)
[http://winehq.org/site/docs/wineusr-guide/index](http://winehq.org/site/docs/wineusr-guide/index)

there are some tools which made easy to install couple of MS application on wine, i am not sure whether they are working or not but you may want to try.
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by New to Linux on 2007-10-30
Thanks !  What versions of Ubuntu and Wine are you uisng ?

---

### Post by New to Linux on 2007-10-30
I reinstalled wine using wine doors, and wine tools.
Wine hangs on both intsallations, just trying to configure wine.
I removed wine doors for now to focus on wine tools.

The Wine tools 'wt' command produces the following results :

no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0".

Then a popup box says winetools can't work with this early version of wine.

Anybody ?

---

### Post by kostkon on 2007-10-30
How did you install Wine? I am asking this because above you said this:
> **New to Linux said:**
> Ubuntu has a source for wine and it appears to install just fine.
It's not so clear what you mean.

> **New to Linux said:**
> I reinstalled wine using wine doors, and wine tools.
Wine hangs on both intsallations, just trying to configure wine.
I removed wine doors for now to focus on wine tools.

The Wine tools 'wt' command produces the following results :

no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0".

Then a popup box says winetools can't work with this early version of wine.

Anybody ?

OK. You don't have a Wine directory in your Home folder. To create one, do this in the terminal
```
winecfg
```

this will also open the configuration application for Wine.

You can find Ubuntu specific information about Wine [here]("https://help.ubuntu.com/community/Wine").

---

### Post by Green_Star on 2007-10-31
Ok,

I am using latest Gusty, and installed wine using sympatic pad. long back i had problems using winetools because it doesnt support some versions of wine. any way as i told you i just install IE on wine. 

Do you know how I install applications on wine?
There is a program IE4LINUX (google it), it is very easy to install. 

1. Install wine
2. Install IE4LINUX
3. If I want to install other applications like firefox, real player, win rar etc I go to the page where I can download instalable file, after clicking instead of saving i just run it, this way i install with out hassel. Later I will see whether it is working fine or not. you can create launchers for those applications by seeing an exaple launcher in bin directory, which is located in your home directory .

the applications i installed this way are real player, firefox, vlc, winrar, some will automatically comes into your system menu, some dont, so i create my own launcher if those are not in my system menu.
hope this helps.

---

### Post by zaphod777 on 2007-10-31
not sure how you are installing wind did you download it from a website?

try this:
sudo apt-get install wine

---

### Post by New to Linux on 2007-10-31
I'll try to answer all of the questions.

Ubuntu 7.10  (latest from ubuntu site)
Wine 0.9.47  (synaptics package manager)
WineTools     wt0.9jo
WineDoors    latest version

Winetools install ends with a "run 'wt' from other than root" instruction.  
Running winecfg hangs.  Running any Wine menu option except view c drive hangs.  View c drive does nothing.

There is no /wine directory created for my user account.  It is like part of winetools did not get executed.

---

### Post by Green_Star on 2007-10-31
> **zaphod777 said:**
> not sure how you are installing wind did you download it from a website?

try this:
sudo apt-get install wine

I said I will install wine using synaptic pad and rest of the windows applications from websites using IE on w

---

### Post by New to Linux on 2007-10-31
Thanks, I'll give  IE4LINUX a try.

---

### Post by Green_Star on 2007-11-01
Let me know your feed back, this may help other users if they encounter this problems.

---

### Post by emwine on 2007-11-01
> **New to Linux said:**
> I reinstalled wine using wine doors, and wine tools.
Wine hangs on both intsallations, just trying to configure wine.
I removed wine doors for now to focus on wine tools.

I don't recommend these tools yet.  You need to find the reason straight wine is crashing.  Using wine helpers is not going to fix the underlying problem.

I don't know what your problem is, but it may be due to improper installation.  Follow the instructions here: [Ubuntu Wine]("http://www.winehq.org/site/download-deb")

Once upgraded to the latest version, if you are still having troubles, see: [IRC help]("http://www.winehq.org/site/irc")

They will not help if you are using winetools, winedoors, cedga, or even compiz.

[Edit]
Actually, prior to following this advice, I would uninstall whatever wine version you have, then any wine repositories other than listed in the link above you may have added.

Then I would remove your current wine setup (~/.wine) which shouldn't do you any harm since apparently you haven't successfully even run winecfg.
```
rm -rf ~/.wine
```

---

### Post by New to Linux on 2007-11-02
IE4Linux install hangs too. 

The setup ran fine (no errors), installed wine,  cab, dcom98, and IE6 - for Ubuntu Gutsy.

It hangs when it tries to execute IE6 - performing the initial  wine configuration, trying to create /home/root/.wine directories.

I waited about 15 minutes before pulling the plug, just in case it was actually doing something...

---

### Post by New to Linux on 2007-11-05
Well, 3 more days of trying to install wine - still no luck.  It appears that wine config only gets part way done when it hangs.  From what I've read it could be a video card or anaudio card.  I might be able to configure my own .wine directory with some help.  I need to have a valid system.reg and user.reg to do it.  Mine has no HKEY_CURRENT_USER, etc type information, just fonts and stuff.

BTW. I have used wine-doors, wine-tools, wine-fix, win4linux, and 3 different versions of wine - all with the same error - it cannot complete the configuration for the windows directories...

---

### Post by emwine on 2007-11-08
> **New to Linux said:**
> It hangs when it tries to execute IE6 - performing the initial  wine configuration, trying to create /home/root/.wine directories.

Do NOT run wine as root.  Probably your ~/.wine directory is now owned by root and is the source of all your woes.  You install the wine binaries as root, but you don't run it as root.  (sudo makes it run as root, don't ever do that)

> **New to Linux said:**
> BTW. I have used wine-doors, wine-tools, wine-fix, win4linux, and 3 different versions of wine - all with the same error - it cannot complete the configuration for the windows directories...

Other than the above quote, you haven't mentioned any errors until now.  Run from a terminal so you can see the actual errors you get.  You are much more likely to get this issue solved at the winehq IRC channel as indicated in my previous post.

---

### Post by New to Linux on 2007-11-09
Sorry, I'm really struggling with  'run as root', and root priviledges when it comes to using the file manager - especially cleaning up files and directories. 

one question:

when I run wine for the first time in a terminal window, should I try to run my windiows application or something else ?

ie wine /solsuite/ solsuite.exe  (assuming soluite is in my directory)  right?

Thanks !

---

