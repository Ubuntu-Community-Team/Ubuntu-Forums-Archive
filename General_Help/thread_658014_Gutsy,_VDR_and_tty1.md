---
title: "Gutsy, VDR and tty1"
date: 2008-01-04
forum: General Help
---

### Post by zupidupi on 2008-01-04
Hi folks,

I recently upgraded my DVR (Digital Video Recorder) from Edgy to Gutsy.The system runs in command line mode, the GUI is disabled. I use my telly for watching the recordings, and (on another channel) for doing maintenance (in command line mode).

VDR needs a tty-slot for receiving commands. In my Edgy-installation I achieved this by fiddling with the /etc/inittab-file. I commented out the following line

#1:2345:respawn:/sbin/getty 38400 tty1

and started VDR with the command

VDRCMD="$VDRPRG **-t /dev/tty1** -w 60 -u zup --config=/home/media/System/VDR/etc --lib=/home/media/System/VDR/lib -Pdvdswitch -Pextrecmenu -Pmp3 -Pmplayer -Pdvd -Psubtitles $*"

This was fine, VDR communicated through tty1 by sending messages and receiving kestrokes. I then used tty[2-6] for the maintenance.

Now, I've realized that Gutsy has shuffled the deck a bit. After some research I tried the following.

First I poked around in /etc/default/console-setup . The original and new lines are as follows

#ACTIVE_CONSOLES="/dev/tty[1-6]"
ACTIVE_CONSOLES="/dev/tty[2-6]"

Then I did some messing around in /etc/event.d I renamed files according to the following file listing:

control-alt-delete  rc0  rc2  rc4  rc6         rcS          sulogin  tty3  tty5  **tty_ett**
logd                rc1  rc3  rc5  rc-default  rcS-sulogin  tty2     tty4  tty6

Note that I renamed tty1. To be on the safe side, I commented out all the contents in the file:

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

#start on runlevel 2
#start on runlevel 3
#start on runlevel 4
#start on runlevel 5

#stop on runlevel 0
#stop on runlevel 1
#stop on runlevel 6

#respawn
#exec /sbin/getty 38400 tty1

I then start up VDR with a command identical to the above:

VDRCMD="$VDRPRG **-t /dev/tty1** -w 60 -u zup --config=/home/media/System/VDR/etc --lib=/home/media/System/VDR/lib -Pdvdswitch -Pextrecmenu -Pmp3 -Pmplayer -Pdvd -Psubtitles $*"

The arrangement almost works. When I boot up tty1 is disabled, and I get a login prompt only at tty2-tty6. The keyboard works, that's for sure, I can switch between tty2-tty6. The problem is that VDR doesn't communicate with tty1 at all - no output, no input. I really don't know where VDR writes its messages, or from where it tries to read keystrokes.

So, this is where I call for help! Any hints will be much appreciated. Hopefully I've been clear enough in stating my problem.

Best regards,

   Mike

---

