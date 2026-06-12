---
title: "[SOLVED] Sound Multistreaming"
date: 2008-07-04
forum: General Help
---

### Post by Nirkon on 2008-07-04
Hi guys!!

I made the move yesterday(OFFICIALY, because I do have an EeePC with Xandros, after 11 years of using Windows, still dual booting for gaming, my Ubuntu is now my main OS!).
Yesterday was a long long day... (Had to reinstall windows twice and ubuntu 3 times to get it working... long story... dual booting GRUB ERRORS)

Maybe I can't find the solution on google or here because I missed something big...

but I can't get sound output multistreaming... I want to play some music with that RythmBox sound player while im playing a youtube video...
now the problem is I can't hear any sound from youtube while rythmbox is even initiated (not even playing music).

I looked all over the sound options... my setup is Genius 5.1 Surround Sound speakers.

Help please.

Thanks in advance,

Nirkon

EDIT:
I also have a different 'problem'.. I CTRL-C some text from firefox, quit firefox, launch it again, and the copied text 
isn't saved... nothing is pasted when I do CTRL-V.... any ideas?

---

### Post by Frozsyn on 2008-07-04
I don't know the answer, but I think you should precise if the problem occurs only when mixing rythmbox with flash plugin, or if it is also the case for rythmbox + totem, or totem + flash plugin. My guess is that flash plugin is the central problem... we will see

---

### Post by danwood76 on 2008-07-04
This is a pulse audio issue.
Ubuntu hardy has moved to pulse as its default but it needs a bit of configuration to get it working right.

Check this guide:
[http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+audio+setup](http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+audio+setup)

---

### Post by Nirkon on 2008-07-04
Thats a bit complicated for a second-day user.
Can't find the asound.conf after the first command.

Anyway I 'found' a solution for my second problem,
If i click CTRL+C multiple times on the thing I want to copy then it will work.

---

### Post by danwood76 on 2008-07-04
With regards to the second command in that tutorial press Alt + F2 and in the application box copy the following:
```

gksudo gedit /etc/asound.conf

```
The gksudo part will prompt for a password and give you admin rights.
Gedit is the name of the text editing program, and finally the files path.

Its highly likely that the file doesnt exist yet and needs creating, this command will open an existing file but also create a file if one doesnt exist.

And also for the second bit of section 2 do the same again:
```

gksudo gedit /etc/libao.conf 

```
I will help you work through the tutorial if you like.
You might learn some useful stuff :)

-- edit --

Btw the above can be executed just the same from a terminal, its easier just to type sudo as opposed to gksudo but either should work.

---

### Post by Nirkon on 2008-07-04
Thanks a lot for your help!! I did the tutorial and got everything working! :)
I wish though they'd put these kinds of things in the guide for absolute beginners :)

Anyway I have a different problem now... well I have a second keyboard layout, hebrew,
but everytime I restart ubuntu I can't use my layout switching (I set one to ALT+SHIFT)..
in order to use that switching again I have to remove my layout and add it again every single startup...

any suggestions?

---

### Post by Nirkon on 2008-07-04
(sorry, accidental repost)

---

### Post by danwood76 on 2008-07-04
Found a thread that might help you: (Post 7)
[http://ubuntuforums.org/showthread.php?t=798555&highlight=hardy+keyboard+layout+switching](http://ubuntuforums.org/showthread.php?t=798555&highlight=hardy+keyboard+layout+switching)

I only use one layout so i cant really help, hopefully the xorg config in that thread should help.

---

### Post by Nirkon on 2008-07-05
> **danwood76 said:**
> Found a thread that might help you: (Post 7)
[http://ubuntuforums.org/showthread.php?t=798555&highlight=hardy+keyboard+layout+switching](http://ubuntuforums.org/showthread.php?t=798555&highlight=hardy+keyboard+layout+switching)

I only use one layout so i cant really help, hopefully the xorg config in that thread should help.

thanks again, that worked.

This is the end of my problems (hopefully, lol).

---

### Post by danwood76 on 2008-07-05
Well done.
Please mark the thread as [SOLVED] using thread tools at the top of the page.

---

