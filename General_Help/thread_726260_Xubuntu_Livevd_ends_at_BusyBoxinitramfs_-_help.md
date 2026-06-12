---
title: "Xubuntu Livevd ends at BusyBox/initramfs - help"
date: 2008-03-16
forum: General Help
---

### Post by cmbcne on 2008-03-16
Starting new thread 'cause similar threads don't apply.  The BusyBox/initramfs situations seems to be appearing a lot.  It also seems to affect users of 7.x versions of ?ubuntu and not earlier ones.  I'm posting my observations in case someone much more experienced than I can pick up a clue as to what's happening.

I am NOT trying to install -- I just want to run Xubuntu 7.10 as a "live-CD".  My system is a PC clone box with an Intel SR440BX mobo, PIII 550 MHz with 512 MB RAM.  Two hard drives:
Primary master runs Windows 2000 Pro
Primary slave runs Kubuntu 7.10

I have tried changing things at the initial splash screen to:
*   pick screen resolution of 1024x768x24  (In Kubuntu, I'm running higher than that - 1440x900x24)
*   Just accept the default settings
*   Pick safe screen mode
*   Edit Other Options line to start with "break=top"  (from another post)

In each case the load proceeds to the point where it shows the BusyBox/initramfs screen.  I've typed exit twice in a row (as suggested in another post).  I've typed "return" twice in a row (in the same post).  I've done Ctl-Alt-Backspace twice in a row (a different post).  Nada, bupkiss, rien-de-tout, nothing.:(

Ctl-Alt-F1 shows:
loading, please wait
cp: unable to open /root/var/log: no such file or diretory
mount: mounting /root/dev on /dev/.static/dev : no such file or directory
mount: mounting /sys on /root/sys : no such file or directory
mount: mounting /proc on /root/proc : no such file or directory
Target filesystem doesn't have /sbin/init      (repeated five times)

I've booted into Kubuntu and tried to view the Xubuntu CD and it reports it's a blank CD -- could that be part of the problem?  I mean, it's obviously NOT blank if it starts to boot, but could it be that the burn screwed up part of it?  My own guess is "no" based on the number of others with the same problem.

OK: what do I do now? :confused:

---

### Post by cmbcne on 2008-03-16
Follow-up to my original post.

Further thoughts...
I just downloaded a new copy of the ISO.  When I went to burn it, I noticed that my burner (CDBurnerXP) was set to burn at 24x and Track-At-Once.  I changed it to 8x and Disk-At-Once.  Lo and behold, this CD works.  It boots into the live cd desktop consistently (three times in a row).  The old CD was, as I say, burned faster and TAO rather than DAO.  I don't know why that makes a difference though.

Another further thought...
The first CD was from an ISO that I got using a torrent.  The second one I used HTTP from the Xubuntu web site link.   Is it possible that my problem and that of many other people may be caused by corrupted files being distributed over torrent networks?  Or could the torrent method be doing the corruption?

Just thinking out loud and putting the question to the community.

---

### Post by cmbcne on 2008-03-16
As an aside to my original post:  I'm a new forum user and I just noticed my post says "Beans 2", "Thanks 0", and "First Cup of Ubuntu"

Where can I read more about that?

---

