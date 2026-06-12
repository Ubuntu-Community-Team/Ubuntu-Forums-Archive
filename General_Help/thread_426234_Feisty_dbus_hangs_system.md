---
title: "Feisty: dbus hangs system"
date: 2007-04-28
forum: General Help
---

### Post by SharkRider on 2007-04-28
My system seems to consistently lock up after about a minute going into multiuser mode, when the login prompt is displayed.

My system
Processor: Intel Core 2 Duo (E6420)
System board: Intel DQ965GF

I had problems with trying to install (K)Ubuntu via the LiveCD method, where I encountered the ["can't access tty" messages"]("http://ubuntuforums.org/showthread.php?t=292533"). 

I was able to use the Alternate CD to install.

I finished the install w/ no networking, rebooted up, and after being presented the login prompt, the system locks up hard. This happens regardless of me logging in or not; it consistenly locks up after the same amount of time had elapsed.

Booting into recovery mode works fine. I am able to stay in that shell indefinitely, but the moment I launch 'init 2', the system will lock up again.

I then started turning off each of the services in /etc/rc2.d (with the exception of gdm, of course!), and narrowed it down to dbus. With this off, I am able to launch the desktop, login, and not have it lock up (albeit, HAL is down, and networking is offlined).

So it seems like this dbus service is locking up my system. This is happening when I use (K)Ubuntu, 32- and 64-bit versions. I can't install Edgy, as I am not able to find an Alternate CD for that (same issue as above LiveCD problem).

Any ideas/insights/workarounds for this? Thanks in advance.

---

### Post by SharkRider on 2007-04-28
I answered my own question. I finally got everything to play nicely together.

I found that passing "all-generic-ide" in the kernel allowed everything to work properly.

To recap, in order to get (K)Ubuntu Feisty 7.04, 32- or 64-bit, to work on the Intel setup:
[LIST]
[*]Use the alternate CD to install
[*]First reboot, go into Recovery mode
[*]Edit /boot/grub/menu.lst, and append to the end of the kernel line, "all-generic-ide" (exclude the quotes).
[*]Reboot (or just do 'init 2')
[/LIST]

Hope this helps others!

Now, let's see if there are other things broken.... ;)

---

