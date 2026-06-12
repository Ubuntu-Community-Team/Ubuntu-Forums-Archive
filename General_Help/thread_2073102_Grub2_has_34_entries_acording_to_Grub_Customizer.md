---
title: "Grub2 has 34 entries acording to Grub Customizer"
date: 2012-10-19
forum: General Help
---

### Post by vt.dave on 2012-10-19
I just upgraded to 12.10 and on boot my grub2 screen:
[LIST=1]
[*]Was really slow, Should I lower the resolution?
[*]had MANY duplicates
[/LIST]

34 items are listed according to grub customizer:
see: [http://i.imgur.com/1n0Lq.png](http://i.imgur.com/1n0Lq.png) - grub2 customizer

Many of them correspond to the loading scripts like 15_osprober and when I ls /etc/grub.d/:
```
dave@shuttle:/etc/grub.d$ ls -l
total 124
-rwxr-xr-x 1 root root  7541 Oct 14 13:36 00_header
-rwxr-xr-x 1 root root  5488 Oct  4 05:30 05_debian_theme
-rwxr-xr-x 1 root root 10891 Oct 14 13:36 10_linux
-rwxr-xr-x 1 root root  7545 Oct  1  2011 10_os-prober
-rwxr-xr-x 1 root root  1032 Aug 15 19:50 11_linux_proxy
-rw-r--r-- 1 root root  1030 Aug 15 19:50 12_linux_proxy
-rwxr-xr-x 1 root root  6335 Apr 17  2012 13_linux_xen
-rw-r--r-- 1 root root  1030 Aug 15 19:50 14_linux_proxy
-rw-r--r-- 1 root root  7603 Apr 17  2012 15_os-prober
-rwxr-xr-x 1 root root   265 Aug 15 19:50 16_memtest86+_proxy
-rw-r--r-- 1 root root   214 Oct  1  2011 17_custom
-rw-r--r-- 1 root root    95 Oct  1  2011 18_custom
-rwxr-xr-x 1 root root 10258 Oct 14 13:36 20_linux_xen
-rwxr-xr-x 1 root root  1688 Oct 11 10:10 20_memtest86+
-rwxr-xr-x 1 root root 10976 Oct 14 13:36 30_os-prober
-rwxr-xr-x 1 root root  1426 Oct 14 13:36 30_uefi-firmware
-rwxr-xr-x 1 root root   216 Oct 14 13:36 41_custom
drwxr-xr-x 2 root root  4096 Jan 19  2012 bin
drwxr-xr-x 2 root root  4096 Aug 15 19:56 proxifiedScripts
-rw-r--r-- 1 root root   483 Oct  1  2011 README

```

there are a LOT of duplicates.

What can I safely remove?  And how?

Thanks!
-Dave

---

### Post by Lisiano on 2012-10-19
Could you be more verbose about what exactly you see? You might just be seeing old kernels. Please post your /boot/grub/grub.cfg using [Ubuntu Pastebin](http://paste.ubuntu.com/). You may use code tags but it will be easier to navigate it using Pastebin.

---

### Post by vt.dave on 2012-10-19
Thanks for the reply
> **Lisiano said:**
> Please post your /boot/grub/grub.cfg using [Ubuntu Pastebin](http://paste.ubuntu.com/).

Here you go:
[http://paste.ubuntu.com/1288469/](http://paste.ubuntu.com/1288469/)

I don't think these are old kernels, my grub menu was basically:
Ubuntu
Linux-3.5
Linux-3.5-recovery
Windows 7
Linux 3.5
Linux 3.5-recovery
memtest x86
memtest x86 serial
memtest x86
memtest x86 serial
Windows 7
Linux 3.5
Windows 7 (/dev/sda1)

It was just really weird how they were all duplicated like that.

Thanks for any help you can provide!

---

### Post by oldfred on 2012-10-19
Not sure what your proxitified scripts are.

Did you renumber scripts back in Aug to change boot order in menu?

Then when you upgraded it put all the standard number scripts back in, creating duplicates.

My new install which I am not in now:

```
fred@fred-Precise:/media/Quantal/etc/grub.d$ ls -l
total 72
-rwxr-xr-x 1 root root  7541 Oct 14 12:36 00_header
-rwxr-xr-x 1 root root  5488 Oct  4 04:30 05_debian_theme
-rwxr-xr-x 1 root root 10891 Oct 14 12:36 10_linux
-rwxr-xr-x 1 root root 10258 Oct 14 12:36 20_linux_xen
-rwxr-xr-x 1 root root  1688 Oct 11 09:10 20_memtest86+
-rwxr-xr-x 1 root root 10976 Oct 14 12:36 30_os-prober
-rwxr-xr-x 1 root root  1426 Oct 14 12:36 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 14 12:36 40_custom
-rwxr-xr-x 1 root root   216 Oct 14 12:36 41_custom
-rw-r--r-- 1 root root   483 Oct 14 12:36 README

```

---

### Post by vt.dave on 2012-10-19
I used Grub Customizer in 11.10 to remove some old kernels and move Windows 7 to the top.

Since I wasn't comfortable mucking with the grub XX_myoshere scripts I wanted to use a GUI.

Now i think my grub scripts are just a mess because of it.

is it safe to delete duplicated scripts, then just do a sudo grub-update?

Also can I verify that the grub config is what I want before I reboot so I'm not hosed?

Thanks,
-Dave

---

### Post by grahammechanical on 2012-10-19
Yes, you got something like what I got when I was testing 12.10 and Grub 1.99 was updated to Grub 2.0.

Part of the mess is caused by Grub 2.0 using different designations for kernel images to that used by Grub 1.99. So, you get both designations. And a lot more duplicates besides.

Grub Customizer does not (or did not a few weeks ago) work well with the Grub 2.0 menus. It messed the menu even further by not recognising Grub 2 sub-menus.

The good news is that although it is difficult to know what OS you are booting in, it does not break any OS. Believe me. I have lived with this for a few weeks.

At the Grub menu select an entry and press e. That will stop the count down timer and let you edit the entry.

Press esc to backout or F10 to boot that entry. You will notice that in the new Grub 2.0 sda1, sda2, etc., has has been replaced by msdos1, msdos2, etc. So, look for msdos to identify the partition that is being booted.

I would also suggest that you use Synaptic Package Manager (not installed by default) to remove old kernels. Then run

```
sudo update-grub
```

that will simplify the menu.

A lot of work has been done in the last few weeks by a Ubuntu developer to make things better.

Oh, by the way, it is intended to bring Grub 2.0 into Ubuntu 12.04 by the end of January. Let the fun begin!

Regards.

---

### Post by vt.dave on 2012-10-19
thanks grahammechanical.

That advice is great, but more for fixing it from the grub menus right?  I'm in Ubuntu 12.10, and would really like my end result to be:

Windows 7 at the top of the boot list and defaultly selected (for the wife)
Ubuntu
memtest x86

With the mess of scripts I now have in /etc/grub.d/ and the total mess my grub.cfg is, what's the easiest way for me to get there?

can I somehow delete all the scripts in /etc/grub.d and auto generate the default ones?

I just really don't want to hose my grub so I end up at: grub recover>  ;)

---

### Post by oldfred on 2012-10-19
You can just backup your grub scripts, then totally delete the grub.d folder. The do a total reinstall of grub2.

If you are in your system you skip the chroot and just run the uninstall & reinstall commands. Make sure Internet is working as you have to download grub package again or else you cannot reboot.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

