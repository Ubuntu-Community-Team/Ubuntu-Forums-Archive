---
title: "Suspend breaks on 12.10's kernel"
date: 2012-10-20
forum: General Help
---

### Post by kli6891 on 2012-10-20
(Also posted at [http://askubuntu.com/questions/203745/suspend-breaks-on-12-10s-kernel](http://askubuntu.com/questions/203745/suspend-breaks-on-12-10s-kernel))

 0 down vote favorite
	

I just installed installed 12.10, and suspend is not working. Here are more details:

   [LIST]
[*]When I select suspend from the power menu, the screen goes black (with the monitor still running), but the computer is still running. Num Lock works, but Caps Lock doesn't work (see below). The computer never enters suspend mode, but I can't get the monitor to respond either. The only way I can get out of this situation is to shut down the machine by holding the power button.

[*]When I forcefully reboot it, I get the message "Ubuntu 12.10 has encountered an internal error". Apparently something is wrong with apportcheckresume.

[*]I googled a bit and found [this launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1062470"). I installed the amd64 kernel from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-quantal/"); on this new kernel suspend works. But there are no drivers, so it's not a solution.

[/LIST] 
    
    

So, the question is:

    1. How do I fix suspend on the current kernel (3.5.0-17-generic); OR
    2. How do I install drivers on the mainline kernel?

A solution to either will solve the problem.

--

[*] [How to debug suspend?]("http://askubuntu.com/questions/16239/how-to-debug-suspend") seem to suggest this is a kernel hang?

---

### Post by pqwoerituytrueiwoq on 2012-10-20
here is a kernel update installer
**whatever package contains the notify-send command is a unlisted dependency

have you tried this:
long suspend command
```
dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```lets give that a alias 
```
sudo sh -c "echo '#!/bin/sh\ndbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend' >/usr/local/bin/suspend;sudo chmod +x /usr/local/bin/suspend"
```now just run suspend from a terminal or keyboard shortcut
there is also this command
```
sudo pmi action suspend
```

---

### Post by kli6891 on 2012-10-21
Unfortunately, neither of those two suspend commmand worked. I tried out your script, but I get the following error:

```

--2012-10-21 02:29:04--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/linux-headers-3.6.2-030602_3.6.2-030602.201210121823_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/linux-headers-3.6.2-030602_3.6.2-030602.201210121823_all.deb)
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12258662 (12M) [application/x-debian-package]
Saving to: `linux-headers-3.6.2-030602_3.6.2-030602.201210121823_all.deb.3'

100%[======================================================================================================>] 12,258,662  3.23M/s   in 5.7s    

2012-10-21 02:29:10 (2.06 MB/s) - `linux-headers-3.6.2-030602_3.6.2-030602.201210121823_all.deb.3' saved [12258662/12258662]

--2012-10-21 02:29:10--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/linux-image-extra-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/linux-image-extra-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb)
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27871898 (27M) [application/x-debian-package]
Saving to: `linux-image-extra-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb.2'

100%[======================================================================================================>] 27,871,898  3.00M/s   in 14s     

2012-10-21 02:29:24 (1.91 MB/s) - `linux-image-extra-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb.2' saved [27871898/27871898]

--2012-10-21 02:29:24--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/linux-headers-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/linux-headers-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb)
Reusing existing connection to kernel.ubuntu.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 943398 (921K) [application/x-debian-package]
Saving to: `linux-headers-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb.2'

100%[======================================================================================================>] 943,398     2.10M/s   in 0.4s    

2012-10-21 02:29:25 (2.10 MB/s) - `linux-headers-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb.2' saved [943398/943398]

--2012-10-21 02:29:25--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/linux-image-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/linux-image-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb)
Reusing existing connection to kernel.ubuntu.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 12279358 (12M) [application/x-debian-package]
Saving to: `linux-image-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb.2'

100%[======================================================================================================>] 12,279,358  3.21M/s   in 5.4s    

2012-10-21 02:29:31 (2.18 MB/s) - `linux-image-3.6.2-030602-generic_3.6.2-030602.201210121823_amd64.deb.2' saved [12279358/12279358]

FINISHED --2012-10-21 02:29:31--
Total wall clock time: 21s
Downloaded: 3 files, 39M in 20s (1.99 MB/s)
dpkg-deb (subprocess): cannot copy archive member from './linux-headers-3.6.2-030602_3.6.2-030602.201210121823_all.deb' to decompressor pipe: unexpected end of file or stream
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing ./linux-headers-3.6.2-030602_3.6.2-030602.201210121823_all.deb (--install):
 cannot copy extracted data for './usr/src/linux-headers-3.6.2-030602/arch/ia64/include/asm/paravirt_privop.h' to '/usr/src/linux-headers-3.6.2-030602/arch/ia64/include/asm/paravirt_privop.h.dpkg-new': unexpected end of file or stream
Done.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
dpkg: dependency problems prevent configuration of linux-headers-3.6.2-030602-generic:
 linux-headers-3.6.2-030602-generic depends on linux-headers-3.6.2-030602; however:
  Package linux-headers-3.6.2-030602 is not installed.

dpkg: error processing linux-headers-3.6.2-030602-generic (--install):
 dependency problems - leaving unconfigured
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.6.2-030602.201210121823 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.6.2-030602.201210121823 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
update-initramfs: Generating /boot/initrd.img-3.6.2-030602-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.7.0-030700rc1-generic
Found initrd image: /boot/initrd.img-3.7.0-030700rc1-generic
Found linux image: /boot/vmlinuz-3.6.2-030602-generic
Found initrd image: /boot/initrd.img-3.6.2-030602-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.6.2-030602.201210121823 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.6.2-030602.201210121823 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
update-initramfs: Generating /boot/initrd.img-3.6.2-030602-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.6.2-030602-generic /boot/vmlinuz-3.6.2-030602-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.7.0-030700rc1-generic
Found initrd image: /boot/initrd.img-3.7.0-030700rc1-generic
Found linux image: /boot/vmlinuz-3.6.2-030602-generic
Found initrd image: /boot/initrd.img-3.6.2-030602-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Errors were encountered while processing:
 ./linux-headers-3.6.2-030602_3.6.2-030602.201210121823_all.deb
 linux-headers-3.6.2-030602-generic

```

---

### Post by pqwoerituytrueiwoq on 2012-10-21
looks like a bad download to me
i used this 3 times in the last 2 days
this copy is harder to mess-up with

---

### Post by Farinet on 2012-10-21
> **kli6891 said:**
> (Also posted at [http://askubuntu.com/questions/203745/suspend-breaks-on-12-10s-kernel](http://askubuntu.com/questions/203745/suspend-breaks-on-12-10s-kernel))

 0 down vote favorite
    

I just installed installed 12.10, and suspend is not working. Here are more details:

[LIST]
[*]When I select suspend from the power menu, the screen goes black (with the monitor still running), but the computer is still running. Num Lock works, but Caps Lock doesn't work (see below). The computer never enters suspend mode, but I can't get the monitor to respond either. The only way I can get out of this situation is to shut down the machine by holding the power button.
[*]When I forcefully reboot it, I get the message "Ubuntu 12.10 has encountered an internal error". Apparently something is wrong with apportcheckresume.
[*]I googled a bit and found [this launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1062470"). I installed the amd64 kernel from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-quantal/"); on this new kernel suspend works. But there are no drivers, so it's not a solution.
[/LIST]
    
    

So, the question is:

    1. How do I fix suspend on the current kernel (3.5.0-17-generic); OR
    2. How do I install drivers on the mainline kernel?

A solution to either will solve the problem.

--
[*] [How to debug suspend?]("http://askubuntu.com/questions/16239/how-to-debug-suspend") seem to suggest this is a kernel hang?


I second you! I posted a thread when i didn't see yours: [http://ubuntuforums.org/showthread.php?t=2074139](http://ubuntuforums.org/showthread.php?t=2074139) (May be some good soul of administrator here could put them together in some way?)

Just to mention: I'm on lubuntu 12.10, but i  checked with a Fedora 17 live cd (based on 3.6 kernel and a kubuntu 12.10 as well as with a LinuxMint Debian 13 (based on 3.2 kernel). Only the Linux Mint was able to suspend and to hibernate.

---

### Post by Farinet on 2012-10-21
> **pqwoerituytrueiwoq said:**
> here is a kernel update installer
**whatever package contains the notify-send command is a unlisted dependency]

lets give that a alias 
```
sudo sh -c "echo '#!/bin/sh\ndbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend' >/usr/local/bin/suspend;sudo chmod +x /usr/local/bin/suspend"
```now just run suspend from a terminal or keyboard shortcut
there is also this command
```
sudo pmi action suspend
```

When i try this command, i'm getting this error msg
```
bash: !/bin/sh\ndbus-send: event not found
```

---

### Post by pqwoerituytrueiwoq on 2012-10-21
```
sudo sh -c 'echo "#!/bin/sh\ndbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend" >/usr/local/bin/suspend;chmod +x /usr/local/bin/suspend'
```
fixed

---

### Post by Farinet on 2012-10-21
> **pqwoerituytrueiwoq said:**
> ```
sudo sh -c 'echo "#!/bin/sh\ndbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend" >/usr/local/bin/suspend;chmod +x /usr/local/bin/suspend'
```fixed

That worked. But the following command not:

```
myname@ab-535U3C:~$ sudo pmi action suspend
sudo: pmi: Befehl nicht gefunden

```

---

### Post by kli6891 on 2012-10-21
> **Farinet said:**
> I second you! I posted a thread when i didn't see yours: [http://ubuntuforums.org/showthread.php?t=2074139](http://ubuntuforums.org/showthread.php?t=2074139) (May be some good soul of administrator here could put them together in some way?)

Just to mention: I'm on lubuntu 12.10, but i  checked with a Fedora 17 live cd (based on 3.6 kernel and a kubuntu 12.10 as well as with a LinuxMint Debian 13 (based on 3.2 kernel). Only the Linux Mint was able to suspend and to hibernate.

Good to know I'm not the only one having this problem :P. 
Have you tried the mainline kernels I linked in the first post to see if that fixes your problem?

> **pqwoerituytrueiwoq said:**
> looks like a bad download to me
i used this 3 times in the last 2 days
this copy is harder to mess-up with

OK, this new version worked, and I booted into the new kernels it installed. All the drivers are working! (3.6.2, and 3.7rc2, or something to that effect.)

But suspend does not work, still -- same symptoms as before. 

As I said before, the 3.7rc1 I installed from mainline does have a working suspend. I'm starting to suspect now that it's the video driver that is causing me problems; I googled around a bit, and found reference to some nouveau driver preventing sleep. 

Is there a way to disable the video driver, so I can confirm this is the case?

---

### Post by pqwoerituytrueiwoq on 2012-10-21
```
echo "blacklist nouveau" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
i assume you spelled the driver name right

if you have a nvidia driver i suggest using nouveau or nvidia-current
nouveau has come a long way from what it used to be, spelling it is still a pain though

---

### Post by kli6891 on 2012-10-21
OK, I tried the above, and unfortunately, it did nothing. Apparently, my system isn't using the nouveau drivers. :O

I don't know what to try now. Something with Ubuntu's kernel doesn't work well with my laptop. If you google "apportcheckresume", and limit the date range to, say, the past week, you'll see that some other people are having the same problem.

Thank you for help; hopefully the developers will fix this soon :)

---

### Post by pqwoerituytrueiwoq on 2012-10-21
after blacklisting you have to reboot for it to be applied

---

### Post by Farinet on 2012-10-22
> **kli6891 said:**
> Good to know I'm not the only one having this problem :P. 
Have you tried the mainline kernels I linked in the first post to see if that fixes your problem?

Where did you point to? May be i've overseen something.

As a subscriber of a bug (in the context of powerpc testing regarding ubiquity) i was pointed to this site:

[https://wiki.ubuntu.com/Kernel/MainlineBuilds#Mainline_Kernels_Archive](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Mainline_Kernels_Archive)

But when i tried to install i got an error:

```

sudo dpkg -i linux-headers-3.7.0-030700rc2-generic_3.7.0-030700rc2.201210201535_amd64.deb

dpkg: Abhängigkeitsprobleme verhindern Konfiguration von
linux-headers-3.7.0-030700rc2-generic:
 linux-headers-3.7.0-030700rc2-generic hängt ab von
linux-headers-3.7.0-030700rc2; aber:
  Paket linux-headers-3.7.0-030700rc2 ist nicht installiert.

dpkg: Fehler beim Bearbeiten von linux-headers-3.7.0-030700rc2-generic
(--install):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 linux-headers-3.7.0-030700rc2-generic

```

Please keep in mind, i'm a simple user not a "coder" . . . ;-)

---

### Post by Farinet on 2012-10-22
I tried with kernel 3.6.0-030600-generic (x86_64) but no luck: The problem remains exactly the same.

[EDIT]: And same goes for 3.6.3 . I think, with that flavour of kernels i won't have luck. We'd someone who creates a patch or who finds out some other workaround. In any case: To NOT have suspend-to-ram (at least, if not suspend-to-disk) on a potable is ridiculous .  .  . :-((

---

### Post by pqwoerituytrueiwoq on 2012-10-22
what hardware are you using
i did not use the 3.5 kernel much, but i do not recall having suspend problems on either of my systems
they are both amd + nvidia

---

### Post by Farinet on 2012-10-22
A Samsung 535 u3c with 2xAMD A6-4455M APU with Radeon (tm) HD Graphics

8GB ram

---

### Post by Farinet on 2012-10-22
Just an add-on: 

I did an upgrade to 12.10 on a SamsungNetbook (150P - atom processor = i386 version) and there standby works (hibernate is deactivated but somewhere on a ubuntu help site i remember i saw how it could be reactivated). Anyway, so this problems seems to touch only certain kinds of machines . . .

---

### Post by Farinet on 2012-10-23
Nice news, at least for me: Looking for a possibility to (re)establish the functionality of Fn-keys on my Samsung "googling" around i found this site:

[http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/](http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/)

I installed the ppa and the samsung-tools package (the samsung-laptop package did not exist, at least for met) and although it seems conceived for another model of Samsung laptop the tools work for me.

After the installation first i realized that the fonts were magnified (i had to reduce from 11 pt to 9 pt to return to the previous situation but ok) but on the other hand, i gained control over wifi, bluetooth and fan by Fn-keys and settings. And, HEUREKA, now, at least i'm able to use hibernate (suspend-to-disk) and can turn back awakening wifi by Fn+F12.

And after i installed the proprietarian - as far as i understand it - Radeon driver (fglrx + associated; found in synaptic) there is also Standby (suspend-to-ram). Moreover the blown-up fonts are reduced to the normal way. 

So far, on the Samsung all fine (but frankly, i do not understand, why this isn't this way by default).

---

### Post by dgharmon on 2013-02-09
I can suspend but cannot resume, I press a key and it powers up and hangs there, the keyboard is then non-resposive, ie num-lock don't work ...

---

### Post by Farinet on 2013-02-09
> **dgharmon said:**
> I can suspend but cannot resume, I press a key and it powers up and hangs there, the keyboard is then non-resposive, ie num-lock don't work ...

I have exactly the same problem (on a Samsung 535 - amd64) with all kernels higher than 3.2. With the standard Debian kernel of testing (3.2) suspend and resume works.

I'm not a technician, asked around here and there, tried to install other graphic card drivers (the not-free amd ati driver) but to no different result. I also tried to install different distributions (lubuntu, debian, crunchbang) but it's always the same, unfortunately. 

I suspect it's something in the kernel, but very likely it's only a very few persons suffering this problem so no one cares . . . 

Cheers.

---

### Post by dgharmon on 2013-02-10
> **Farinet said:**
> I have exactly the same problem (on a Samsung 535 - amd64) with all kernels higher than 3.2 ..

The 'Step 2' worked for me, now I briefly get masses of kworker processes, unless I didn't notice them before ...


[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)

---

### Post by roachmmflhyr on 2013-02-17
> **dgharmon said:**
> The 'Step 2' worked for me, now I briefly get masses of kworker processes, unless I didn't notice them before ...

[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)

Run this to see what has the most interrupts:
```
grep enabled /sys/firmware/acpi/interrupts/*
```

Add this to your /etc/rc.local or /etc/init.d/rc.local file:
```

echo "disable" > /sys/firmware/acpi/interrupts/gpeXX 
## Where XX is the gpe number with the most interrupts

```

Reboot and enjoy!

---

### Post by NetworkNerd7 on 2013-03-26
If you simply want it to stop popping up errors on resume, try the following:

```
sudo gedit /etc/default/apport
```

and then change:

```
enabled=1
```
to
```
enabled=0
```

Cheers ;)

---

### Post by stelladeli on 2013-06-01
dgharmon I have the same problem/bug with an Hp pavilion dv7 notebook.

You said that step 2 worked...but the fix is for Ubuntu 12.04...Is it safe to try it on 12.10?

---

### Post by toobaz on 2013-09-02
> **dgharmon said:**
> I can suspend but cannot resume, I press a key and it powers up and hangs there, the keyboard is then non-resposive, ie num-lock don't work ...

I had exactly the same problem, on a Samsung 535U3c with Ubuntu 12.10, but it was solved by installing the fglrx drivers. I did that through "software-properties" and I selected the last option (I think it was called "proprietary-updates", while the second was "proprietary").

(there still was a problem with wifi non working after suspend, but that was solved as described in the following post:
[http://ubuntuforums.org/showthread.php?t=2029875&p=12468150#post12468150](http://ubuntuforums.org/showthread.php?t=2029875&p=12468150#post12468150)

Now everything seems to work great. I didn't test hibernation however, and neither virtual consoles (which Farinet on another forum reported as broken with fglrx).

---

### Post by macoymadson on 2013-09-13
I'm also having this same problem with Lubuntu 13.04 (Kernel 3.8.0-19-generic)
I have an HP Pavilion dv8210us (AMD Turion 64 ML-32).

It seems like the only fix so far only works with Samsung devices. Does anyone have any ideas?

---

