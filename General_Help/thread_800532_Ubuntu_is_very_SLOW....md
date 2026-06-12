---
title: "Ubuntu is very SLOW..."
date: 2008-05-19
forum: General Help
---

### Post by Benihanna124 on 2008-05-19
Hi all!   My first post here and Hardy is the first version of Ubuntu I have ever used.   I have searched thru stickies and countless other forums, but dont know what is happening with my Ubuntu.

Comp Specs:
E6400 C2D @ 2.56GHz (well cooled)
2x 2gig Gskill DDR2 800
Gigabyte P965-DS3
ATI brand X1800XT 256mb

I dual boot 32bit XP and Ubuntu 8.04.

I get my internet through a Belkin G+ MIMO USB antenna.
In XP, internet is blazing fast, downloads come in between 50kb/s and 700kb/s.   I can have engineering drawing programs, itunes, and other programs running and never experience any waiting or lag i guess you could call it.   

My problem is this... in Ubuntu I open up a few applications and when I run Firefox(3 beta 5) it all goes to hell.   Long loads to open new windows, downloads rarely go over 15kb/s, and everything runs like molasses.   My friend believes its a driver problem for the Belkin wireless antenna but I am not sure.   What do you all think?

---

### Post by kbuel on 2008-05-19
Well one easy thing you can do to see if anything is taking up a lot of your CPU is to run the command 'top' in the terminal.

You can see if any application is pegging the processor and so on.

---

### Post by Benihanna124 on 2008-05-20
I ran the command and have watched firefox take up as much as 44% of my CPU and one of the roots was 22%.  Never more than say 3% of memory was spent on FF.  Is there a setting in Ubuntu that limits the use of the processor to a minimum or something like that?   This is kinda frustrating... I love ubuntu, but I have a hard time using it when Windows is out performing it greatly.

---

### Post by Benihanna124 on 2008-05-20
This might be something too...
My processor is dual core stock @ 2.13GHz
Im running it at 2.56 and when I added the CPU frequency scaling icon to the panel its only displaying 600MHz.

---

### Post by Benihanna124 on 2008-05-20
Still havnt figured it out :(

---

### Post by sugarfresh on 2008-05-20
whats your cpu speed displayed at in your bios, have u disabled c1e and t1 or t2, i thk there's another process that is used by intel that cuts clocks or something, i have a q6600 and when i first got it it was showing 1.6mhz and figured out it was some power saving features, disabled them and oc'd to 3.0 24/7, but check your bios

---

### Post by Benihanna124 on 2008-05-20
it says 2560MHz, and I checked that feature in my bios and its disabled.

---

### Post by wpshooter on 2008-05-20
The first thing I would try is to scrap Hardy for the moment and then download and trying installing Gutsy in place of Hardy and see it you get the same bad results that you have mentioned above.

P. S. - My guess is that you won't.

Good luck.

---

### Post by Benihanna124 on 2008-05-21
no, im not giving up on hardy yet... i really believe this is fixable, i just dont know how yet

---

### Post by Benihanna124 on 2008-05-21
UPDATE:
     Ok, heres what I have figured out so far...   The CPU frequency monitor is set to run my proc at 75% of its full speed.   I have tried to change it to 100%, but do not have the option to change it.   I turned my overclock off and went back to my stock speed and now have 1.60GHz displayed (which is 75% of my stock 2.13GHz).   So thats getting somewhere.   When I overclock to 2.56GHz, it displays my 100% speed as 800MHz and only uses 75% which is 600MHz.

---

### Post by perillux on 2008-05-21
Firefox 3 Beta 5 (the one that comes with hardy) has some resource management issues for some people.  I had it a little but not nearly as bad as you, for me it would just freeze for a few seconds periodically.

It fixed it for me when I went to Edit (on the firefox menu) > preferences > Security tab   uncheck the "Tell me if ...."  boxes.  That fixed my problem.  If you still have issues after that, you can install Firefox 3 Beta 4 or a previous version.
Look here to install beta 4:
[http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/](http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/)

I did that originally, but it kept reverting back to firefox 3 beta **5** somehow.  I'm not sure how to prevent it from doing this, but here is a guess as to how you can do it:
go back to edit > preferences > advanced, under that click the "update" tab and try unchecking some things.  Set it to "ask me what I want to do" when updates are found.

Good luck

---

### Post by sugarfresh on 2008-05-21
hmmmm. i'm brand new to ubuntu only played with it for about an hr or 2, but maybe ubuntu has a hardware problem for some reason with your config, or just with oc'ing period, i never did check to see if my cpu was clocked really low, but i have a quad so i mite not notice until i run something big like a game, i only had 3 apps, 2 browser's and a download window, open at one time. just an idea

---

