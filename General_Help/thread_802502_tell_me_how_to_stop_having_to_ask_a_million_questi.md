---
title: "tell me how to stop having to ask a million questions"
date: 2008-05-21
forum: General Help
---

### Post by karasuman on 2008-05-21
I feel more than a little lost using ubuntu.  I just switched from XP two days ago, and I'm using Hardy now.  I've managed to muddle my way through several different things, but I still feel like I don't know what I'm doing.

I've figured out how to open the terminal and successfully typed things into it.  I have NO idea what any of what I've typed actually meant, though.  I remember learning how to use command line prompts in DOS and understand basically what some of the commands did.  How can I learn the same kind of things for this?

I have NO idea how to install programs except through the "add/remove programs" function, for instance.  I downloaded Thunderbird and failed at doing anything with the file until I let the add/remove programs do it itself (including downloading again).  How can I learn how to be less dependent on automatic features?

And, two more nagging questions...

How do I know if I have 32 bit or 64 bit?  (That has something to do with how much RAM you can handle, right?)  I need to know before I purchase Maple.

How do I change the color of the screen that loads between the log-in screen and my desktop?  I'm going for a green theme, and those few seconds of orange-pink really throw off my vibe.  :)

If anyone can recommend a book or a website that will help me get started with really knowing how to use Linux, I'd really appreciate it.  I'd like to be able to answer questions, not just ask them--and I'd love to be able to ask questions without having to add "but I'm an idiot, so go slow".  :)

---

### Post by mrtomservo on 2008-05-21
For terminal commands, i've always found this page to be useful. 

[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

Most package handling in Ubuntu is graphical.  (Add/Remove programs)  But if wanted to add a program/package and you know the name of it then you can use the command as follows:

```
sudo apt-get install firefox
```

Or to remove it you would use:

```
sudo apt-get remove firefox
```

Hope that helps a little bit!

---

### Post by lswest on 2008-05-21
and about 32/64 bit, you can go to go the terminal and type in ```
uname -a
``` which gives you an output similar to this: ```
lswest@lswest-laptop:~$ uname -a
Linux lswest-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 **i686** GNU/Linux
```
and if it says x86_64 or amd64 (not sure which one it will display, i never use 64 bit) you will have 64 bit, if it says i386 or i686, then it's 32 bit.

*edit* just checked up on it, turns out i686 means that it's 64-bit compliant hardware, not that the OS is running on 64bit.  Sorry.  However, the x86_64 should be present if you're running 64 bit hardware, and not present if you're running 32 bit.

---

### Post by danwood76 on 2008-05-21
The best way to not have to ask so many qs is to use google and search the forums.
Im sure nearly every new linux q has been asked on these several times over.

The login screen can be customised by adding themes (or editing themes) you can change them in the System -> Administration -> Login Window (Local Tab)

If you want more themes then [http://www.gnome-look.org/](http://www.gnome-look.org/) is good.

Weather you have 64 or 32 bit depends on which CD image you downloaded and weather your processor supports it.
If you just downloaded the standard one then probably 32 bit.

---

### Post by sisco311 on 2008-05-21
[URL="http://ubuntuforums.org/showthread.php?t=801404"][B]New to Ubuntu?  Start here...
[/B][/URL]

---

### Post by karasuman on 2008-05-21
> The login screen can be customised by adding themes (or editing themes) you can change them in the System -> Administration -> Login Window (Local Tab)

Yeah, I figured that part out.  I've changed the log-in screen, and I've changed what my desktop looks like.  What I can't figure out how to change is the screen between the two.  After I type in my name/password and log-in, it switches to a pink-orange (empty) screen, then adds the top and bottom bars, and then fills in my desktop background.  Every place I can see to select a solid color has been changed to green.  I don't know how to get rid of the pink-orange, which seemed to be the default shade.

I've been googling and searching these forums like crazy, and I've found the answers to a lot of questions that I haven't had to post about.  That tells me how to solve individual issues, but it doesn't tell me how to figure out how to solve problems for myself, which is what I'm asking for in this post.

I don't know if you intended to sound harsh, but I'm definitely reading this as a chastisement for having to ask anything at all.  :(  I'm doing my best to learn, and I AM trying to find answers for myself before asking.  But you didn't really read what I ask asking about; instead, you assumed that I was asking a dumb question that I obviously would have figured out if I'd bothered to search... and I did search, so I already knew how to get new themes.

---

### Post by rbc on 2008-05-21
Great tutorial for installing:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by lswest on 2008-05-21
this thread should help with the gdm stuff: [http://ubuntuforums.org/showthread.php?t=745869](http://ubuntuforums.org/showthread.php?t=745869)

> **edajai] Re: Change background color after GDM Login before background image appears
One trick for get rid of the the brown screen shown after the GDM Login window is open the file /etc/gdm/PreSession/Default in a text editor with administrator privileges:
```
sudo gedit /etc/gdm/PreSession/Default
```

and search for the part that says:
```
# Default value
if [ &#8220 said:**
> ; then
BACKCOLOR="#dab082"
fi
```

and change it to:
```
# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR=(new color in hex)
fi
```

and about the learning bit...my best advice is this: just work with it, if you mess something up, learn how to fix it, you learn so much more that way than reading a lot of documentation.  Also helps you remember it for later on.

P.S. thanks for the thanks.

---

### Post by xueg0i on 2008-05-21
Even after being an extensive DOS user I do understand your frustration. The only real answers are: read (as in [rtfm]("http://en.wikipedia.org/wiki/Rtfm"), forums and google) and ask (as in use forums, we are always willing to help)

If you really want to be in control, linux has a very nice feature which is called 'man pages'. If you type in a terminal:
```
man anycommand
```
It will give you a explanation of the command in question.

Another thing I find most useful is:
```
apt-cache search thethingyouaresearchingfor
```
This will give you a list with all installable packages which have something to do with "thethingyouaresearchingfor". (scroll up with Alt+PageUp) In the above post you can read how to install packages.

One last important thing:
```
man sudo
```

Good luck with your ongoing quest for knowledge ;)

---

### Post by HermanAB on 2008-05-21
How to stop asking questions?

Go to tldp.org and start reading.  That will keep you out of trouble for a few weeks/months.

---

### Post by Bari on 2008-05-21
For a basic understanding read Rute.  Go here  [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz) you can download it in pdf or html format. Read it and have a play with the commands etc. Each Linux distribution does things slightly differently but this will give you a good basic grounding.  I've certainly learn't more about computing since entering the Linux world mainly as it seems more interesting than Windows.  Good Luck and continue to ask questions and reading the forums as its the best way to learn things.

---

### Post by Jaiinus on 2008-05-21
As a perspective shocker, using XP, did you actually have any idea what you were doing? You knew that action a leads to result a, but there was always so much in between. Ubuntu lets you choose whether you want to keep that paradigm of automagic configuration, installation, and general interface ease of use. At the same time you have the option to complete uninstall what you see (the GUI or graphical user interface) and you'll still be able to do (almost) everything you were able to with it installed and so much more. As far as command line goes, this operating system and its derivative have been the proverbial opiate of the terminal users and can be very arcane and contradictory at times. At my school they require a class in Unix scripting and even after 10 weeks many of my classmates were still having trouble because there is just such a wide array of tools for each situation and often overlaps. Just be patient and you'll see increases in productivity and decreases in wasted time as you gain comfort and ability with the OS.

---

### Post by Helgiks on 2008-05-21
Well, you can't just learn how to solve everything. That's like learning the answer to every question, but by reading about linux and how it works you learn more and more about the system and how it works, by that time you won't have to ask questions about everything. But every beginner to linux feels like you do when they start.

But by asking questions, google-ing, reading forums/books, you will learn more and more, thus won't have to ask all those questions AGAIN, and maybe be able to give back by solving someone else's problems, like people do for you now.

---

### Post by sisco311 on 2008-05-21
> **karasuman said:**
> 
I have NO idea how to install programs except through the "add/remove programs" function, for instance.  I downloaded Thunderbird and failed at doing anything with the file until I let the add/remove programs do it itself (including downloading again).  How can I learn how to be less dependent on automatic features?

[https://help.ubuntu.com/8.04/add-applications/C/install-file.html](https://help.ubuntu.com/8.04/add-applications/C/install-file.html)

---

### Post by danwood76 on 2008-05-21
> **karasuman said:**
> 
I don't know if you intended to sound harsh, but I'm definitely reading this as a chastisement for having to ask anything at all.

Sorry if I sounded harsh, I wrote it in a rush.
It was meant as constructive criticism, it does sound a little harsh I guess. :)

No idea how to get rid of that colour between the two, I just live with it ;) its too short to care about for me.

---

### Post by Tom--d on 2008-05-21
With the login colour.. that is Very very simple :) 

Go to.. 

System > Admin > Login Window > Local > background colour :D Thats it :D

Also, if you want to automatically login.. go to the Security tab

---

### Post by ibuclaw on 2008-05-21
> **karasuman said:**
> I feel more than a little lost using ubuntu.  I just switched from XP two days ago, and I'm using Hardy now.  I've managed to muddle my way through several different things, but I still feel like I don't know what I'm doing.

Don't Worry, You're not alone!
Everyone feels one gripe or another when they first start with Linux.
You have to keep positive in everything you do and have a willingness to learn!
Give it a few months, a few re-partitions of your hard-drive and a few lessons well learnt and you'll forget all the nasties that you had when you started!

> **karasuman said:**
> 
I've figured out how to open the terminal and successfully typed things into it.  I have NO idea what any of what I've typed actually meant, though.  I remember learning how to use command line prompts in DOS and understand basically what some of the commands did.  How can I learn the same kind of things for this?

If you need any help, or need someone to explain to you what each command does step by step. Just ask!
I'm sure that they will be happy to explain.

If you wish to learn how the commands work themselves through self-learning. Linux has two commands that will get you started.
The first being **man**, the second being **whatis**.
ie:
```

whatis cp

man cp

```
> **karasuman said:**
> 
I have NO idea how to install programs except through the "add/remove programs" function, for instance.  I downloaded Thunderbird and failed at doing anything with the file until I let the add/remove programs do it itself (including downloading again).  How can I learn how to be less dependent on automatic features?

In the Ubuntu GUI, there are essentially two apps.
The first being the one you just meantioned.
The second being synaptic.

If you go into "System>Administration" then you should see a link named "Synaptic Package Manager".

This gives you a little bit more control, and you can generally see alot more packages than what you can in Add/Remove Programs.

In the command-line you have two or three too.
First being **apt-get**, which is only good at being told what to do. Other than that it is quite a dumb command-line app (no offense to you apt-get users).

The second is called **aptitude**, which you can consider the command-line version of synaptic (has a funky ncurses UI).

And I think that having automated package installments is brilliant.
You just search, mark (check dependancies) and install!

Generally, in Linux. We can be considered quite fortunate, as we never have to go searching round the internet for programs that we wish to install, because we have everything that we could ever possibly need in the repositories that are availiable to us!

> **karasuman said:**
> 
And, two more nagging questions...

How do I know if I have 32 bit or 64 bit?  (That has something to do with how much RAM you can handle, right?)  I need to know before I purchase Maple.

32bit and 64bit is to do with your CPU processor.

Whether or not you have one or the other really depends on how old your PC is. But in general:
If you have an Intel, you generally have a 32bit processor.
If you have an AMD, unless you have an old chip, then you are most probably have a 64bit processor.

You generally don't have to worry about this if you let the repositories handle everything.

Though I generally recommend that you go for the 32bit version, as it is backwards compatible with 64bit machines.
Rather than the vice-versa. (Getting a 64bit Ubuntu Installation and putting it the CD in a 32bit PC) where the CD will fail to boot as the 64bit assembly will not be recognised by the 32bit CPU.

> **karasuman said:**
> 
How do I change the color of the screen that loads between the log-in screen and my desktop?  I'm going for a green theme, and those few seconds of orange-pink really throw off my vibe.  :)

I'll have to check this when I get back on my Ubuntu Machine, but on my current OS, I can change the GNOME back-colour by right-clicking on the Desktop and selecting "Change Desktop Background".
There is a small drop-box with the title "Desktop Colours" next to it (That will be the control).

> **karasuman said:**
> 
If anyone can recommend a book or a website that will help me get started with really knowing how to use Linux, I'd really appreciate it.  I'd like to be able to answer questions, not just ask them--and I'd love to be able to ask questions without having to add "but I'm an idiot, so go slow".  :)

Sites you might enjoy:
[LIST]
[*][Google Penguin]("http://www.google.com/linux")
[*][Ubuntu Help Docs]("https://help.ubuntu.com/8.04/")
[*][Ubuntu Geek]("http://www.ubuntugeek.com/")
[*][The only Linux Bible you'll ever need...]("http://tldp.org/guides.html")
[*][The UNIX Forums]("http://www.unix.com/")
[/LIST]

Regards
Iain

---

### Post by strabes on 2008-05-21
> **danwood76 said:**
> No idea how to get rid of that colour between the two, I just live with it ;) its too short to care about for me.

Did you not see this post earlier in the thread?> Re: Change background color after GDM Login before background image appears
One trick for get rid of the the brown screen shown after the GDM Login window is open the file /etc/gdm/PreSession/Default in a text editor with administrator privileges:

```
sudo gedit /etc/gdm/PreSession/Default
```

and search for the part that says:
```
# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR="#dab082"
fi
```

and change it to:
```

# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR=(new color in hex)
fi
```

You can find the hex value of the color you want when you open the color select box in the login window screen.

---

### Post by Cap'n Skyler on 2008-05-21
> **karasuman said:**
> Yeah, I figured that part out.  I've changed the log-in screen, and I've changed what my desktop looks like.  What I can't figure out how to change is the screen between the two.  After I type in my name/password and log-in, it switches to a pink-orange (empty) screen, then adds the top and bottom bars, and then fills in my desktop background.  Every place I can see to select a solid color has been changed to green.  I don't know how to get rid of the pink-orange, which seemed to be the default shade.

I've been googling and searching these forums like crazy, and I've found the answers to a lot of questions that I haven't had to post about.  That tells me how to solve individual issues, but it doesn't tell me how to figure out how to solve problems for myself, which is what I'm asking for in this post.

I don't know if you intended to sound harsh, but I'm definitely reading this as a chastisement for having to ask anything at all.  :(  I'm doing my best to learn, and I AM trying to find answers for myself before asking.  But you didn't really read what I ask asking about; instead, you assumed that I was asking a dumb question that I obviously would have figured out if I'd bothered to search... and I did search, so I already knew how to get new themes.

hi and welcome to the forums.
first off NEVER get chapped at any attitude from linux "pro's" some have a giant cup of elitism in their hands.ugh
as for the rest of us,yes like was posted,try to use google and the forums.i also can suggest the Sams books--they are chock full of very good new user info and how to's.
[http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942](http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942)
[http://www.amazon.com/Beginning-Ubuntu-Linux-Novice-Professional/dp/1590596277](http://www.amazon.com/Beginning-Ubuntu-Linux-Novice-Professional/dp/1590596277)
and my fave of all time for the new users 
[http://www.amazon.co.uk/Ubuntu-Linux-Unleashed-2008-Covering/dp/067232993X](http://www.amazon.co.uk/Ubuntu-Linux-Unleashed-2008-Covering/dp/067232993X)
it includes a dvd in case you need it,or want to pass it along to a friend.
i like some books because you can get away from the 'net and the comp and absorb it.and you can do it with no posts etc LOL
FYI there are a LOT os commands with linux that are similar between distros,so if you can get one up and working and all the bugs for your needs worked out,you can do so with other distros as well.some of the DOS and linux commands are similar.while being similar you already know what they are for.for me the maddening thing is once you do it right,usually the linux/unix gives you no idea if you did it right.no reward for getting it right LOL .
  a LOT of the folks here are AWESOME with command line....i wish i was LOL.  search out and bookmark any web sites with good lists of commands for reference.
 and read read read!!
i have been using linux since 2004 and right now is awesome for linux--and Ubuntu is right at the top one or two for ease of use and "it just works". 
  so welcome and ask away.
:popcorn:

---

### Post by lswest on 2008-05-23
I just had a look at the gdm stuff, that fix i posted works for Gutsy, but in hardy all you have to do is (in the login window preferences) under the theme selection you can choose the background colour.  That is what you want to do. (see attached screenshot) - Sorry for the outdated advice, it doesn't seem to work in Hardy anymore.

---

