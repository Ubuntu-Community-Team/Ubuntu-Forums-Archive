---
title: "Recurring shutdown problem"
date: 2007-10-22
forum: General Help
---

### Post by MegaSvensk on 2007-10-22
Hi,

Sometimes when I attempt to shutdown my Utbuntu 7.10, I get this error:
```
NetworkManager: <WARN> nm_signalhandler (): Caught signal 15, shutting down normally

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1193029284.958940] nm_print_open_socks(): Open Sockets List

NetworkManager: <debug> [1193029284.959004] nm_print_open_socks(): Open Sockets List Done

NetworkManager: <info> Deactivating device eth0

NetworkManager: <info> Deactivating device eth1

NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - connection is closed

NetworkManager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection ' failed

NetworkManager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection ' failed

NetworkManager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection ' failed
```

Does anyone know how to fix this?

---

### Post by MegaSvensk on 2007-10-22
bump

---

### Post by MegaSvensk on 2007-10-22
Bump again

---

### Post by Big Ben on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've been getting the same errors, ending with:
```
could not get the system bus. Make sure the message bus daemon is running!
```

This might be related to Bug #138691
It doesn't happen on every shutdown, but about once every five times. It's quite annoying to have to hold the power button to shut down my machine, so ...Bump!

---

### Post by danielsbrewer on 2007-11-09
I'm getting the same problem in Gutsy.  It's annoying, but doesn't occur all the time.

---

### Post by Big Ben on 2007-11-09
I may have figured out how to fix it.

[https://answers.launchpad.net/ubuntu/+question/16914]("https://answers.launchpad.net/ubuntu/+question/16914")

Adding acpi=force to grub options seems to have worked, but it's hard to tell since the problem doesn't happen every time anyway.

---

### Post by Big Ben on 2007-11-12
I spoke too soon. It still happens some of the time. This is really annoying.

---

### Post by Chiad on 2008-02-24
i'm bumping this cause i also get this problem. BUT..

my computer shuts down perfect everytime. my problem is that it happens when i least want it. f.ex if im running firefox and a site with a large flashfile.. it hangs, and then if it has to use to much CPU or is stressed to much.. it shuts down automaticly:(:(:(:(


im getting the same error message as this post.. caught termination signal or killsignal (15). 

really annoying! does anyone know why it turns of itself like that?? im starting to hate my computer as im starting to think that it hates me!

---

### Post by Chiad on 2008-02-26
Bump! (haha, what a retard thing to say:P)

---

### Post by ubermaus on 2008-02-27
[COLOR="Purple"]Hello. I'm new to Ubuntu, and I'm having the same issue with my pc. I'm dual-booting with Vista (installed first) and Gutsy Gibbon (Ubuntu 7.10) on an AMD-based system with DSL internet connection.

Quite frankly, I'm at the end of my rope and just about ready to give up on Ubuntu altogether if I cannot solve this problem.

I've spent the last several days scouring the internet and found many suggested fixes but, interestingly enough, the only solution(s) that works on my system is the **exact** combination of fixes that I list below. I've tried each one (along with others) individually, in every possible combination, and in differing orders, but only the exact combination _and_ exact order of fixes below allows my system to shut down properly. (NOTE: Each fix and combination of fixes was applied after a clean re-installation of Ubuntu.)

However, although these fixes solved the shutdown issue, they raised another unacceptable issue: I no longer have access to the internet. I read somewhere that Network Manager is not needed to connect to the internet, but I know this to be untrue for my system. When I simply disable Network Manager by right-clicking on the icon and unchecking "Enable Network Manager," I lose my internet connection, while enabling it restores my connection.

Anyway, here is the combination of actions I must take for Ubuntu to properly shut down my pc:[/COLOR]

1.  From ["Gutsy network-manager causes OS to freeze on system restart or power down"]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3"):

> [COLOR="Green"]The problem appears to be caused when network manager catches the SIGTERM (15) signal
I have a workaround involving hard killing network manager with SIGKILL:

Modify /etc/dbus-1/event.d/25NetworkManager as follows (just add the --signal 9 option)

d_stop() {
        # Modified MF 11 Feb 2008 To avoid NM hang
        #start-stop-daemon --stop --retry 60 --quiet --pidfile $PIDFILE \
        # --oknodo --user $USER --exec $DAEMON

        start-stop-daemon --stop --signal 9 --retry 60 --quiet --pidfile $PIDFILE \
                 --oknodo --user $USER --exec $DAEMON
}

Modify /etc/init.d/sendsigs as follows
...
        # Kill all processes.
        log_action_begin_msg "Terminating all remaining processes"

        # Added MF 11 Feb 2008 To avoid shutdown hang
        OMITNM=
        if [ -f /var/run/NetworkManager/NetworkManager.pid ]; then
                OMITNM=$(cat /var/run/NetworkManager/NetworkManager.pid)
                OMITNM="-o $OMITNM"
        fi
        echo "Not killing $OMITNM"

        killall5 -15 $OMITPIDS $OMITNM

        # END MF mods
        log_action_end_msg 0
...

- Martin Fuzzey[/COLOR]

2. From [URL="http://ubuntuforums.org/showthread.php?t=359190"]"Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > Hardware & Laptops  
 Incomplete shutdown issue"[/URL]:

> [COLOR="green"]For anyone else having these issues:

I've fixed it! No more annoying shutdown problems. The answer is kinda spaced out over a couple of posts:

[http://www.ubuntuforums.org/showthre...highlight=hang](http://www.ubuntuforums.org/showthre...highlight=hang)

[http://ubuntuforums.org/showthread.p...light=shutdown](http://ubuntuforums.org/showthread.p...light=shutdown)

Basically I combined steps from both posts into this:

Step 1: Add Code:

apm power_off=1

to your /etc/modules

Mine already had an entry so I just added the code directly below it and then hit enter to add 1 blank space at the end of the file. Basically it should look like this:

Code:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
apm power_off=1

You may have other modules like fuse or p4_clockmod or whatnot. That's ok. So long as you put in "apm power_off=1" and keep a blank entry at the end of the file you should be ok. The blank entry might not be needed, but it was there when I started so I kept it.

Step 2: Add Code:

acpi=off apm=power_off

to your /boot/menu.lst so it looks like this:

Code:

## ## End Default Options ##

title Debian GNU/Linux, kernel 2.6.18-3-k7
root (hd0,1)
kernel /boot/vmlinuz-2.6.18-3-k7 root=/dev/hda2 ro acpi=off apm=power_off
initrd /boot/initrd.img-2.6.18-3-k7

You probably have other entries in your boot stanza like quiet splash and the like, but that's ok. So long as the acpi=off apm=power_off is there it should work.

Please note that just about all the code and what not are shameless rips from Kross's excellent posts. PM him a pat on the back if this worked for you, since it looks like he really took initiative and tracked this problem down well.

- Redeyes_Gambit[/COLOR]

3. From ["WifiDocs/NetworkManager"]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"):

> [COLOR="green"]According to  this bug here's how to disable Network Manager without uninstalling it: 

Stop network manager 

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are: 

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher[/COLOR]

[COLOR="purple"]The following suggested fixes did *not *work for me:[/COLOR]

[COLOR="blue"]Restart in single user mode
sudo apt-get remove network-manager-gnome
sudo apt-get remove network-manager
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome

logout then restart (or shutdown)

resetting my Visual Effects to Normal[/COLOR]

[COLOR="Red"]Any suggestions - anyone? Please?![/COLOR]

---

### Post by ubermaus on 2008-02-28
[COLOR="Purple"]Phew! I finally found the solution to my shutdown problem. Ironically, after attempting various suggested fixes as detailed in my previous post, the solution turned out to be an extremely simple one.

I reinstalled Ubuntu (yet again) and, at the splash menu, I clicked F6 to bring up the linux kernel command line. At the end of the line, I typed *acpi=force noapic*. Previously, I had typed *acpi=off noapic*, per someone's suggestion, because I was unable to install Ubuntu. Well, all I needed to do was change *off* to *force*! Simple, right?

This not only solved my shutdown issue but also retains my internet connection since I do not even need to touch Network Manager.

Once again, Ockham's Razor rules and the simplest solution is the best.

I hope this solution works for others who may be experiencing the same problem.

Note: I only reinstalled Ubuntu (as opposed to simply changing the kernel line in the /boot/grub/menu.lst file) because I wanted a fresh install on my newly built pc.

:biggrin:

P.S. A nod to Big Ben - I hesitated to try your solution because you later posted that it did not work, after all, but perhaps the additional *noapic * command may be necessary.[/COLOR]

---

### Post by davegod75 on 2008-03-12
hmm, I get the same thing with my computer running Hardy.

---

### Post by pbubenik on 2008-04-29
I have the same problem with Hardy.

---

### Post by t4ggs on 2008-05-11
> **ubermaus said:**
> [COLOR="Purple"]Phew! I finally found the solution to my shutdown problem. Ironically, after attempting various suggested fixes as detailed in my previous post, the solution turned out to be an extremely simple one.

I reinstalled Ubuntu (yet again) and, at the splash menu, I clicked F6 to bring up the linux kernel command line. At the end of the line, I typed *acpi=force noapic*. Previously, I had typed *acpi=off noapic*, per someone's suggestion, because I was unable to install Ubuntu. Well, all I needed to do was change *off* to *force*! Simple, right?

This not only solved my shutdown issue but also retains my internet connection since I do not even need to touch Network Manager.

Once again, Ockham's Razor rules and the simplest solution is the best.

I hope this solution works for others who may be experiencing the same problem.

Note: I only reinstalled Ubuntu (as opposed to simply changing the kernel line in the /boot/grub/menu.lst file) because I wanted a fresh install on my newly built pc.

:biggrin:

P.S. A nod to Big Ben - I hesitated to try your solution because you later posted that it did not work, after all, but perhaps the additional *noapic * command may be necessary.[/COLOR]

How do i do it...im having the same problem...reinstalled hardy and nothing.
I turned the pc on and keep pressinG F6 but nothing happens....where do i have to add the line acpi=force noapic at menu.lst
this is mine:


title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=43990f9e-1080-45d2-87d7-4f180569c9b7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=43990f9e-1080-45d2-87d7-4f180569c9b7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet



Thank u

---

### Post by Scruffynerf on 2008-05-18
Seems to be happening for me also on Hardy, however putting the ```
acpi=force noapic
```
at the end of the 'kernel' line did not fix it for me.

---

### Post by jb5 on 2008-05-30
Have the same problem. Even the recent kernel upgrade (2.6.24-17-generic) did not cure the problem for me.

Problem appears to have been introduced with Hardy Upgrade, no problems whilst running Gutsy.

Will try the 
```
acpi=force noapic 
```
again but didn't solve the problem previously.

---

### Post by jb5 on 2008-05-31
Nope. Still failing.

Filed separate bug report and attached info requested in another bug report for this issue [original bug report](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42160).

[my bug report](https://bugs.launchpad.net/ubuntu/+bug/227844)

---

