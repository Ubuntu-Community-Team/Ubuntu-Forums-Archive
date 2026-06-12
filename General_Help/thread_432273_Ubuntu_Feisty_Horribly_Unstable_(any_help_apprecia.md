---
title: "Ubuntu Feisty Horribly Unstable (any help appreciated)"
date: 2007-05-03
forum: General Help
---

### Post by cdrom600 on 2007-05-03
I had been using Ubuntu 6.10 since about February (it was working well), and I upgraded to Feisty about two weeks ago.  Since then, my computer has been plagued by problems, and they have gotten substantially worse in the last two or three days.  It's to the point now where, unless I can resolve these issues, I will need to boot into Windows - there's just no other way I'll be able to actually get work done on this computer.

A summary of the worst problems, in approximate order of the time I noticed them after the upgrade:

- When the system boots, metacity does not load for (literally) another five or so minutes.  The system boots and the Ubuntu boot screen (with three icons on the bottom left) appears after I log in, and then that boot dialog stays on screen.  The startup applications (Desktop Search, Beryl Manager, Bluetooth Manager) do not load until metacity loads.  I can start applications, but they appear without title bars or borders, and they do not appear in the tray.  If I open an application and then wait for metacity to start, the title, etc. will appear on windows already drawn on screen.  I am not using beryl as the default window manager.

- The gnome-pilot application hangs when it gets to syncing the task list on my PDA (Palm Tungsten E) with Evolution.  This didn't happen in Edgy, and I really need it to synchronize.

- Some multimedia apps have failed since the upgrade.  I suspect that I could fix this with a little tinkering, though, and am not holding this against Feisty (as I am the rest of these issues).

- Firefox has been randomly hanging very frequently lately.  Occasionally, I am forced to restart the X server (Ctrl-Alt-Backspace).

- When the screen is turned off (as I've told it to under the "Power Management" applet), it refuses to turn back on.  No mouse movements or key presses will restore it, and neither will restarting the X server.  I am forced to hit the hard reset button.

- Just today, I was monitoring Azureus's main screen with Firefox and Evolution open in the background.  My transfer rates for Azureus dropped to a few bytes/s, and then Azureus crashed.  I then opened the Firefox window, and it crashed.  Evolution just disappeared from the system tray.  I tried to start the Gnome system monitor; it didn't start.  I started the terminal and got an error message about some input/output error.  Then, my Gnome panels disappeared from the screen and I was left staring at my background image and an otherwise completely blank desktop.  Ctrl-Alt-Backspace to restart the X server brought me to a blank screen, and a few minutes later I hit the hard reset button on the computer for the umpteenth time in the last week.

- The system as a whole has a habit of freezing for long periods of time in general.

I am going to run a fsck now, and then maybe run memtest86 (if I have time).  I hope that someone will be able to help me diagnose and solve these issues; otherwise, I will be forced back to Windows (at least for now).  I have generally been pleased with Ubuntu, but Feisty has been way below the quality I saw in Edgy.  When it comes down to it, I need to use my computer one way or the other.  Tonight, that may mean using Windows.

Having said that, if I can fix this situation, I would obviously be happy to do so.  Consider this a plea for help as well as a warning to those considering upgrading to Feisty.

Help is appreciated.

---

### Post by justinjstark on 2007-05-03
I'm in no way an expert, but with these kinds of problems I would seriously wonder about bad hardware.

---

### Post by cdrom600 on 2007-05-03
> **justinjstark said:**
> I'm in no way an expert, but with these kinds of problems I would seriously wonder about bad hardware.
I wonder about this too, but it seems unlikely.  I just ran fsck on every partition of the disk, and it found nothing.  I will run memtest86 overnight, but I don't think it will find anything.  I bought my RAM back in January and ran memtest86 on it for several hours as soon as I had installed it.

---

### Post by rjfioravanti on 2007-05-03
It is very possible that your upgrade messed up things, depending on how you did it. How did you upgrade?

What kind of hardware do you have... video card, wireless card

Have you used things like Automatix to install software?

---

### Post by cdrom600 on 2007-05-03
> **rjfioravanti said:**
> It is very possible that your upgrade messed up things, depending on how you did it. How did you upgrade?

What kind of hardware do you have... video card, wireless card

Have you used things like Automatix to install software?

I upgraded through the update manager, as was recommended.  I have an nvidia graphics card, and no wireless card.  I haven't used Automatix or anything; I've heard too many bad things.

---

### Post by eugene.shaddow on 2007-05-03
Hi

I don't understand clearly what your problem is since you have not specified what type of system you are operating. Also, 6.1 is edgy, I am running 7.1 Feisty Fawn, sounds like you inadvertently mixed your upgrade which is not a nice thing to do when upgrading. This will cause programs to crash not load, etc because some of the programs would no longer be compatible. If this is the case, than the easiest way to correct things unfortunately would be to reinstall your version of debian Ubuntu or Kbuntu it really doesn't matter which, since you can easily change one to the other.

---

### Post by cdrom600 on 2007-05-03
> **eugene.shaddow said:**
> Hi

I don't understand clearly what your problem is since you have not specified what type of system you are operating. Also, 6.1 is edgy, I am running 7.1 Feisty Fawn, sounds like you inadvertently mixed your upgrade which is not a nice thing to do when upgrading. This will cause programs to crash not load, etc because some of the programs would no longer be compatible. If this is the case, than the easiest way to correct things unfortunately would be to reinstall your version of debian Ubuntu or Kbuntu it really doesn't matter which, since you can easily change one to the other.

Perhaps I wasn't too clear - I was more than a little annoyed when I wrote the post.  I was running 6.10 (Edgy), and upgraded through the upgrade manager to 7.04 (Feisty).  The upgrade to 7.04, Feisty, completed successfully.  I don't believe that I'm running a "mixed" system; everything has been upgraded to Ubuntu 7.04 (Feisty).

---

### Post by jerrylamos on 2007-05-03
Well, how about Edgy Eft 6.10?  

I'm on Feisty 7.04 (with workarounds, none sound like your problems) and also Gutsy 7.10 (very early level liable to be unstable) and this happens to be Dapper 6.06.1 LTS, i.e. to be supported for the next 2 years.  This is a quad boot system with all three levels plus Windoze so I can flip back and forth and compare.

If 6.10 Edgy runs fine, I'm not sure what advantage you'd get from Feisty.  Some people with wireless run better with Feisty.  Others wireless breaks.  Some people like me have problems with Feisty Network Manager, some don't.  You don't need Network Manager on Edgy but you could install it if for some reason (beyond me) you wanted it.  My impression Gutsy goals are to smooth over the function they have rather than add new. (read between the lines fix some Feisty bugs or is it my wishful thinking).

Now they tried to speed up boot with Feisty.  I think that's what broke CD Live "persistent" mode.  They also worked on combined IDE, SATA, USB support, which on some systems (like mine) ran afoul of the boot speedup.  Some people with SATA may get some benefit from Feisty.

Just because they brought out a new release doesn't mean the previous one still isn't a good workhorse.

And by the way I do some running with Knoppix, Puppy, PCLinuxOS, ... you could check out distrowatch.com for some alternatives to Ubuntu.  I sample the others and wind up back on Ubuntu and do some work with XP; on our systems, XP's LAN workgroup file sharing support sucks.  And by the way, with 5 computers here, no way we'd buy 5 Vista's.

My opinon.  Cheers, Jerry

---

### Post by cdrom600 on 2007-05-03
I'm wondering if it's possible that Azureus is causing the instability.  I will try running without it tomorrow, although it is by far my favorite Bittorrent client (are there any others?  on Windows, I used BitComet).
This seems like a remote possibility to me, but I'm willing to try.
I am going away for the night now, and will run memtest86 overnight.  In the meantime, would anyone knowledgeable please respond?

---

### Post by justinjstark on 2007-05-04
> **cdrom600 said:**
> I'm wondering if it's possible that Azureus is causing the instability.  I will try running without it tomorrow, although it is by far my favorite Bittorrent client (are there any others?  on Windows, I used BitComet).
This seems like a remote possibility to me, but I'm willing to try.
I am going away for the night now, and will run memtest86 overnight.  In the meantime, would anyone knowledgeable please respond?

Java can be dicey.  Hence, I stay away from java programs as much as possible.  Let us know what you find out.

---

### Post by Sef on 2007-05-04
Could you post your sources list.  Let's make sure that is ok.

Applications > Accessories > Terminal

```
cat /etc/apt/sources.list
```

---

### Post by kelvin spratt on 2007-05-04
i'm no expert have you got beryl and azures permently on as this could be your trouble as with anything try simple things first azuares as good as itis has issues with the latest java  try ktorrent from their site as the fiesty version is not stable set it up correctly it uses minute amounts of resources switch beryl off totally
and give it a try again berryl uses huge amounts of ram combined with azuarus will really hammer your system also check you have enough ram and it is not low grade which again can give strange results
512 mb of good ram can often outperform 1gb of lowgrade ram and good luck at least you are trying to sort pboblems out i upgraded to fiesty with no probs fortunatly but i did it by reformating with gparted live cd
and downloading the live disc i don'd believe in going over the top to upgrade i once did that with windows
98 to 98se and it was a disaster just a thought

---

### Post by Rich43 on 2007-05-04
> **kelvin spratt said:**
> i'm no expert have you got beryl and azures permently on as this could be your trouble as with anything try simple things first azuares as good as itis has issues with the latest java  try ktorrent from their site as the fiesty version is not stable set it up correctly it uses minute amounts of resources switch beryl off totally
and give it a try again berryl uses huge amounts of ram combined with azuarus will really hammer your system also check you have enough ram and it is not low grade which again can give strange results
512 mb of good ram can often outperform 1gb of lowgrade ram and good luck at least you are trying to sort pboblems out i upgraded to fiesty with no probs fortunatly but i did it by reformating with gparted live cd
and downloading the live disc i don'd believe in going over the top to upgrade i once did that with windows
98 to 98se and it was a disaster just a thought

Punctuation? What moron tought you english?

---

### Post by WW on 2007-05-04
Rich43: Please abide by the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy").  In particular, see numbered item 1 in Section I on that page.

By the way, I think you meant "taught" and "English". :)

---

### Post by tgalati4 on 2007-05-04
I still stand by the advice:  "Never trash a working system."

Sometimes it is better to put in another hard disk (or create a new partition) and do a fresh install to try out a new distribution.

The upgrade procedure is too easy to use and unfortunately can break things.  

The automatic upgrade means that you don't go through the effort to download and burn a new Live CD to test it first to see if it is compatible with your system.  If you can run the Live CD for a few days and run the basic applications (and they work--but slowly from CD), then you can have some confidence that a hard disk install will be successful.

As the Ubuntu user base grows, the types of hardware being used will expand and more "edge" cases will show up on these forums.

In this case, it could be a hardware problem that has developed at about the same time that the upgrade to Feisty occured.  So there may be a false correlation, but to the end user it looks like the upgrade corrupted a working system.

---

### Post by kelvin spratt on 2007-05-04
rich 43
Punctuation? What moron tought you english?
I'm Fuckiing DYSLEXIC the only moron is you pleople try to help wankers like you and this is the thanks you give and as far as intelligence is concerned my iq is 145 that 145 more than yours tosser

---

### Post by WW on 2007-05-04
kelvin: Please abide by the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy").  In particular, see numbered item 3 (concerning profanity) in Section I of that page.

---

### Post by useLinux, on 2007-05-04
- When the screen is turned off (as I've told it to under the "Power Management" applet), it refuses to turn back on. No mouse movements or key presses will restore it, and neither will restarting the X server. I am forced to hit the hard reset button.


I actually get that problem too. I'm not sure why though. Something maybe is wrong with Fiesty

---

### Post by kelvin spratt on 2007-05-04
WW you are right but people that throw insults at people diserve what they get back 
there is a saying in the Uk people that live in glass houses should not throw stones
and if you make jokes about somebodies writing you should make sure you can spell yourself
so here is the bottom line i won't post on this forum again

---

### Post by cdrom600 on 2007-05-04
> **justinjstark said:**
> Java can be dicey.  Hence, I stay away from java programs as much as possible.  Let us know what you find out.
Well, the system just froze and Azureus wasn't running.  Specifically, I tried to click on Evolution in the task bar (Firefox was running in the foreground.)  The computer froze, and only the mouse still worked.  I came back a few minutes later, and it was still frozen.  The clock had frozen and was showing the time that the system froze, too.
A hard reset, of course, fixed it - I didn't think of restarting only X until later.

---

### Post by cdrom600 on 2007-05-04
> **Sef said:**
> Could you post your sources list.  Let's make sure that is ok.

Applications > Accessories > Terminal

```
cat /etc/apt/sources.list
```

```
$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

# Major bug fix updates produced after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

# Backports
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

# Security
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main universe multiverse

# Beryl
deb http://ubuntu.beryl-project.org/ feisty main

# Cinelerra
deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./

deb http://archive.canonical.com/ubuntu feisty-commercial main

# Medibuntu
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

```

---

### Post by cdrom600 on 2007-05-04
> **kelvin spratt said:**
> i'm no expert have you got beryl and azures permently on as this could be your trouble as with anything try simple things first azuares as good as itis has issues with the latest java  try ktorrent from their site as the fiesty version is not stable set it up correctly it uses minute amounts of resources switch beryl off totally
and give it a try again berryl uses huge amounts of ram combined with azuarus will really hammer your system also check you have enough ram and it is not low grade which again can give strange results
512 mb of good ram can often outperform 1gb of lowgrade ram and good luck at least you are trying to sort pboblems out i upgraded to fiesty with no probs fortunatly but i did it by reformating with gparted live cd
and downloading the live disc i don'd believe in going over the top to upgrade i once did that with windows
98 to 98se and it was a disaster just a thought
I should have been more clear - I am not currently running Beryl, but the Beryl Manager is running in the background so I can switch to Beryl if I want to.

---

### Post by cdrom600 on 2007-05-04
My Palm issue seems to have been resolved.  I think it has to do with removing the Pilot Applet icon from my Gnome panel, but I'm not 100% sure.
**Updated:** It turns out that for some reason, gpilotd cannot sync task list entries that don't have due dates.

---

### Post by Ateo on 2007-05-07
It's not unstable just because *you are* having issues with it. You should really reword your subject.

It would be 'unstable' if everyone were having issues.

Learn to word correctly. And perhaps check your hardware.

---

### Post by edmondt on 2007-05-07
> **Ateo said:**
> It's not unstable just because *you are* having issues with it. You should really reword your subject.

It would be 'unstable' if everyone were having issues.

Learn to word correctly. And perhaps check your hardware.

There are many users including myself who had major problems after upgrading Feisty from Edgy, it was beyond repair to the point I have to reinstall because the time it will take to resolve the issues is just not worth it.

---

### Post by cdrom600 on 2007-05-08
My metacity load issue was solved with [this suggestion]("http://ubuntuforums.org/showthread.php?p=2614868#post2614868").  It seems like many users are having multiple problems, but with roughly the same symptoms.

---

### Post by w00dchaz on 2007-05-11
I think there are indeed some instability problems. I upgraded to Feisty two days ago and anytime I leave the computer on for several hours, I go back to find it has crashed, either with error messages or just a blank screen with a cursor. I'll write down the error messages next time.  Also, Nibbles doesn't work in Gnome games. That's what I've found so far. 

No hardware problems before this. Edgy was working PERFECTLY. I thought Feisty was a little further along than this or I wouldn't have upgraded :(

---

