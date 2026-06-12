---
title: "Power management problems"
date: 2007-04-22
forum: General Help
---

### Post by jtcedinburgh on 2007-04-22
Hi everyone.

I have a Shuttle XPC with Athlon XP cpu.  I want to use it as a music server, running Slimserver software.  I would like it to sleep after a certain period of inactivity, and wake on a lan request or a mouse movement.

I have set it to sleep after 15 minutes of inactivity.  However, it is sleeping regardless of whether it is actually doing something.  For instance, I am transferring several Gb of files from another machine, which to me is 'activity' but still the power management kicks in and the machine goes to sleep.  Likewise, running the Slimserver (serving network requests to other devices), it still has sleep kick in.  Most annoying!

**How do I prevent it going to sleep unless *truly* idle?**

Secondly, though it is set to wake on lan properly, it never does - neither does it wake on a mouse movement.  These are enabled in BIOS, and worked perfectly when the machine had Windows XP installed on it.  Nothing has changed in the BIOS, so I am assuming it is a 'deeper' configuration than simply setting things using ethtool.  The only thing which brings this machine out of sleep is pressing its power button.  It resumes quite happily when I do this, but it's hardly ideal as I intend to be in another room, using the Squeezebox device for accessing my music.

**Can anyone help me find out how to get it to wake from sleep?**

Many thanks,

John

---

### Post by baldmosher on 2007-04-23
Not an answer, but an expansion on the problem via a similar issue.

I also found a bit of related info [here](http://ubuntuforums.org/showthread.php?p=2047919#post2047919) about being **environmentally friendly**.


I've a P3-733 that I use for a home network fileserver, serving my XP-based Athlon XP 2000 PC in the office (Winamp) and my Xbox in the living room for Divx.

The server is eventually going to be used to host Sancho (when I eventually get round to install and config) for filesharing, but for now I like to switch off the box overnight to save power.

Thankfully, my PSU boots the machine automatically after a power cut, so I have set up a simple mains timer to turn it off at 1am and back on again at about 5pm (I'm at work during the day, except weekends when I don't mind manually switching on the machine if required).


What I'm wondering is: when I install Sancho, is there any way of setting up an automatic power down (or suspend) when idle, and power up on request from the LAN?

I suspect that if John has had similar problems I might struggle to achieve this. I also appeared to be having a similar issue when PM was done in the BIOS because Ubuntu would enter a coma if I left it alone for an hour. It would still be working as a server in the background but would refuse to wake up. Not a clue why this would happen but disabling the 3D screensaver and disabling PM seems to have fixed this. I had assumed it was incompatibility with Ubuntu and the BIOS PM.

---

### Post by jtcedinburgh on 2007-04-23
Well, I'd hate to have to go back to the world of Microsoft but at least I do know that this worked fine with XP.  I'd really like to be free of the rest of the hassles of MS world, and to give support to Ubuntu, but as a beginner I am finding it a bit perplexing and I would appreciate any help anyone can give.

Thanks,

John

---

### Post by baldmosher on 2007-04-24
Well John, the simple answer is to turn off your PM support in the BIOS as I have done! Although if you're not pirating your electricity supply like I am, that might cost you a bit.

---

### Post by jtcedinburgh on 2007-04-24
Hmmmm... but that's the very point - I want to be eco friendly, green, save a few bob on the bills, etc.

Please don't make me go back to the woeful world of Windoze... :(

---

### Post by jtcedinburgh on 2007-04-24
Ah, sod it.  Hate to say it, but I don't think Ubuntu is ready for me (or I for it).  At least where my Shuttle PC is concerned.  So I sit here re-installing Windoze... :(

---

### Post by ashz on 2007-04-24
I'm sorry that no one was able to help you with your problem, and your right I don't think Ubuntu is ready for 100% of people at the moment (mainly because it is still in development).

Yours is a unique(ish) problem, but you have to go with whats right for you.

You want a certain feature that Ubuntu evidently does not supply.  I'm just sorry that to get that feature you have to go back to the bloatware, viruses, spyware etc etc etc.

My question to you is have you tried any other distros? Suse, Mandriva, Fedora, PCLinuxOS etc etc just because Ubuntu did not work wont mean they wont, unless of course its a BIOS problem in which case none of them will including XP!!

Cheers and hope to see you back soon (When you see the light :P)
Ash

---

### Post by StewD on 2007-04-24
Hi John

I'm struggling with the same problem, and noticed you made reference to "ethtool". I've had a look at the MAN pages, and have to admit to not really understanding much of the resulting text! I'm guessing I need something from here:

```
wol p|u|m|b|a|g|s|d...
              Set  Wake-on-LAN  options.   Not  all devices support this.  The
              argument to this option is a  string  of  characters  specifying
              which options to enable.
              p  Wake on phy activity
              u  Wake on unicast messages
              m  Wake on multicast messages
              b  Wake on broadcast messages
              a  Wake on ARP
              g  Wake on MagicPacket(tm)
              s  Enable SecureOn(tm) password for MagicPacket(tm)
              d  Disable  (wake  on nothing).  This option clears all previous
                 options.

```

But which of these? Is there any way of seeing what is currently switched on?

Any hints before I break everything?

Cheers,

Stew

---

