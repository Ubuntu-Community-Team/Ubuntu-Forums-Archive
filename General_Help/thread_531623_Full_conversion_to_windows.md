---
title: "Full conversion to windows"
date: 2007-08-21
forum: General Help
---

### Post by tyggna1 on 2007-08-21
I don't know where else to post this.  I consider the Ubuntu community well informed and fairly unbiased about their OSes.  I've seen enough posts towards people who are unwilling or unable to learn how to setup Ubuntu properly to know that there isn't a general community hatred towards windows.

I've been using Ubuntu for a little over a month now, and I love it.  I can do more things in Ubuntu than I could with windows.  Somethings didn't function right away--wireless networking, direct rendering on my graphics card--but after doing some research I've finally got all the things I deem essential up and running exactly the way I want them to (Minus dual-monitor support, but I'm working on that).  

Here's why I'm posting:  My windows partition is nagging at me everyday.  It takes up half my harddrive, and I've only logged into it 3 times this past month (and I use my computer for at least an hour everyday).  Ubuntu is faster, cleaner, and the default--why would I boot up for any reason other than functionality, right?  I really want to make the full conversion, and stop dual booting to (one day) utilize my whole hard drive.  


I have a 28gig drive:
Linux and all of my installed programs (MP3 players, movie players, WINE, Tremulous, Rosegarden+a lowlatency kernel, and much more) takes up a whole 5 gigs--leaving 7 gigs of freespace on my linux partition.   
The windows partition has Windows and Office on it--and that's it--and it takes up 10gigs--leaving only three gigs for me to play with (enough for 1 game, with the windows page file working right).

Here's my question:  Should I save half of my hard drive and try to get the few games I have working in Ubuntu, or just keep one game installed at a time and boot into windows.  You all are probably familiar with Wine's current short comings, and know that it is getting better.  Should I kill windows and just use the OS I love, or keep it--just in case?

I'll make a poll, but comments and questions are appreciated.

---

### Post by bodhi.zazen on 2007-08-21
Wipe (reformat) and re-install windows for games.

run as much as possible in Ubuntu.

If you want to know how to game in linux, start here : 

[http://gaming.gwos.org/news.php](http://gaming.gwos.org/news.php)

---

### Post by Kilz on 2007-08-21
[Here is a link to the Wine application database]("http://appdb.winehq.org/"). As soon as you can get the needed applications running on Wine you can remove windows. The database will help with that.
You can also consider paying the $15 bucks for a 3 month subscription to Cedega to run Windows games. If you want after the 3 month subscription ends you can stop paying the $5 a month. Cedega will still run the games.

---

### Post by g2g591 on 2007-08-21
I'd uninstall almost everything and shrink that partation to the size of a deck of cards, which I'm about to do

---

### Post by Het Irv on 2007-08-21
I guess this is not an option but have you considered getting a larger hard drive?

Barring that I would Shrink windows as much as possible.

---

### Post by tyggna1 on 2007-08-21
Believe me, I'd love to get a bigger drive--but I run on a thinkpad (portable) and it's older too, so upgrades don't come cheap.  I--actually, can get a new computer for cheaper than a larger hard drive.  Also, thanks for the link bodhi--it's broken, but I still found the page.

---

### Post by tyggna1 on 2007-08-21
> **g2g591 said:**
> I'd uninstall almost everything and shrink that partation to the size of a deck of cards, which I'm about to do

That's what I've done, but XP pro needs about a gig of free space to run smoothly on your drive--for much the same reason you need a swap partition in linux.   For some reason or another, I cannot uninstall office.  There's also one more complication:  I can't reinstall windows on this machine.  I have a valid key and all--it's a sticker on my machine--but it just won't take it on this computer (it will on another--I think it has something to do with factory OEM's storing part of the windows authentication key in the BIOS).

---

### Post by likemindead on 2007-08-21
I completely ditched Windoze just a few weeks ago and Ubuntu hasn't left me with any regrets. Actually, I couldn't be more pleased! Thanks everyone for all that you do in this community. :)

---

### Post by perspectoff on 2007-08-21
There's a nice thread on how to get Windows to boot from an external harddrive. It takes some minor (legal)  hacking: one makes an ISO from a Windows Installation disk, edits a few configuration files, re-archives the resulting files back into an ISO, then burns a new installation disk. 

Then you install a fresh install of Windows onto your USB drive from your hacked installation disk.

Then you can boot Windows from your USB drive whenever you want (or don't want). Recover your primary hard drive for Ubuntu. Then let the extra USB hard drive with Windows on it gather dust more and more until, like a baby's pacifier, you have outgrown it.

Oh wait; there's only one problem. Really old laptops may not have the BIOS option for booting from a USB drive. You had better check that first in your BIOs setup. If it's allowed, then you're in luck!

See:

[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)

for instructions how to get Windows to boot from a USB drive.

Note that some of the utilities mentioned in the instructions are Windows based and you have to pay for one of them (as always). However, you can do the work on Linux with free programs.

Infra-Recorder can read and write ISO files, and you can extract ISO files for editing using file-roller, the default archiving program found in the current Ubuntu (Feisty) by default.

---

### Post by perspectoff on 2007-08-21
I trust Microsoft as far as I could comfortably spit a rat

a kleptomaniac rat with code diarrhea

---

### Post by callan79 on 2007-08-22
> **bodhi.zazen said:**
> Wipe (reformat) and re-install windows for games. Run as much as possible in Ubuntu.


Howdy,

I still run dual boot, and I use my Windows installation ONLY for doing video editing, as I haven't found time to find a suitable Linux app to complete my half-finished Home DVDs.

I blew my whole HDD away, and whacked WIndows + Video Editing onto a 10GB partition, which still leaves enough room to mess around.

Cheers :)
CD

---

### Post by tyggna1 on 2007-08-22
New info:  I thought that I'd try booting into windows again, and now it won't boot up properly.  I have to restart my computer twice before it'll boot up normally--and it takes about 7 minutes.  The Ubuntu only now option is looking more appealing.

If I get dual-monitor support working in Ubuntu, I'm jumping on that like Tigger on a trampoline!

---

### Post by stchman on 2007-08-22
> **tyggna1 said:**
> I don't know where else to post this.  I consider the Ubuntu community well informed and fairly unbiased about their OSes.  I've seen enough posts towards people who are unwilling or unable to learn how to setup Ubuntu properly to know that there isn't a general community hatred towards windows.

I've been using Ubuntu for a little over a month now, and I love it.  I can do more things in Ubuntu than I could with windows.  Somethings didn't function right away--wireless networking, direct rendering on my graphics card--but after doing some research I've finally got all the things I deem essential up and running exactly the way I want them to (Minus dual-monitor support, but I'm working on that).  

Here's why I'm posting:  My windows partition is nagging at me everyday.  It takes up half my harddrive, and I've only logged into it 3 times this past month (and I use my computer for at least an hour everyday).  Ubuntu is faster, cleaner, and the default--why would I boot up for any reason other than functionality, right?  I really want to make the full conversion, and stop dual booting to (one day) utilize my whole hard drive.  


I have a 28gig drive:
Linux and all of my installed programs (MP3 players, movie players, WINE, Tremulous, Rosegarden+a lowlatency kernel, and much more) takes up a whole 5 gigs--leaving 7 gigs of freespace on my linux partition.   
The windows partition has Windows and Office on it--and that's it--and it takes up 10gigs--leaving only three gigs for me to play with (enough for 1 game, with the windows page file working right).

Here's my question:  Should I save half of my hard drive and try to get the few games I have working in Ubuntu, or just keep one game installed at a time and boot into windows.  You all are probably familiar with Wine's current short comings, and know that it is getting better.  Should I kill windows and just use the OS I love, or keep it--just in case?

I'll make a poll, but comments and questions are appreciated.

I voted to kill Windows as my laptop is Ubuntu only.

I keep Windows as a dual boot on another machine for gaming only.  I have not booted into XP in some time.

---

### Post by southernman on 2007-08-22
I voted to kill windows. I almost didn't vote because of the way you worded it and the opening comment you make in the OP:

> I don't know where else to post this. I consider the Ubuntu community well informed and fairly unbiased about their OSes. I've seen enough posts towards people who are unwilling or unable to learn how to setup Ubuntu properly to know that there isn't a general community hatred towards windows.

Still the ultimate decision is yours alone to make. I too am a fairly recent Windows convert (3-4 months) and the only app that kept me holding on to Windows was Dreamweaver. When I need to write (X)HTML now, I just use gedit or nano. 

Never being a gamer, I can't relate to all the gaming fanatics out there that (if they wanted to) can't switch to Linux merely for the gaming vendors lack of support for Linux. If only half of the people that use pirated copies of Windows would wake up (as I did.. not meaning it deragotory) and start using a TRULY free OS, then the Linux market share would be such that Gaming programmers would soon be called on the carpet by the CEOs and demand them to start porting games to Linux. IMHO at least. YMMV

In the end, it's your call.

---

### Post by tyggna1 on 2007-08-28
trying a bump, please leave feedback.

---

### Post by astralsin on 2007-08-28
well, if windows is giving you that many problems i say ditch it.  i converted to *nix a little over 5 years ago and I'm a gamer.  I play mostly Q3A, UT2k4, and Alien Arena all of which run natively on linux.  i've had very good luck with cedega and moderate luck with wine (though wine is very spotty for me).  in many cases, its necessary to install a game on windows then you can copy the game's directory over to linux and run with wine, in which case you can install windows on a virtual machine (if your laptop is capable, if its old it may not like it) and copy it from there.  i assume if you're running 3d games, its not that old.  it really all comes down to what games you want to run.  list some here and some of us may be able to help you more.  as it is, its kinda hard to tell you whether to make the full switch or keep windows around.

---

### Post by notwen on 2007-08-28
Personally depending on how often you actually play your windows based games and do you tend to grow bored and hop back and forth from game to game before finishing?  I would recommend dual-booting and maybe giving yourself enough room for 2 or more games, that way should you get bored of the currently installed game you could always install and play the 2nd.  Or break down and get a console gaming system. =p

---

### Post by tyggna1 on 2007-08-28
> **astralsin said:**
>  i assume if you're running 3d games, its not that old.

Bad assumption with Ubuntu :D.  It *is* old, dating back to around 2000--my car is newer than my computer.  I will give the virtual machine a test--but I'm gonna leave windows on my wife's machine (even though she prefers Ubuntu) for the install folders/registry stuff that I need.  I have a 2Gig thumb drive that will let me transfer with that just fine.

---

### Post by weblordpepe on 2007-08-28
> **tyggna1 said:**
> I don't know where else to post this.  I consider the Ubuntu community well informed and fairly unbiased about their OSes. I guess that was mistake #1 :P
You should expect people on this forum to be cheering for Ubuntu all the way. I would suggest anther site, but from what I can tell its pretty difficult to find a non-bias group of people on any website, or in any place in the real world.

Secondly I'd say it comes down to what you had initially. People usually say to me 'why not use Windows?' And thats valid from their perspective. Its difficult to argue away an OS that works for someone.

What I usually do is change the question to 'Why not use Linux'? as it makes Linux the default unless arguments & facts dictate otherwise. I.e. puts Windows on the defensive.

---

