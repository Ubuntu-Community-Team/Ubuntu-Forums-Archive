---
title: "How to run Netflix with the demise of  Linux Google chrome 32 bit"
date: 2016-05-29
forum: General Help
---

### Post by neilsfarm on 2016-05-29
How to run Netflix with the demise of  Linux Google chrome 32 bit


The recent loss of Google chrome 32 bit means  new users of Netflix on  XUbuntu, Ubuntu, etc 32 bit are not able to use Netflix or other video streaming services with DRM.


The current {last checked 2 week of posting} is that Netflix does not work with Linux- Firefox or Chromium based web browsers. This is because they do support DRM and/or the needed video support file.


Netflix will tell you to install silver light and use a HTML 5 compliant browser. This info is out of date.



_***Some Solutions***_


1. If your hardware supports 64 bit apps....upgrade to 64 bit and install Chrome 64 bit.


Tested with Xubuntu 14.04  64 bit on 6 year old EEEPC 1001p. 




*Can't upgrade see below;*




2. The following is not a very good idea as Google Chrome 32 bit no longer has security updates.


Chrome 32 bit is still available for download from a Gentoo lib IE    [http://bbgentoo.ilb.ru/distfiles/](http://bbgentoo.ilb.ru/distfiles/)    (search for the googlechrome32bitstable last 2016 build NB lower case comes after upper case letters you may need to keep looking). Pin Netflix to the desktop and do not use chrome 32bit for anything else.


See also [http://unix.stackexchange.com/questions/267587/where-to-download-chrome-32bit-since-it-has-been-discontinued-by-Google](http://unix.stackexchange.com/questions/267587/where-to-download-chrome-32bit-since-it-has-been-discontinued-by-Google)


Tested on XUbuntu 16.04 32 bit and 2007 era HP Laptop NC6400




3. Install wine and play on Linux, before installing a MS windows version of Firefox 32bit with POL, download the latest version and when installing Firefox a prompt will allow you to install from a file on yr disk. The version of Firefox that POL downloads is an older version. 


Tested on XUbuntu 14.04 and Firefox,  not tested with MS windows Chrome but is worth trying.


This idea is also on another Ubuntu forum(s). 




4. Install Opera or Vivaldi browser. You will also need two Google chrome files see [https://vivaldi.net/forum/vivaldi-browser-for-Linux/9131-Netflix-and-vivaldi-on-Linux#50688](https://vivaldi.net/forum/vivaldi-browser-for-Linux/9131-Netflix-and-vivaldi-on-Linux#50688)


I have not tried this so I can not recommend this, it may or may not work.




5. Wait for Linux Firefox to have DRM support.  MS Windows Firefox has DRM and video support for Netflix..... When Linux too?




NB There is a downside to all these solutions and yup you try any or all of this at your own risk.

---

### Post by T.J. on 2016-05-29
I say this with the greatest respect, and in no way am I trying to detract from your efforts to help people. =)  As a programmer with years of experience, I have some practical knowledge of the subject.

The best advice I can offer regarding 32 bit anything is:** don't **unless there is no other option.

I doubt anyone coming here even has a computer or device that is older than 10 years. There is *absolutely* no reason not to use 64 bit software. 32 bit is a 30 year old technology, and is plagued with problems that most users today have no idea how to deal with.  A significant portion of computer/device users today weren't even born when it was created.

I realize that no one has reason to, but please trust me when I say the demise of 32 bit is something that is long overdue, and should have been completed years ago. Users are better off because of what Google did; especially considering that browsers have security issues.  The reasons are technical and take a long time to explain.

The only reason I post is that it should be said that 32 bit workarounds should not be used, unless absolutely necessary.  Everyone using Linux who can, should upgrade to 64 bit and be done with it.  They simply are better off for the effort, and if they need to - a 64 bit system can still run 32 bit programs when there is no 64 bit version.

---

### Post by QIII on 2016-05-29
Let me get my wellies on before I step into this...

32bit has as its primary handicap the fact that developers have moved on to 64bit.  Since we don't like to have to maintain too many codebases, and many of us have pretty much stopped 32bit development.  Many are still happily producing code for 32bit applications.

It's as simple as that.  But stuff that is 32 bit and being maintained is perfectly fine to use and there is absolutely no reason to not use it.

10 year old computers?  A lot more than you apparently think.

I go all the way back to 8-bit.  The advent of 16 bit caused a slow but steady move to 16 bit products.  Eventually a few 8bit hangers on were either crushed or converted.  16 to 32 was a quicker change, but the issue of hangers on was the same.

I expected the advent of the 64bit world to be more swift change still.  But that didn't happen.  There has been no rush.  The change has been an evolution.  Eventually hangers on will go extinct, but I think that is a long way off yet.

---

### Post by ajgreeny on 2016-05-29
> I doubt anyone coming here even has a computer or device that is older than 10 years. There is absolutely no reason not to use 64 bit software. 32 bit is a 30 year old technology, and is plagued with problems that most users today have no idea how to deal with. A significant portion of computer/device users today weren't even born when it was created

I totally agree with QIII and think T.J. must be living in a world that is far removed from mine.

I still have 2 machines that are 32bit only and have only last year got rid of a very old laptop that was 32 bit, not because it did not work with Lubuntu, but simply because it was not needed any more and had too small a hard disk; it did not seem worthwhile spending money on a bigger hard disk for such a machine.

---

### Post by lisati on 2016-05-29
> **T.J. said:**
> 
I doubt anyone coming here even has a computer or device that is older than 10 years. There is *absolutely* no reason not to use 64 bit software. 32 bit is a 30 year old technology, and is plagued with problems that most users today have no idea how to deal with.  A significant portion of computer/device users today weren't even born when it was created.


I wish to respectfully disagree. One of my machines is at least 15 years old, and trying to run 64-bit software on it is likely to be a complete waste of time. When I blow the dust off it, just for the fun of it, I'm likely to use a minimal CLI-based installation.

---

### Post by mörgæs on 2016-05-30
Thanks for posting and thanks for helping to keep the 32 bit computers in a useable state. I have several of them. It will also come in handy for people buying some of the new 32 bit ones available.

If you mark the thread solved there is a better chance that people will find it.

---

### Post by DuckHook on 2016-05-30
Not to pile on, but I have an atom-based Asus thin client only about 4 yrs old that will only run 32 bit due to a hobbled video subsystem that Intel refuses to provide 64-bit drivers for.

32 bit is alive and well, and is absolutely indispensable even for relatively modern HW.

---

### Post by T.J. on 2016-05-30
> **QIII said:**
> Let me get my wellies on before I step into this...

LOL!  Good evening! =) What I said was "The best advice I can offer regarding 32 bit anything is:** don't **unless there is no other option." Obviously, if you have a 32-bit processor, you can't run 64-bit code. I was speaking about running 32-bit code on a 64-bit processor. In my opinion, hybrid processors are problematic.

> 32bit has as its primary handicap the fact that developers have moved on to 64bit.  Since we don't like to have to maintain too many codebases, and many of us have pretty much stopped 32bit development.  Many are still happily producing code for 32bit applications.




I freely admit that I am biased to some degree, mostly because I am also one of those developers you mentioned as well. No one is "happily" producing code for 32 bit. We do so, because in most cases, the compiler takes care of most of the details. As long as it isn't an annoyance, I think you will agree we usually do a lot of things related to code. 

> 
 But stuff that is 32 bit and being maintained is perfectly fine to use and there is absolutely no reason to not use it.


Running a 32-bit process on a 64-bit AMD64 processor is possible, but it is less than ideal.  Just having  32-bit circuits in a 64-bit processor is hugely power inefficient, because you have to have more circuits in the processor to deal with multiple modes of operation.

Memory efficiency and hard drive access is also affected.  In order to use more than 4GB when using a 32 bit OS on a 64 bit processor, you have to resort to what I call "ugly hacks" because the OS does not use the full addressing space of the processor. This leads to more swapping of memory pages, wear and tear on your swap device, and so on.  

Not anticipating the differing processor mode users run your code on can produce instances of run-time bugs in the software that would otherwise not occur.  There are details, such as the width of the registers and memory mapping, that have a direct effect on algorithms and how bug free - and hence how secure they are.  Software security can depend a great deal on making sure the compiler generates code that behaves only as you expect.  

I think the most controversial comment I made was: "32 bit is a 30 year old technology, and is plagued with problems that most users today have no idea how to deal with."

32 bit is 30 years old.  Intel released the 80386 in 1986.  As for "plagued with problems that most users today have no idea how to deal with", that is also true when referring to software and the fact that world has moved on.  By keeping 32-bit around, uncertainty and problems abound. Duckhook's comments about being forced to use a 32-bit driver because the 64-bit ones are unavailable is an example. 

AMD64 and Itanium replaced 32-bit in the mainstream over 10 years ago. There is no reason for Google to retain 32-bit. Remember, their main concern is their own systems. It's all good though, you can always port it yourself.

---

### Post by T.J. on 2016-05-30
> **DuckHook said:**
> Not to pile on, but I have an atom-based Asus thin client only about 4 yrs old that will only run 32 bit due to a hobbled video subsystem that Intel refuses to provide 64-bit drivers for.

32 bit is alive and well, and is absolutely indispensable even for relatively modern HW.

Since Intel usually provides source code for their video drivers, I am curious why that would be.  Would you mind providing some more details?  I am genuinely interested.

---

### Post by DuckHook on 2016-05-30
Because this one uses a baked-in piece-of-junk cedarview graphics chip that Intel contracted from a third party and therefore cannot release open code for.

This thread: [http://ubuntuforums.org/showthread.php?t=2192251](http://ubuntuforums.org/showthread.php?t=2192251)

I am happy to report, however, that the 32-bit proprietary cedarview driver was ultimately manhandled into some form of functionality with 14.04 and I can install Lubuntu but only after nuking a phantom LCD screen at boot through use of a kernel parameter.

That box was more trouble than a carload of monkeys and I would not have been able to manage it without a 32-bit OS.

---

### Post by T.J. on 2016-05-30
> **DuckHook said:**
> Because this one uses a baked-in piece-of-junk cedarview graphics chip that Intel contracted from a third party and therefore cannot release open code for.

Wow, that is absolutely crap-tastic!  I'm sorry you ended up in that, Duckhook.  I'm glad I have made a point of avoiding Intel GPUs.

---

### Post by kerry_s on 2016-05-30
check the software center see if 32bit version has kodi.
i use kodi on 64bit. i add the super repo & go to town on the add ons. exodus(installed via addon installer addon) & animeram being my most used add ons.

---

### Post by jim_deadlock on 2016-05-30
Netflix has worked on 64bit Chrome out of the box for some time now. Have you tried it?

---

### Post by vasa1 on 2016-05-30
> **jim_deadlock said:**
> Netflix has worked on 64bit Chrome out of the box for some time now. Have you tried it?
OP seems to have a 32-bit system.

---

### Post by jim_deadlock on 2016-05-30
I'll get my coat.

---

### Post by SeijiSensei on 2016-05-30
The answer to your question is to use Firefox and [Pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") which has both 32-bit and 64-bit implementations.  You'll also need to install a User-Agent spoofer in your browser; I use [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") with this User-Agent string:
```
Mozilla/5.0 (Windows NT 10.0; rv:41.0) Gecko/20100101 Firefox/41.0
```

---

### Post by kerry_s on 2016-05-30
If you just can't live without Netflix you can just grab a cheap alternative with android.
I have a fire TV stick & a tablet, both I picked up for less than $30 each. But like I said grab kodi & cut the cord, save some dollars on entertainment. I have kodi on everything, haven't had cable TV for more than year. I dropped phone & cable, with the money I saved I got better internet & it's still way cheaper than what I use to pay.

---

