---
title: "[Solved - sorta] broken pipe error at boot of 12.04LTS (after HW upgrade)"
date: 2014-08-10
forum: General Help
---

### Post by WB0HYQ on 2014-08-10
For several weeks after the upgrade to the new HW stack, I ran just fine with my unity-2d desktop (except by best resolution was a stinking 1024x768).  Today, when I booted up, I got a tty login screen isntead of my desktop.  When I hit Ctrl-Alt-F7, I got "cannot write bytes broken pipe".

I have seen what apprears to be hundreds of  posts in this forum with that in the title and I've tried every solution offered in them to no avail.  I simply cannot get a graphical desktop started due to this error.

My disk is not full, as df -l and df -i show (my main drive is 3% full).

I've tried to add the yannubuntu 'boot-repair' repository (which seemed to work) but entering 'boot-repair' fails with the following message:

(gksudo:2509): Gtk-warning **: cannot open display

This seems to reinforce what I've seen in other threads that it has to do with my graphical card (an NVIDIA GeForce card) but I haven't had any luck with this command:

sudo apt-get install nvidia-current-updates  (after sudo update and sudo apt-get purge nvidia-*)

The above command give me the error that it cannot find some sort of NVIDIA log file and refuses to do anything more.

So, I guess my system is probably messed up enough now so that re-installation is the best bet?  I really hate to do that as I have invested a lot of work fine-tuning it the way I want it and now I really don't want to start all over.  WOuld it be best to just forget 12.04 and the new HW stack and jump directly to 14.04 LTS and be done with it?

Bill

---

### Post by WB0HYQ on 2014-08-10
I've messed with the stupid computer now for the last three hours and am no closer to fixing it than I was at the original bootup.  What is totally strange to me is that I can use desktop connection INTO it from my WIn7 machine and GET an actual desktop GUI.  If I can do that, why can't I do it from the actual video display attached to the stupid computer?  Riddle me that.

The last thing I tried was this:

sudo apt-get install ubuntu-desktop  && sudo apt-get install -f
sudo reboot

This produced no discernable change at all.

So far, 93 individuals have read this thread.  To me, that means the thread title was enough of a grabber for them to wonder what it was about.  Hard to believe that out of 93 people there isn't at least 1 who can give me the slightest advice.

EDIT: It's bedtime here on the east coast.  Back again tomorrow for round 2.

Bill

---

### Post by NM5TF on 2014-08-11
you might try this...seems to have worked for others....YMMV

[CODE]
sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvida-current-updates
sudo rm .Xauthority
/CODE]

tommy

---

### Post by WB0HYQ on 2014-08-11
@nm5tf:  I mentioned those commands in my first post.  I hadn't tried to remove .Xauthority though and will do so and report back.

Bill

---

### Post by NM5TF on 2014-08-11
do you know what driver version you are running for your nvidia card ??

if not, use this to find out...

```
nvidia-smi -q | grep "Driver Version" | awk '{print $4}'
```

tommy

---

### Post by WB0HYQ on 2014-08-11
Here is an update:

1) tried to issue the command to find out what my video card was and the prompt just returned without any information at all.

2) loaded up the DVD with 14.04LTS on it and tried "update 12.04 to 14.04 upgrade" which failed miserably.  When it got to the 'reinstall of existing software" every one of them failed with "you are holding broken software" EVERY one of them including all the libraries gave me this error.  When I finally got to reboot, I had no mouse and the screen was set of 800x600, which is terrible.  Keyboard worked, but barely.  I could hit a key and TWO MINUTES later, the keystroke would show up in a white box at the bottom-right of the screen.  This was totally unacceptable, so I moved onwards to the next step.

3) Used the same DVD and REPLACED the old 14.04 with a completely new copy of 14.04.  This appeared to work, but now I am offered only 1024x768 and 800x600 as resolutions.  WHile running on the DVD, I was at a might better resolution which begs a question: Why can the installer give me a better resolution than the final installation?

I am now letting the machine download and installl 270Mb of updates.  Luckily, I have a fairly fast Internet connection - without it, this would be very painful.

The video card is an NVIDIA GeForce 7600GS with a half-gig of RAM.  The computer itself is a pretty old one, with only 700Mb of RAM and a slow processor.  I can live with the slowness as it is only used when I am in the basement fiddling with my routers and servers.  The resolution, under WIndows XP, was 1440x800 so I don't understand why Ubuntu can't at least match that.

Bill

---

### Post by NM5TF on 2014-08-11
Bill...

it almost certainly is a video card driver issue...

my card is a 6150se and uses the 304.117 driver...I can get the full resolution
of my monitor 1440 x 900 using this driver

here is a page from nvidia that has a driver for your card that should fix your issue

go here:

[http://www.geforce.com/drivers/results/72477](http://www.geforce.com/drivers/results/72477)

73 de Tom NM5TF

---

### Post by Bashing-om on 2014-08-11
WB0HYQ; Hello.

See NM5TF's last, I agree it is apt.
However, more to the point, you just do not have the horse power to run the high end edition 'ubuntu'. 
> 
The video card is an NVIDIA GeForce 7600GS with a half-gig of RAM. The computer itself is a pretty old one, with only 700Mb of RAM and a slow processor. I can live with the slowness as it is only used when I am in the basement fiddling with my routers and servers. The resolution, under WIndows XP, was 1440x800 so I don't understand why Ubuntu can't at least match that.

See:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
For clarification.

May I suggest ya try Lubuntu, as it is specifically designed to run on older hardware - lubuntu impresses me greatly.

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

### Post by WB0HYQ on 2014-08-11
@NM5TF: I have managed to completely fix the issue.  See below for the details...

@Bashing-om:  Au contraire, my computer isn't THAT old.  When I bit the bullet and completely overwrote (after saving what I wanted of my data files) 12.04 with a fresh install of 14.07 right from the DVD as in my previous post, option 2, I then went to the System page and then to "Additional Drivers" and switched to an NVIDIA 304.117 (which worked instead of crashing).  Then I went to the Display and found I had a few more resolution options, one of which was a 16:9 that is now running my display.  I can reboot and the computer comes up quite fast.  The last two or three hours have been spent replacing/reinstalling what software I had before under the old OS.

I don't know if I should mark this as Solved because the solution was pretty drastic.  For someone who has this problem, and hundreds of applications, I don't recommend my solution.  Much appreciation for everyone's help here.

Bill

---

### Post by Bashing-om on 2014-08-11
WB0HYQ; Great !

Way to go .

[INDENT][INDENT]when you are good
[INDENT][INDENT][INDENT][INDENT]you are good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by WB0HYQ on 2014-08-11
As my sig says, I've been in computers a long time.  I manage to squeeze every erg of juice out of them before they melt down. I dug into my parts bin and came up with a bit more RAM.  The computer H/W now is:

MEM: 2G
CPU: AMD Athlon XP 2800+
Video: GeForce 7600GS/AGP/SSE/3DNOW!
Disk: 115.9G (free)

I expect it will have a long life after I cleaned out a dust bunny the size of Cleveland at the bottom of the case.

Bill

---

### Post by Bashing-om on 2014-08-11
WB0HYQ; Yeah !

Like you I run an old AMD box and I fully expect to run this 14.04 installed box to at least 2019.
- I like my system, just as I have it -


[INDENT][INDENT]when it breaks
[INDENT][INDENT][INDENT][INDENT]fix it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by NM5TF on 2014-08-12
that's great news Bill :cool:

and that extra bit of RAM will go a long way to make it run like it should.\\:D/

enjoy your adventures in Linux....I certainly have =d>

tommy

---

