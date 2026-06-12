---
title: "(New to Linux) Need alot of help!"
date: 2013-12-07
forum: General Help
---

### Post by ilikecolors on 2013-12-07
My ASUS Notebook arrived today and I am a bit lost since its my first time with Linux. First off, how do I put items on the homescreen? I drag them there, but they fall back in the dashboard.

Second. I played a few games and whenever I leave the game, the screen turns small. Like, it seriously zooms in so that I can only see two programs after the little client thingy. Im a gamer and I have stuff to do, so thats a serious issue. How do I prevent that or at least revert it to its normal size?

Last, it would be really neat if someone can explain how to install Asepriter. Anything thats not on the Software Store I can't install because it gives me a headache with all the libs the ubuntu redirects tell me I need. Please help. Im running on 12. something. Thanks.

---

### Post by codemaniac on 2013-12-08
For your last question- you can search any package/software in repositories. Open a terminal and use the below command.

```
fego@production:~$ apt-cache search aseprite
aseprite - sprite and pixel art editor
```

Whenever you are trying to install a software/package in ubuntu, the package manager automatically finds out the dependent packages  that need to installed.

```

fego@production:~$ sudo apt-get install aseprite
[sudo] password for fego: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liballegro4.4 liballegro4.4-plugin-alsa libloadpng4.4
The following NEW packages will be installed:
  aseprite liballegro4.4 liballegro4.4-plugin-alsa libloadpng4.4
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,291 kB of archives.
After this operation, 3,692 kB of additional disk space will be used.
Do you want to continue [Y/n]?  
```

The libs need to be installed so that the software can behave/work properly.

---

### Post by ian-weisser on 2013-12-08
> **ilikecolors said:**
> First off, how do I put items on the homescreen? I drag them there, but they fall back in the dashboard.

If you are using Unity, you don't.
The point of Unity is that you should not need to reorganize your files, or use your Desktop as an organizer, to make them easily re-discoverable. The system should intelligently keep track of your stuff for you.

Applications (not you) are generally responsible for remembering your recently-used data, and where it's located.
The applications you use every day go on the launcher bar. (one click)
The applications you use occasionally show up on the Dash screen. (two clicks)
The applications you use almost never (and data files) are easily findable using Dash search. (three clicks and a keystroke or two)

Unity's experience is quite popular with most new Ubuntu users. But nobody said Unity is perfect for everybody. If you don't like it, fully-supported alternative Desktop Environments are available that may more closely match your imprinted workflow.

---

### Post by ilikecolors on 2013-12-08
Ah! Thanks a lot guys! I still need an answer to the gaming screen though. Thats my biggest problem.

---

### Post by heir4c on 2013-12-08
You can put files on your desktop if you install the gnome-tweak-tool (it shows up as "Tweak Tool' in Dash) and you set under 'Desktop' the first option to "On":

[IMG]http://i.imgur.com/XDbblJj.png[/IMG]

You can drag than files to it from the filemanager (Nautilus).

(There are more options with the gnome-tweak-tool. For Example: you can set Ctrl+Alt+Backspace to reload the xserver and also disable Capslock and many more.)

---

### Post by ilikecolors on 2013-12-08
By the way, the aseprite installation terminal code didn't work. It says something about not being recognizeable, and I made sure it was downloade beforehand.

---

### Post by The Cog on 2013-12-08
> **ilikecolors said:**
> By the way, the aseprite installation terminal code didn't work. It says something about not being recognizeable, and I made sure it was downloade beforehand.

If you try that command again, and copy/past the text of both the command and the response here, I'm sure someone will be able to figure out what the problem is.

---

### Post by ian-weisser on 2013-12-08
> **ilikecolors said:**
> Last, it would be really neat if someone can explain how to install Asepriter.

> **ilikecolors said:**
> By the way, the aseprite installation terminal code didn't work. It says something about not being recognizeable, and I made sure it was downloade beforehand.

Do you mean "asepriter" or "aseprite"? They might be very different.

Aseprite was added to the Ubuntu repositories in 12.10. If you are running 12.10 or later it is indeed in Software Center.
If you downloaded it from the aseprite website (*don't* do that unless you know what you are doing!) then you have the 12.10 version, which is not designed to be compatible with earlier releases of Ubuntu.

OPTION 1) You can try installing aseprite from a PPA: [http://lino.ubuntuupdates.org/pm/aseprite](http://lino.ubuntuupdates.org/pm/aseprite)
PPAs are not the same as the Ubuntu Repositories, and are not supported software. Use at your own risk. Backup your data first.

OPTION 2) You can update to a release of Ubuntu that does have aseprite in the Ubuntu Repositories (Software Center) - 12.10 or newer.

OPTION 3) You can give us an exact, detailed list of every error message, and we can see if it's possible to somehow workaround the install of the deb you have. If you downloaded the deb from the aseprite website, then it's the 12.10 version.

---

### Post by ilikecolors on 2013-12-08
I am running on 12.04 IPS. I downloaded the deb file from aseprite release 0.9.5 which can be found here:[https://launchpad.net/ubuntu/raring/amd64/aseprite/0.9.5-2ubuntu2](https://launchpad.net/ubuntu/raring/amd64/aseprite/0.9.5-2ubuntu2) after, I entered codemaniacs' first code in the terminal, and I get this: fego@production:~$: command not found

---

### Post by ian-weisser on 2013-12-08
> **ilikecolors said:**
> I am running on 12.04 IPS.
What's an IPS? It is some rare version or not-quite-Ubuntu derivative? Perhaps you mean plain old Long Term Support (LTS).


 > **ilikecolors said:**
> I downloaded the deb file from aseprite release 0.9.5 which can be found here:[https://launchpad.net/ubuntu/raring/amd64/aseprite/0.9.5-2ubuntu2](https://launchpad.net/ubuntu/raring/amd64/aseprite/0.9.5-2ubuntu2) 
The word 'raring' in the URL indicates that the deb is designed to work with Ubuntu 13.04. It might work with earlier or later versions with a few hacks...or it might not.

> **ilikecolors said:**
> after, I entered codemaniacs' first code in the terminal, and I get this: fego@production:~$: command not found
fego@production:~$ is his system's command prompt, not a command. So your system's response is appropriate.
He wanted you to try the apt-cache command that followed. That command will tell you if the desired package is available in Software Center without all the hassle of firing up SC to look for it. Since you're running 12.04, we now know the package won't be in your apt-cache, nor in your Software Center.

Which of those three options do you want to pursue?

---

### Post by ilikecolors on 2013-12-08
Eh, it seems too much of a hassle by now. I'll just search for an alternative- any ideas?

OH, and I nee to uninstall a program that I got elsewhere (Pokemon Showdown), how do I do that?

---

### Post by ian-weisser on 2013-12-08
> **ilikecolors said:**
> I nee to uninstall a program that I got elsewhere (Pokemon Showdown), how do I do that?

It depends on how you installed it. Deb binary packages, compiled source, tarballs, and scripts all install rather differently.

Where did you get it from? Do you recall how you installed it? Did you follow any instructions to install it? Please provide as much detail as you can remember. Links to where you got it from, and a link to the install instructions would help a lot.

Since it's not software from the Ubuntu Repositories, we don't support it (wherever you got it from supports it)...but we'll sure try.

---

### Post by ilikecolors on 2013-12-08
Nevermind, I got it. Thanks a lot. How do I upgrad Ubuntu though? Id like to get the newer version but im unsure if it will work or how to do it at all.

---

