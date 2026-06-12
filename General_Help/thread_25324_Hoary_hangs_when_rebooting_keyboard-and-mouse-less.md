---
title: "Hoary *hangs* when rebooting keyboard-and-mouse-less servers"
date: 2005-04-09
forum: General Help
---

### Post by user-jon on 2005-04-09
Hi, I need help to get to the bottom of this problem..

I have a fully up to date Ubuntu Hoary, on two servers (a new Athlon64 3000+  and  an older Athlon 750).

Under normal circumstances, Ubuntu can reboot both PCs just fine.
However, if I:
- disconnect *both* the keyboard *and* the mouse (leaving just network, vga and power)
- then boot up Ubuntu
- then go to some other workstation and ssh into the server as root
- then try to reboot the server (with 'shutdown -rt2 now')
- after all the normal shutdown messages, the screen blanks but the PC just *hangs*
  (as the system is running /etc/rc6.d/S90reboot)

Extra Info:
- just running 'reboot -d -f' directly causes the same hang.
- I'm talking about PS/2 keyboard and PS/2 mouse, by the way.
- this behaviour is exhibited on both machines, regardless of architecture
  (ie. using the latest ubuntu kernel 2.6.10-34, for amd64 both k8 and generic,
  and for x86 both k7 and 386)
- 'shutdown -ht2 now' *does* still correctly power off the machine (it's just reboots that fail)
- it's very specific that *both* keyboard and mouse have to be unplugged *while Ubuntu is starting*.
  You can plug them back in after booting but the PC will still hang.
  If either the mouse *or* the keyboard (or both) is plugged in while Ubuntu is starting, the hang does not happen.

Can anybody shed any light on this?
Any particular kernel boot parameters I should try?
Is there a Ubuntu 2.6.11 kernel available / coming soon that I can try?

Thanks..

---

### Post by user-jon on 2005-04-10
..me again.

Just wanted to add that even if you don't have any ideas for this problem...
if you have access to an Ubuntu box and any other networked PC,
it would be very helpful if you could test this out and post back here if you
see the same behaviour -- should only take a few of your earth minutes.

- on Ubuntu box:
    if necessary, install 'openssh-server' (run 'apt-get install openssh-server')
    take note of your IP address (eg.run 'ifconfig' and look for
      'inet addr:' field under 'eth0' section)
    reboot and unplug keyboard and mouse immediately -- before Ubuntu
      starts up again.
- on the other box:
    if it's linux/unix you probably have 'ssh' client already, so run:
        ssh <adminuser>@<ubuntu_ip_addr>
    if it's windows get 'putty.exe' from
        [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
        and run:
        putty -ssh <adminuser>@<ubuntu_ip_addr>
    then run 'sudo reboot' and check if the Ubuntu box hangs..

If you can confirm this problem, then maybe we can get one of the
clever "Succulent Strawberries" kernel folks to have a look at it
..there must be other sufferers who are trying to run headless servers.

Many thanks.. Jon

---

### Post by daniels on 2005-04-10
I wouldn't be surprised if it's a hardware issue.  Is your BIOS telling you that you have no keyboard and waiting for you to press F1?  Headless machines have always worked fine for me.

---

### Post by user-jon on 2005-04-11
[QUOTE=daniels]I wouldn't be surprised if it's a hardware issue.  Is your BIOS telling you that you have no keyboard and waiting for you to press F1?  Headless machines have always worked fine for me.[/QUOTE]

hi there, that's not the problem because, just to reiterate:
1) i can reproduce this on 3 different machines (2 kubuntu and 1 ubuntu)

2) i can plug the keyboard and mouse *back in* before i reboot and the hang still happens 
    (the trigger for the problem is that both the keyboard and mouse are missing as Ubuntu loads and initialises)

3) i can leave the monitor attached and *see* that it doesn't even begin the BIOS's reboot process.
    (in a normal reboot, the 3 keyboard LEDs blink simulatenously a few times.. then the screen goes black.. then the BIOS boot process starts.
    in this case, the 3 LEDs don't blink at all.. then the screen goes black.. then it just hangs forever)

4) the BIOS 'keyboard error' settings were the first thing I checked


Anybody tried testing this on a fully updated 'hoary hedgehog' box yet?
Thanks

---

