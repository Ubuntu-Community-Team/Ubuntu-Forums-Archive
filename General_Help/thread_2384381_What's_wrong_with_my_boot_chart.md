---
title: "What's wrong with my boot chart?"
date: 2018-02-06
forum: General Help
---

### Post by QwUo173Hy on 2018-02-06
[ATTACH]278455[/ATTACH]
I installed Ubuntu on my Uncles computer a few years ago. He hasn't installed many apps or used it much, but boot has gotten slower over the years. It's on 16.04 now, can anyone see an obvious culprit from the bootchart - something that has a solution?

I'd like to avoid a reinstall since Windows is also on the same disk and it was very difficult to get them to play well together.

---

### Post by TheFu on 2018-02-06
It is probably worth telling us about the hardware involved.  All mainstream Linux desktop systems demand more hardware today than they did even 5 yrs ago.  16.04 with Unity is a hog, IMHO.  There are lighter versions that will run nicely on 15 yr old computers.

```
$ inxi -FG
```
output would be helpful. Please.  And please use "code tags", like I have above.

---

### Post by QwUo173Hy on 2018-02-06
Thanks TheFu. Unity might be a hog, but I wouldn't have expected it to affect boot time for example.

I've attached the output of inxi and I'm very curious what you think of the output!
[ATTACH]278459[/ATTACH]

---

### Post by TheFu on 2018-02-06
That is a very low-end computer.  My first chromebook, Acer C720, was faster.
You definitely need to run a lite-Ubuntu GUI.  Definitely.

I appears to have 3G of RAM with about 256MB stolen for the iGPU.  Adding more RAM would be a good idea, if it is cheap.  The sad thing is that the CPU is designed for a low-end netbook and a used laptop for $75 would be 2x faster.   Just for fun, searched ebay ... [https://www.ebay.com/itm/Toshiba-CB35-A3120-Chromebook-13-3-1-4GHz-4GB-16GB-SSD-Laptop/401487727861](https://www.ebay.com/itm/Toshiba-CB35-A3120-Chromebook-13-3-1-4GHz-4GB-16GB-SSD-Laptop/401487727861) - $40.  It has a nice Celeron 2995U (1500 ~ passmark), 4G of RAM and 768p screen.  Just sayin'.  Heck, I'm tempted.  Toshiba made A, B, and C models.  A's have the nice celeron.  C's have good CPUs and 1080p screen too.  B's were in that time where Intel was making bad CPUs for netbooks/chromebooks. Avoid the "B" models.  I'm running Ubuntu+Openbox on my C model now. 

Using passmark scores for CPU-to-CPU comparisons. It isn't perfect, but close enough for general purpose users.  I've found that anything less than 1500 provides a not-good desktop experience using a lite-Linux, like XFCE, LXDE or Mate DEs.

BTW, I didn't look at the SVG file - don't have a way to view that type of file and remember [something about viruses]("http://www.securityweek.com/cybercriminals-use-svg-files-distribute-ransomware") coming with those files. ;(

I'm a mainly shell-only user, BTW.  I'm always going to prefer a lighter desktop. I don't actually use any DE myself, prefer the window-manager only setup. Find most DEs to be too bloated.

Some others thought their startups were long too:
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)  shows the longest processes and a few ideas for limiting how long they might take.

---

### Post by oldfred on 2018-02-06
If you add some parameters the redirected inxi report is more readable.

 Debian command line tool for system data
[https://packages.debian.org/sid/misc/inxi](https://packages.debian.org/sid/misc/inxi)
inxi -b
Summary hardware info
inxi -Fxz
Need -c 0 on redirect to eliminate extra ASCII chars.
inxi -Fxz -c 0 > inxi_list.txt

---

### Post by QwUo173Hy on 2018-02-06
[ATTACH]278464[/ATTACH]
Thanks guys. I've attached updated inxi with better formatting and other options :)

I'm interested in feedback on the bootchart. Once I'm finally logged in everything is acceptable, if not fast. :)

---

### Post by oldfred on 2018-02-06
I have never understood boot chart.

What does this show?
       fred@Z170N:~$ systemd-analyze 
Startup finished in 2.435s (kernel) + 8.703s (userspace) = 11.139s 

And this:

 echo $XDG_SESSION_TYPE 



On my old laptop with 1.5GB of RAM, Ubuntu with Unity was very slow.
So I install "fallback", "flashback", gnome-panel or whatever they call it now.
It is a gui like the old gnome2 with menu and top & bottom panels. My old system had 4:3 monitor and Unity with panel on side used valuable space. Laptop had space on sides, but I wanted same configuration.
gnome-panel still works in my tests install of 18.04.

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

---

### Post by QwUo173Hy on 2018-02-06
$ systemd-analyze 
Startup finished in 5.302s (kernel) + 42.879s (userspace) = 48.182s

$ echo $XDG_SESSION_TYPE
x11

A lot must have changed between 14.04 and 16.04 for the system to have regressed so much. Although I suspect a clean install would make a difference. Unfortunately it's not an option.

I'll consider an alternate desktop, but he's used to Unity and likes it so he might prefer to put up with the slowness than change.

---

### Post by TheFu on 2018-02-06
The main thing that changed in 16.04 is systemd.  It was supposed to make things faster.  I haven't seen that myself.

A few reference points from **systemd-analyze**:
```
Core i3/Chromebook: Startup finished in 13.425s (kernel) + 3.058s (userspace) = 16.483s
Pentium G3258: Startup finished in 3.192s (kernel) + 44.773s (userspace) = 47.965s
Core i7: Startup finished in 7.538s (kernel) + 28.200s (userspace) = 35.738s
Core i5: Still running 14.04 (no systemd)
Desktop running inside Core i5 VM: Startup finished in 2.083s (kernel) + 18.411s (userspace) = 20.495s
Raspberry Pi v2: Startup finished in 6.353s (kernel) + 14.009s (userspace) = 20.363s

```
The i5 and i7 are 1st generation ~ from 2010. The VM is fastest for a few reasons. Mainly because there isn't any GUI.

I don't reboot very often, perhaps every 3 weeks or so. Startup time isn't a big deal to me. If I rebooted 2+ times a day, I might care more.

---

### Post by QwUo173Hy on 2018-02-08
I'm seeing the kernel take 5 seconds, then systemdtake 5 seconds. And that's before any parallel processing kicks in, as per my bootchart attached above.

---

