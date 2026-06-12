---
title: "Running a DOS program"
date: 2007-03-27
forum: General Help
---

### Post by GolfGeek on 2007-03-27
I have a friend who wants to move more and more into the Ubuntu system but has a small problem. She needs to run a program that was written and compiled in the DOS environment. It is a clipper application. In windows, I have set up a command window and she is able to run with no problem. Is there a way to accomplish this under Ubuntu. My first thought was to use something like wine but I haven't had the opportunity to try that out so I figured someone here in the forums has run across a similar problem /(solution?)

---

### Post by milton1 on 2007-03-27
try wine, and in setup set it to emulate an earlier version of windows (95, or even 3.1 if you can).

---

### Post by PictureThis on 2007-03-27
If wine doesn't work out I would definitely go for [DOSBox](http://dosbox.sourceforge.net/news.php?show_news=1), originally created to run old DOS-games but this tool has superseded itself. :)  Highly recommended.

---

### Post by ScottMorris on 2007-03-27
I agree with PictureThis   DOSBox runs everything from old games to Windows 3.1 :) It is really stable and cross platform, I use it on Windows, Linux and Mac with no issues.

---

### Post by tszanon on 2007-03-27
I once tried running the old game Full Throttle...unfortunately I wasn't very successful. Think I had to do some more tweaking to get there.

---

### Post by icarus.lnx on 2007-03-27
> **tszanon said:**
> I once tried running the old game Full Throttle...unfortunately I wasn't very successful. Think I had to do some more tweaking to get there.

Full Throttle is a SCUMM engine game, try using [SCUMMVM]("http://www.scummvm.org") with it, should work great (I still play Sam & Max Hit the Road with this :)) It's most likely in APT also...

As for other DOS apps/games, DOSBox is the way to go.

---

### Post by ElGimpo on 2007-03-27
haha... I have an oldddddddd "laptop" that still has fullthrottle on it. I love that game!

---

### Post by rolando2424 on 2007-03-27
> **ScottMorris said:**
> I agree with PictureThis   DOSBox runs everything from old games to **Windows 3.1** :) It is really stable and cross platform, I use it on Windows, Linux and Mac with no issues.

I didn't know that...

/me goes search for his floppy disk case...

---

### Post by PictureThis on 2007-03-27
> **tszanon said:**
> I once tried running the old game Full Throttle...unfortunately I wasn't very successful. Think I had to do some more tweaking to get there.

Hmm.. according to [Full Throttle DOSBox ](http://dosbox.sourceforge.net/comp_list.php?showID=756&letter=F) the game should work just fine, have you tried the latest release [v0.70](http://dosbox.sourceforge.net/download.php?main=1)? It's **really** blazing fast.

Setup is easy and for reference an excellent README is included. I love the quickstart advice:
"Type INTRO in DOSBox. That's it." :biggrin:

---

### Post by tszanon on 2007-03-27
@icarus.lnx: I don't even know what SCUMM is...I'm gonna do some research about it and give it a try. Thanks!

@PictureThis: since it was a long ago, it's unlikely that I was using any of the recent versions. Gonna check it out too. Thanks!

---

### Post by GolfGeek on 2007-03-27
Folks
Thanks a million.. The dosbox sounds perfect and it could settle a lot of issues. I am curious about one thing that may or may not get answered. This program makes repeated references to LPT ports for print assignments. Any idea how that will work in the DOSBOX environment? Thanks again

---

### Post by PictureThis on 2007-03-27
> **GolfGeek said:**
> Folks
Thanks a million.. The dosbox sounds perfect and it could settle a lot of issues. I am curious about one thing that may or may not get answered. This program makes repeated references to LPT ports for print assignments. Any idea how that will work in the DOSBOX environment? Thanks again

There is a patch available as you can read [here](http://vogons.zetafleet.com/viewtopic.php?t=13117&highlight=print) but I have never tested it/needed it. You might want to check that out. Keep in mind though that DOSBox was created primarily for games compatibility. Printing from within a DOS app has never been a priority. I'm not familiar with your program but the obvious thing to do is try changing the assignment from "print" to "save" and then import-->printing it from a current app?

---

### Post by tszanon on 2007-03-27
> **GolfGeek said:**
> Folks
Thanks a million.. The dosbox sounds perfect and it could settle a lot of issues. I am curious about one thing that may or may not get answered. This program makes repeated references to LPT ports for print assignments. Any idea how that will work in the DOSBOX environment? Thanks again

From dosbox site ([http://dosbox.sourceforge.net/wiki/index.php]("http://dosbox.sourceforge.net/wiki/index.php")):
> DOSBox emulates an Intel x86 PC, complete with sound, graphics, mouse, modem, etc., necessary for running many old DOS games that simply cannot be run on modern PCs and operating systems, such as Microsoft Windows 2000, Windows XP, Linux and FreeBSD. However, it is not restricted to running only games. In theory, any DOS application should run in DOSBox, but **the emphasis has been on getting DOS games to run smoothly, which means that communication, networking and printer support are still in early developement.**
So, unfortunately, it seems that there is no printer support available yet.

Edit: forget what i said. "PictureThis" answered before me.

---

### Post by GolfGeek on 2007-03-27
Another quick question: I went to DOSbox and have been reading. .it sounds terrific but the question is which download to use. There is no specific for Ubuntu. Should I download the windows version. I guess I am confused because I would like to cut out windows altogether. My favorite scenarion would be to create a folder for the application on the Ubuntu machine. run DOSbox and instruct it to run the DOS application. Am I in the right ballpark

---

### Post by tszanon on 2007-03-28
> **GolfGeek said:**
> Another quick question: I went to DOSbox and have been reading. .it sounds terrific but the question is which download to use. There is no specific for Ubuntu. Should I download the windows version. I guess I am confused because I would like to cut out windows altogether. My favorite scenarion would be to create a folder for the application on the Ubuntu machine. run DOSbox and instruct it to run the DOS application. Am I in the right ballpark

You can find DOSBox in the repositories. I don't remember which version is available there but, anyway, that's how they tell us to get it :) 
> DosBox Ubuntu Linux Howto
1.) Getting DosBox

I'm going to assume (bad idea, I know), that if you are using Ubuntu you are using GNome. Otherwise you'd be using Kubuntu.

    * Click System
    * Click Administration
    * Click Synaptic Package Manager
          o Enter your password
    * Click Search (I find this easier than manually looking and produces the same results)
          o Type dosbox in the search box and press enter
    * Click the selection box in front of the only item to appear, BosBox
    * Check Mark for Installation
    * Click Apply
    * Click the Apply button in the window that just popped up
    * When prompted click the close button

Congratulations, you now have DosBox.
If the available version is old, then I'd suggest downloading the source-code and compiling it.

---

### Post by drpaul on 2007-03-28
Let me suggest the dosprog package. I have found it much better than dosbox for applications that need to print.

HTH

Paul

Sorry. I meant dosemu

---

