---
title: "wholly bad experience with ubuntu so far.."
date: 2006-12-28
forum: General Help
---

### Post by eitan_a on 2006-12-28
I wish I could say this linux experience is working out like I'd like... (and they wonder why more people don't use linux, but that's another thread..)

I've had various issues with ubuntu on a new sony vaio laptop.  I spent the whole day trying to fix the touchpad (to make it have vertical scroll) and while it workes after I log out and log back in, if I do a restart my settings aren't saved so I have to do it again.  This is very annoying!

Next, I started having a problem with my audio today.  My system plays audio through its internal speakers regardless of whether i have my headphones in the jack or not.  This is annoying since if I'm listening through my headphones, I want my computer silent.

Also, I spent most of today trying to get ubuntu to be able to change the brightness of my LCD screen, but haven't been successful.  I've done everything that was suggested online on the topic.  

When using the wireless connection, it is very much slower than in winxp.

Finally, my internal SD card reader doesn't work in ubuntu.

I just want to say that everything here works in WinXP.  I'm dissapointed so far with linux.  I wasn't expecting something with this many simple problems.  I do, however, want to fix this and learn more about linux.  I need it for my profession for the coding ease. 

I hope this message doesn't get lost in this forum.  I'm really able to learn, I just don't know where to begin with this.  I also would love to troubleshoot the problems i'm having with ubuntu.

Thanks!

---

### Post by majoridiot on 2006-12-28
what release did you install?  i had NIGHTMARES with edgy (6.10) from a clean install and
finally gave up and installed dapper (6.06) after too many hours fighting things that had been
changed/moved/broken.  from my experience (and on my boxes) dapper is solid as a rock.

if you installed edgy, i sincerely recommend wiping that HD and installing dapper from 
SCRATCH. 

regardless, it would probably be wise to make a list of your problems in order of importance
and then working through them one by one in the appropriate forum- i.e. general, multimedia
etc.

---

### Post by eitan_a on 2006-12-28
I installed 6.10...I will go for 6.06 if that's what it takes to fix these things, but I'd like to try here first.

The list of things...

1. Sound is played from internal speakers regardless of whether my headphone is in the jack.
2. Internal SD card unresponsive
3. Very slow wireless (compared to winxp).
4. Touchpad settings aren't saved after reboot.

I have asked in other forums but the post got lost in the jumble.

---

### Post by adriantry on 2006-12-28
Hi Eitan

> **eitan_a said:**
> they wonder why more people don't use linux

Your complaints are not necessarily about Linux, but about Ubuntu in particular. I love Ubuntu. It has excellent hardware recognition, and a great philosophy, but may also requires a lot of post-install configuration (depending on your hardware). There are other distros that are designed for people who don't want to do a lot of post-install configuration.

To be fair, though, last time I installed Ubuntu on my Sony Vaio (that was Dapper Drake 6.06), most of the things you mentioned all worked automatically.

And there are Linux distros much harder to configure than Ubuntu.

> **eitan_a said:**
> I've had various issues with ubuntu on a new sony vaio laptop. . . touchpad (to make it have vertical scroll) . . . audio . . . LCD screen . . . wireless connection . . . SD card reader.

If you're having a lot of trouble getting these working, you might like to try another distro like PCLinuxOS or Freespire or Simply Mepis. These distros tend to have less post-install configuring. In fact, on the partition that I do most of my work, I'm using PCLinuxOS. I go to that partition when I want to be productive without having to do much fiddling.

> **eitan_a said:**
> I just want to say that everything here works in WinXP.  I'm dissapointed so far with linux.

As you'll probably be told quite a few more times in this thread, that's simply not true. Sony spent hundreds (thousands?) of hours customising Windows - writing and pre-installing device drivers, codecs and software for a start - to get everything working when you bought the computer. And Sony probably didn't even give you a "restore" CD to put the computer back in its original state if things go wrong. They make you burn your own these days so that they save a few cents.

I spend a lot of time helping people with laptops and desktops which went bad, and very few of them created that restore CD. I can tell you that it is no fun trying to track down and install all of the drivers to get their computers working again. It certainly doesn't work like you're saying after an initial Windows XP install. And it certainly isn't within the capability of the average computer users I am helping. It takes many hours of frustration!

> **eitan_a said:**
> I wasn't expecting something with this many simple problems.  I do, however, want to fix this and learn more about linux.  I need it for my profession for the coding ease.

I love Ubuntu. One of my initial reasons for choosing Ubuntu is that I felt that I would learn more about Linux using Ubuntu than the distros I mentioned earlier in this post.

If you're serious about learning more about Linux (and you should be if your profession depends on it), then you should stick with Ubuntu, and learn how to solve all of the problems you're encountering. (And it sounds like some of the problems are self-inflicted!) Once you've learnt how to solve them, you'll be surprised how easy it is the second time. And you'll be able to help people with the same problems here on this forum the second time.

Stick with it, Eitan!

Adrian

---

### Post by Shay Stephens on 2006-12-28
Historically, I have never had a good experience with linux.  But last year I became motivated by all the news about vista.  So I took a new approach.  This time I was going to learn how to use it slowly.  It was going to be a long term project to gradually migrate from using windows to using linux.  In order to achieve that I relied on dual booting with windows and linux.  As of a couple of weeks ago I finally reached my goal and I am now using ubuntu 100%.

But it wasn't easy, and it wasn't fast, but it did pay off in the end.  So my suggestion is to take a long term approach and go slow.  Dual boot until you don't need to any more.  And replace hardware that is not compatible with linux compatible hardware.  It makes all the difference in the world.

---

### Post by Shay Stephens on 2006-12-28
Oh, and let me add something I learned about slow internet.  By default, IPv6 is on.  If you don't have IPv6 hardware to support that (like me) then you are going to have a slower experience.  You need to turn off IPv6 until such time as it is fully supported.  Here is what I do:

 1. In the terminal copy and past this and press enter to run it.

```
gksudo gedit /etc/modprobe.d/aliases
```

2. Find the line: alias net-pf-10 ipv6
3. Replace it with: alias net-pf-10 off ipv6
4. Save the file and close the window

5. In the terminal copy and past this and press enter to run it.

```
gksudo gedit /etc/hosts
```

6. Comment out the ipv6 lines like this (add an asterisk before the line)
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

Save the file and close the window. The next time you reboot, the changes should take effect and browsing should be snappier.

---

### Post by aysiu on 2006-12-29
This is a support thread started by eitan_a.

It appeared to have been hijacked into being a "complain about Linux" discussion thread, so I've moved the irrelevant (to support) posts to [this thread](http://ubuntuforums.org/showthread.php?p=1941773#post1941773). Please continue your discussion there, and let this remain a support thread. Thanks.

---

### Post by eitan_a on 2006-12-29
Thanks guys for the support =) I'm gonna stick it out for the long run.  I think the main problem of mine is that it was very overwhelming at first.  Now that I know some commands and what sudo is (hehe) it's feeling a bit better.  

The status on my problems..

1. Sound is played from internal speakers regardless of whether my headphone is in the jack.
-Solved!  Downloaded a gnome audio mixer and was able to mute the internal speakers while keeping the PCM at a different volume.  It's not automatic (the internal speakers are muted while the box is checked) but I'm sure there's a script that can be written to turn it on/off without going into the program.  But so far, very happy since I need music to work and use my headphones all the time.  Program was called Gnome ALSA mixer.

2. Internal SD card unresponsive
-Haven't tried anything lately, going for suggestions.  The reader is listed in my hardware, I'm sure it's a configuration thing I need to do change so I'm open to help on this topic.

3. Very slow wireless (compared to winxp).
-Haven't tested lately...will post back.

4. Touchpad settings go into effect after log-in from a log-out and not from a reboot.
This one is wierd to me, maybe someone can help me take apart xorg.conf?  My touchpad settings go into effect ONLY after I log-in from a log-out, but NOT after a reboot.  Any help here?

Thanks a lot guys.

---

### Post by WiseElben on 2006-12-29
For your slow wireless problem, you can try disabling ipv6. I know Shay Stephens told you how to do it, but a quicker way (if you're using Firefox) would to be to type in "about:config" (w/o quotes) in the address bar, filter "ipv", and then make the value true. This will disable ipv6, something that many servers still do not use (they are using ipv4, I think).

---

### Post by eitan_a on 2006-12-29
Quick update...

3. Wireless internet, SOLVED!  I disabled iv6 how both of you suggested.  I also installed kwifimanager and wifi-radar to manage the wireless connections along with my wired one.  I also reset my wireless router on my desktop.  I can now say that wireless is as fast as it is on WinXP, so I'm happy about this.

Things I'd want to get fixed..

1.  SD internal reader still unresponsive.  Would love to get help on this.

2.  Touchpad settings don't get loaded unless I log-out and log back in.  I have an entry in my sessions->start-up programs that says..

gsynaptics-init --sm-disable

Could this be the problem?  I'm using gsynaptics to manage my touchpad settings.

3.  Not so important, but I installed compiz and am liking the desktop.  One thing though..the menu opening/closing doesn't show unless "fade" button is checked in "Windows" tab.

Thanks again guys!

---

### Post by eitan_a on 2006-12-31
Ok, so here's an update.  I got my SD card reader to work, so I was very happy about that and the help from this forum in solving the problem.  

I still have an annoying bug where my touchpad settings aren't loaded after a reboot, but ARE loaded when I log out and log back in.  Im about as stumped as this guy..:confused: .  I think it could be some sort of conflict of settings between the PS/2 and touchpad that are loaded in xorg.conf.  Any help is much appreciated.  This is the last bug I want solved.

Thanks!

---

### Post by bulldog on 2006-12-31
Did you try to reconfigure Xserever?
```
sudo dpkg-reconfigure -phigh  xserver-xorg 
```

---

### Post by eitan_a on 2006-12-31
I haven't...will do now.  Thanks for the tip!

---

### Post by eitan_a on 2007-01-01
Well that didn't change anything.  After I reboot, X uses my PS/2 settings for my touchpad.  Then after I log out, log back in, my synaptics touchpad settings are used.  It seems like somewhere in the boot up process, there is a problem of recognizing what I have, a PS/2 mouse or a touchpad.  I've also noticed after I do a cat /proc/bus/input/devices that the event number changes for my ALPS touchpad.

I would like to know if there's a way to emulate a scrollwheel on the PS/2 mouse driver, since I just want to vertical scroll.  Or, if there's a way to force the synaptics driver to load for my "mouse."

---

