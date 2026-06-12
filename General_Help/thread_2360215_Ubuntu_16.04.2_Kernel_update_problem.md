---
title: "Ubuntu 16.04.2 Kernel update problem"
date: 2017-05-02
forum: General Help
---

### Post by ordak on 2017-05-02
Hi,

I used to update my Ubuntu on an ASUS laptop, using terminal commands:

sudo apt update
sudo apt upgrade

without problems. Last time I used Ubuntu update-manager. It downloaded a new Kernel, maybe incomplete, after the restart my computer gets into a login screen. I can not access the Internet on this laptop, as it shows "No network devices available".

the command "sudo uname -r" shows:
4.4.0-77-generic

---

### Post by Impavidus on 2017-05-02
Reverting an update isn't easy, but in case of kernel upgrades (which  are the most likely to give problems), the old kernel isn't uninstalled  automatically. If you get to the grub menu, you can use the advanced options and boot an older kernel. It may be fixed with the next upgrade.

Interestingly, I found someone with a very similar problem: [https://ubuntuforums.org/showthread.php?t=2360216](https://ubuntuforums.org/showthread.php?t=2360216)

---

### Post by mago90 on 2017-05-02
Hi as Impavidus says I had a very similar issue which I fixed by reverting (via grub) to  4.4.0-75-generic. Indeed seems that 4.4.0-77-generic causes internet issues on the latests Ubuntu 16.04.02

---

### Post by ajgreeny on 2017-05-02
@ mago90
Have you files that bug yet?  If not it may be very helpful to you and others to do so as quickly as possible.

---

### Post by jsalisbury2 on 2017-05-02
There is a bug opened for this issue here:
  [http://pad.lv/1687623](http://pad.lv/1687623)

---

### Post by ordak on 2017-05-03
> **mago90 said:**
> Hi as Impavidus says I had a very similar issue which I fixed by reverting (via grub) to  4.4.0-75-generic. Indeed seems that 4.4.0-77-generic causes internet issues on the latests Ubuntu 16.04.02

I reverted back to 4.4.0-75-generic kernel also, and it seems, things work fine for now.

---

### Post by ajgreeny on 2017-05-03
If you have got back wifi or connection via ethernet, update again using either terminal or synaptic.

That bug suggests that it is update-manager only that is the cause of the problem as it is not installing the linux-image-extra or the linux-header packages needed.

---

### Post by A4Skyhawk on 2017-05-03
I had similar issues as described above after upgrading to 4.4.0-77.  Running sudo apt-get update and  
sudo apt-get upgrade fixed the problems.

---

### Post by Keith_Helms on 2017-05-03
I don't want to nitpick, but I believe 16.04.2 uses the 4.8 kernel series.  You must really be on 16.04 or 16.04.1

---

### Post by A4Skyhawk on 2017-05-03
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

:~$ cat /proc/version
Linux version 4.4.0-77-generic (buildd@lgw01-59) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #98-Ubuntu SMP Wed Apr 26 08:34:02 UTC 2017

---

### Post by alessandro38 on 2017-05-04
I had the same issue and I solved it booting from the previous kernel version, 4.4.0-75. But if I had removed the previous packages (like running sudo apt autoremove) how could I revert to a previous working kernel?

It's not my actual situation, fortunately, but I'd like to know just in case.

---

### Post by Impavidus on 2017-05-04
> **Keith_Helms said:**
> I don't want to nitpick, but I believe 16.04.2 uses the 4.8 kernel series.  You must really be on 16.04 or 16.04.1If you have a fresh install of 16.04.2, you have kernel 4.8. But if you have a properly upgraded 16.04 or 16.04.1, you get to version 16.04.2 even if you still run kernel 4.4.

> **alessandro38 said:**
> I had the same issue and I solved it booting from the previous kernel version, 4.4.0-75. But if I had removed the previous packages (like running sudo apt autoremove) how could I revert to a previous working kernel?

It's not my actual situation, fortunately, but I'd like to know just in case.

apt autoremove always keeps one old kernel.

---

### Post by hans12345 on 2017-05-20
I have been watching this thread hoping there would be a simple set of instructions that I could follow to upgrade.

Like others here, I have updated via the standard path to 4.4.0-77, and it is "bugged" - no network etc.
So, like others, I power up and in grub go to previous versions and boot with  4.4.0-75. 
This has been going on for around 3 weeks.

How do I update now?

If the "bug" is fixed, can I just do a normal update? 
Do I need to remove the faulty  4.4.0-77 first?
Do I need to work via the terminal?

Your help requested.

---

### Post by deadflowr on 2017-05-20
> How do I update now?
There is newer stable kernel out 4.4.0-78
> If the "bug" is fixed, can I just do a normal update? 
maybe fixed, maybe not fixed, and yes try a normal update first.
> Do I need to remove the faulty 4.4.0-77 first?
No, but you can if you want, doesn't affect the outcome of installing a new kernel.
> Do I need to work via the terminal?

If the regular gui software updater ( I assume that's what you would be calling a normal update) doesn't pull in the new kernel, then use the terminal.
Terminal commands
```
sudo apt update
sudo apt full-upgrade
```
this should pull in and install the 4.4.0-78 kernel.

---

### Post by JKyleOKC on 2017-05-20
> **Keith_Helms said:**
> I don't want to nitpick, but I believe 16.04.2 uses the 4.8 kernel series.  You must really be on 16.04 or 16.04.1I ran into that confusion myself about 10 days ago. There has been a change in the way kernels get updated, and as a result my 16.04.1 clean install uses a 4.4.77 kernel while the 16.04.2 clean install on the other box has a much later one in the 4.8 series, same as 16.10 or maybe 17.04! It's quite confusing!

---

### Post by Kris_M on 2017-05-20
My problem is that I am on 16.04.2 and I still have a bunch of kernels:
4.8 52
4.8 51
4.4 78
4.4 77
4.8 49
4.8 45
And when a new one comes along it does not update grub and I have to do that manually.
How can I simplify this (like maybe getting rid of all but the last 2)?

---

### Post by A4Skyhawk on 2017-05-20
[**[COLOR=#000000]@hans12345[/COLOR]**]("https://ubuntuforums.org/member.php?u=356071") Try the steps that I mentioned in post #8 - worked for me.  I now, when notified of new updates, use the terminal commands (sudo apt-get update/sudo apt-get upgrade/sudo apt-get dist-upgrade/sudo apt-get autoremove) instead of the gui.

---

### Post by hans12345 on 2017-05-21
> **deadflowr said:**
> There is newer stable kernel out 4.4.0-78

maybe fixed, maybe not fixed, and yes try a normal update first.

No, but you can if you want, doesn't affect the outcome of installing a new kernel.

If the regular gui software updater ( I assume that's what you would be calling a normal update) doesn't pull in the new kernel, then use the terminal.
Terminal commands
```
sudo apt update
sudo apt full-upgrade
```
this should pull in and install the 4.4.0-78 kernel.

Thanks Deadflower.

The standard update (the regular gui software updater) worked perfectly without any special steps.

---

