---
title: "Trouble restarting"
date: 2014-11-04
forum: General Help
---

### Post by Penfold1971 on 2014-11-04
I had posted a longer version of this in September, got a reply, but then got bogged down, being very non-tech in these matters:
 > I have a machine that I have been running headless for two and a half years. Recently I upgraded it from Ubuntu 12.04.4 to version 14.04.1.
I normally shut it down remotely from my Intel iMac, with the Terminal command 'sudo shutdown -h now', when it requires a restart after certain updates. I then go and physically power the machine on again. This all worked well until version 14.04.1. What happens now is that I can't communicate with it remotely after carrying out those steps. the remote machine isn't recognised.
Upon re-connecting the monitor, kb and mouse and powering back on, I get a screen offering me choices as to what to restart into, with Ubuntu being at the top of the list.

Is there a way I can make the machine boot into Ubuntu by default so as to not have the process hang waiting for me to go and physically choose a boot option?

I was directed to a [page on askubuntu]("http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry") which suggested using the command 'gksudo gedit /etc/default/grub'.

I can't decide what to do with the result which is as follows :

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

There are brief notes which explain what the various bits of this result do, but I'm not confident about interpreting them.

I just want the machine to boot up automatically into Ubuntu. Can someone please explain, in simple terms, what I might do to achieve this?

---

### Post by QIII on 2014-11-04
Hello!

What boot choices are being offered?

---

### Post by grahammechanical on 2014-11-04
Is Ubuntu the only OS? When that is the case the Grub boot loader will not even show a boot menu and it will load Ubuntu automatically after a delay of 10 seconds. By editing that file we can reduce GRUB_TIMEOUT=10 to 2. I would not advise going lower. Reducing the timeout to zero will make it very difficult to get a Grub boot menu when you need to enter recovery mode or a previous kernel.

But the thought enters my head. Are you seeing the Grub Boot menu? Upgrading from 12.04 to 14.04 should not change the default grub text file. In fact it is more likely to replace an edited file with a default file. Ubuntu should still be loading automatically. You say it is not loading automatically and that makes me wonder if it is some other menu that you are seeing.

Perhaps you could post the contents of /etc/default/grub so that we can see if it is still in the default state or has been modified. The only thing that I know of that will stop Grub automatically loading an OS is if a key has been pressed. That stops the delay count down. But that is not happening, either. So, I really do not know what is going on.

Regards.

EDIT: After a little bit of research there is this from the Grub manual

> ‘GRUB_TIMEOUT’
Boot the default entry this many seconds after the menu is displayed, unless
a key is pressed. The default is ‘5’. Set to ‘0’ to boot immediately without
displaying the menu, or to ‘-1’ to wait indefinitely.


Have you changed GRUB_TIMEOUT= to a negative value. That would stop Grub loading Ubuntu until a selection was made and the Enter key was pressed.

---

### Post by Penfold1971 on 2014-11-05
Thank you, both, for replying.

Today, for some inexplicable reason, I can't replicate the problem! I'm happy at that and shall be disconnecting the monitor, kb & mouse when the current work unit (Folding@Home project) is finished.

HOWEVER …

I remain unconvinced that all is well, due to lack of knowledge about what exactly happened to cause this strange problem. I'm suspicious that it will recur.

I have just run the command 'gedit /etc/default/grub' and it returns the following :

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

which is exactly as previously detailed. Hence my confusion - nothing appears to have changed. I have definitely not fiddled with anything, even by mistake, since I communicate with the Ubuntu machine via Terminal on my iMac.

---

### Post by Penfold1971 on 2014-11-26
I'm returning to this thread because the original problem recurred today.

I installed updates as per usual, following the prompt from the Software Updater. This was done at the Ubuntu machine (after, apparently, already updating from my Intel iMac remotely).

At the Ubuntu machine, I was prompted to Restart. What followed was a shutdown. I restarted the machine manually, and had to power off via the power supply switch because nothing happened except a grey/black, empty screen. Upon powering on and restarting again, I was eventually confronted with a screen I recognised from previous occasions. I had to choose one of the following, listed in the order they appeared on the screen :

[LEFT]*Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)[/LEFT]

The title at the top of this screen was :

[LEFT]GNU GRUB version 2.02^beta2-9ubuntu1[/LEFT]

Following previous advice here, I ran the command :

gedit /etc/default/grub

and got the same result as previously, namely :

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

What this all means in practical terms is that, at present, I can't remove the display, kb and mouse from the machine to run it headless, and use ssh from my Intel iMac to do updates and check temperatures, for fear of it playing dead on me when I have to do a Restart after certain updates.

Note: I am an enthusiastic amatueur and what little understanding I have of these matters has little to no depth.

Can anyone help me here?

---

### Post by Penfold1971 on 2014-11-27
Should I change GRUB_TIMEOUT=10 to GRUB_TIMEOUT=0?

---

### Post by Penfold1971 on 2014-11-29
It seems that a Restart as opposed to a Shutdown brings Ubuntu back to life (and at the same time Folding@Home restarts folding again automatically - Folding@Home being the only use I put this machine to). A _Shutdow_n causes the aforementioned stalling, waiting on me to choose what to do.

With Ubuntu 12.04, a Shutdown followed by powering back on never presented these problems.

I Restart when prompted after certain updates. A Shutdown is useful if I want to clean any accumulated dust out of the machine.

So it boils down to two questions :

1)  What Terminal command will I use to perform a Restart?  (I still regard myself to be a novice. I've always used 'sudo shutdown -h now' and can't remember why.)

2)  How can I make any necessary adjustments so that I can get the machine to boot into Ubuntu automatically after a Shutdown?

I really want to run this machine headless, as I had been doing with Ubuntu 12.04.

---

