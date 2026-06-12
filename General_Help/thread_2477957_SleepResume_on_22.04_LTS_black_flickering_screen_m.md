---
title: "Sleep/Resume on 22.04 LTS: black flickering screen must shutdown"
date: 2022-08-12
forum: General Help
---

### Post by ddkn on 2022-08-12
Hello,

(First time poster!) I just got a new Lenovo T14 Gen 3 Inteli7-1260, and the sleep resume seems to be having an issue. Everything else works great while running Kubuntu 22.04 LTS. When the system goes into sleep (button press or lid closure), and wakes up it has a pitch black screen for a few seconds, then a black screen with a mouse for a few seconds, and repeats indefinitely while heating up.

I have tried several solutions on the forums here,


[LIST=1]
[*]    Upgrade kernel from 5.15 -> 5.17-oem 
[*]    set GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" 
[*]    Enable/disable TLP security chip 
[*]    Change Sleep from Linux S3 to Windows+Linux a few times 
[*]    Upgrade to mainline kernels 5.18.15 and 5.19 
[*]    plasma-workspace-wayland 
[/LIST]


I would really like to have the sleep/resume working if possible, so far I have just changed the lid closure to lock the screen.

Does anyone have any suggestions? Or something I may be overlooking? I am attaching my [cpuinfo]("https://pastebin.ubuntu.com/p/f72v9vtPwn/") and [dmesg]("https://pastebin.ubuntu.com/p/gv3r8KMdcH/").

Thanks!

---

### Post by ddkn on 2022-08-14
Latest attempt was using the latest 5.19.1 kernel. I noticed that there was issues with missing i915 files missing. I therefore checked out [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/), and copied the latest **i915** folder to **/lib/firmware** by

```

$ sudo su
$ sudo mainline --install 5.19.1
$ cd ~/tmp
$ git clone [URL="https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/"]https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/
[/URL]$ cd /lib/firmware
$ cp -r i915 i915.orig
$ cp -r ~/tmp/linux-firmware/i915 .
$ update-initramfs -u -k all

```

Unfortunately it seems that nothing has changed. I did notice that my system is not detecting external monitors either. On any of the 5.{15,17,18.15,19.0,19.1} kernels.

---

### Post by dcollect on 2022-08-17
I understand Wayland is the default on 22.04.  I did an in-place upgrade from 20.04 and ***my*** default was the X11.  I noticed the same behavior you are experiencing on a recent Dell Precision 5500 when I ran the Wayland windowing system.  There  With the tested Nvidia driver and the older X.org 22.04 is reliable.  Hope this helps.

Also,
>bump

---

### Post by ddkn on 2022-08-22
Hi @dcollect (sorry for the late reply as I wasn't on this computer for a few days),

On KDE I believe X11 was default for 22.04 LTS? When I checked I only have X11 installed. I tried installing wayland with no change, but that was on kernel 5.15 (I can check when I get home from work if there is a difference). This morning I had a Lenovo firmware update but nothing changed on that front.

```
[FONT=monospace][COLOR=#000000]$ loginctl show-session $(loginctl | grep $(whoami) | awk '{print $1}') -p Type[/COLOR]
Type=x11[/FONT]
```

I may contact the kernel mailing list if they know of any issues this week, but perhaps this is more of a x11/wayland issue?

---

### Post by ddkn on 2022-08-23
So I installed **plasma-workspace-wayland**. I got a flickering screen when going to _sleep_ from the startmenu, but the login screen was now visible during flickers. No mouse movement while visible, but the mouse would be in a different location if I moved during a black screen. After a while I got this error message, 

[IMG]https://user-images.githubusercontent.com/13819239/186229785-b3ea91da-c468-4b5b-a576-830e8d4273e1.png[/IMG]

So no luck yet.

---

### Post by ddkn on 2022-09-01
A further update, I noticed that my system BIOS allows me to select sleep states **S1** and **S3**, however my system doesn't support these states,

```
[FONT=monospace][COLOR=#000000]$ sudo dmesg | grep ACPI | grep S[012345] [/COLOR]
[    0.471473] ACPI: PM: (supports [COLOR=#ff5454]**S0**[/COLOR][COLOR=#ff5454]** S4 **[/COLOR][COLOR=#ff5454]**S5**[/COLOR][COLOR=#000000])[/COLOR][/FONT]
```

I have seen here [https://www.reddit.com/r/linuxhardware/comments/i28nm5/ideapad_14are05_s3_sleep_fix/](https://www.reddit.com/r/linuxhardware/comments/i28nm5/ideapad_14are05_s3_sleep_fix/) that someone has added it in for an ideapad. Has anyone tried this? or have a suggestion in the same vein?

---

### Post by miguel001 on 2022-09-01
The sleep state shouldn't be the way to fix it anyway. Its up to the distro and the GPU driver etc to deal with getting the OS visible and working again to the user. Sometimes they get frustrating bugs there. Though sometimes its side effect of user created depending on how the GPU driver is installed or whatever. The kernel might cause it as well at times.

I wouldn't be concerned all that much about the states there. You could play around with it but there's a lot of possibilities as to why a black screen can appear on resume that shouldn't be solved by the user through those settings. Like the screen locker that should not be the way to fix it lol.

---

### Post by ddkn on 2022-11-09
Just to update, I had a Lenovo Bios update in 22.04 today. This upgraded the bios which has both fixed HDMI out and Sleep. Now the laptop works as expected! FYI I am on the kernel 5.19.3.  So, I believe for my processor i7-1260P, the laptop works as expected. I am updating the title to reflect this.

---

