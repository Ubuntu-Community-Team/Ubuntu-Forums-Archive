---
title: "I'm on Ubuntu 22.04, after a simple update I now can't login, it's glitched."
date: 2023-01-21
forum: General Help
---

### Post by SpaceManJack on 2023-01-21
Please go read my comment down below &#8595;&#8595;&#8595;

---

### Post by Impavidus on 2023-01-21
1 GB is huge. Kernel updates or updates to large packages like LibreOffice can be around 100 MB, but I've never encountered an update of a gigabyte. Unless this was the first after installation or you hadn't updated in half a year or there was something wrong with your software sources for a long time and you just fixed it.

Updates can break Ubuntu, but it's rare. It happened to me just once and I've been using Ubuntu since 2006.

Can you access the grub menu and boot Ubuntu in recovery mode, then proceed to a graphical login? That will load Ubuntu with the open source graphics drivers. It could be that your graphics drivers have turned into a problem. Or can you use the grub menu to boot Ubuntu using an older kernel?

Can you tell a bit more about your graphics hardware? There have been some reports lately about problems with proprietary nvidia drivers. If you can access the filesystem of your installed system, either by booting it or via a live disk, you can have a look at the log files to see what packages were updated: /var/log/dpkg.log. Other log files may also give some clues, but I can't tell what exact line you have to look for.

There are bugs, sure. Some are small glitches that don't affect usability, some are nasty. Some are visible, some are invisible. The invisible ones are more dangerous. Sometimes new users think something is a bug, but actually the system did exactly as requested. Linux doesn't protect the user the way Windows does. I don't know if that's the case for you.

---

### Post by SpaceManJack on 2023-01-22
I truly believe an update broke my computer, and I'd like to know why? I  really didn't do much with my computer, I don't think I'm at fault for  this, everything was fine til this update came along.

I'm on Ubuntu 22.04. I'm using a PC built in 2015. So my Ubuntu hadn't  updated my computer in probably about 2 weeks, then about a few days ago  it said I needed an update and it was a 1GB update, it was just under a  GB as i remember. So I said sure go ahead and update. Right away I  could tell there was something wrong as it kept asking for my  administrator password over and over again as it was updating.

Then it switched to this menu and again, asked me to update. Look. I  took this screenshot at the time, so this screenshot is from a few days  ago when this was all happening to me. I added up all those little  updates, and it equals just over 1GB in total. 

[https://ubuntuforums.org/attachment.php?attachmentid=291606&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=291606&stc=1)

[https://ubuntuforums.org/attachment.php?attachmentid=291607&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=291607&stc=1)

[URL="https://askubuntu.com/posts/1451316/timeline"]

So it would update and then come right back to the update menu and ask  me if I wanted to update, and it did this over and over again, and after  about 7 or 8 times of doing this I just gave up and turned my computer  off.

Now after turning my computer off, I turned it back on. Now my computer  is fully encrypted using LUKS. So after I enter in my password and  decrypt the system it takes me to this screen. Look.[/URL]

[https://i.stack.imgur.com/hnrT6.jpg](https://i.stack.imgur.com/hnrT6.jpg) 
[https://i.stack.imgur.com/wRktb.jpg](https://i.stack.imgur.com/wRktb.jpg)

And then it goes to a black screen with a blinking dash in the upper  left hand corner of the screen, and it'll remain like this forever. So I  couldn't log into my computer, that update broke my computer.

But I did some tinkering and I figured out how to get into my computer. I  have to go to the GNU GRUB menu and I have to click on the "Ubuntu  advanced options" and then go into the command line, and then go back  into "Ubuntu advanced options" and just kinda do this back and forth,  and then hit "*Ubuntu". And it takes me to this login screen. If I can  get this login screen (instead of the normal one with the huge orange  Ubuntu symbol) I can successfully get into my computer.

[https://i.stack.imgur.com/teGfL.jpg](https://i.stack.imgur.com/teGfL.jpg)

So I can now get back into my computer but the screen tearing, which I  had fixed before, has come back and the sound doesn't work, so my  computer is clearly messed up. So I've backed up the files I wanted to  backup and now I'm going to do a fresh clean install of 22.04 LTS.

That was the main thing, I just wanted to at least get back into my computer so I could backup some files.

And yes the update really was 1GB. I really wanted to let the community  know what happened to me, cause this really happened to me. This weird  update broke my computer. And look at how I can get back into my  computer, look how weird that is. Ok well now that my files are backed  up I'm going to do a clean install of Ubuntu. If I ever get another 1GB  update I'll immediately come here and let you guys know about it.

p.s. Just to clarify with you all. If I get this login screen, it will not let me get into my computer.

[https://i.stack.imgur.com/D2YZ0.jpg](https://i.stack.imgur.com/D2YZ0.jpg)

p.s. So yeah just to clarify. You know how when you log into Ubuntu sometimes it will prompt you letting you know that there's an update available? Well that's what happened a few days ago, and I said, sure go ahead and update. I knew right away something was wrong because it kept asking for my administrator password as it was updating. And I'm sure some of you will place the blame on me saying I was installing kernels or I was customizing my computer. While I know more about computers than your average Joe I'm certainly not a computer expert, in fact I don't even know what a kernel is exactly lol, I'm a total novice when it comes to Linux. 

I will say this. Before I was using 22.04LTS I was using 20.04LTS. But keep in mind I've only been using Linux for just over a year now (I was a lifelong Windows user), so, I first installed 20.04LTS back in September of 2021, but 20.04 came out in April of 2020 which means 20.04 had been out for about a year and a half when I installed it on my computer. And while I had bugs on 20.04 I never had a system breaking bug like this. So I've learned my lesson from this. When they release 24.04LTS I won't be installing it til it's been out for at least 1 year. And I'll be doing a fresh clean install as I learned my lesson from that as well lol, I did the upgrade from 20.04 to 22.04 and right away it was full of bugs, I mean it was glitched, so from now on I only do clean installs.

[B]Edit:

[/B]So I checked my apt logs and bingo, you can see what happened on Jan.  19, 2023. You'll see that on Jan. 19 it kept trying to update over and  over again, and that's exactly what happened, it just kept asking me to  update over and over again, til I decided to turn my computer off. On  Jan. 21 is when I finally figured out how to get back into my computer  as you'll see.

Here's the output of ```
less /var/log/apt/history.log
```
[B] 
```
  

Start-Date: 2023-01-17  20:37:24
Commandline: /usr/bin/unattended-upgrade
Install: linux-headers-5.15.0-58-generic:amd64 (5.15.0-58.64, automatic), linux-modules-5.15.0-58-generic:amd64 (5.15.0-58.64, automatic), linux-modules-extra-5.15.0-58-generic:amd64 (5.15.0-58.64, autom
atic), linux-headers-5.15.0-58:amd64 (5.15.0-58.64, automatic), linux-image-5.15.0-58-generic:amd64 (5.15.0-58.64, automatic)
Upgrade: linux-image-generic-hwe-22.04:amd64 (5.15.0.57.55, 5.15.0.58.56), linux-headers-generic-hwe-22.04:amd64 (5.15.0.57.55, 5.15.0.58.56), linux-generic-hwe-22.04:amd64 (5.15.0.57.55, 5.15.0.58.56)
End-Date: 2023-01-17  20:38:52

Start-Date: 2023-01-17  20:38:57
Commandline: /usr/bin/unattended-upgrade
Upgrade: vim-common:amd64 (2:8.2.3995-1ubuntu2.1, 2:8.2.3995-1ubuntu2.3), vim-tiny:amd64 (2:8.2.3995-1ubuntu2.1, 2:8.2.3995-1ubuntu2.3)
End-Date: 2023-01-17  20:39:09

Start-Date: 2023-01-17  20:39:14
Commandline: /usr/bin/unattended-upgrade
Install: linux-signatures-nvidia-5.15.0-58-generic:amd64 (5.15.0-58.64, automatic), linux-modules-nvidia-525-5.15.0-58-generic:amd64 (5.15.0-58.64, automatic), linux-objects-nvidia-525-5.15.0-58-generic:amd64 (5.15.0-58.64, automatic)
Upgrade: linux-modules-nvidia-525-generic-hwe-22.04:amd64 (5.15.0-57.63+1, 5.15.0-58.64)
End-Date: 2023-01-17  20:39:55

Start-Date: 2023-01-17  20:40:00
Commandline: /usr/bin/unattended-upgrade
Upgrade: libxpm4:amd64 (1:3.5.12-1build2, 1:3.5.12-1ubuntu0.22.04.1)
End-Date: 2023-01-17  20:40:02

Start-Date: 2023-01-17  20:40:07
Commandline: /usr/bin/unattended-upgrade
Upgrade: xxd:amd64 (2:8.2.3995-1ubuntu2.1, 2:8.2.3995-1ubuntu2.3)
End-Date: 2023-01-17  20:40:10

Start-Date: 2023-01-17  20:40:15
Commandline: /usr/bin/unattended-upgrade
Remove: linux-modules-extra-5.15.0-56-generic:amd64 (5.15.0-56.62)
End-Date: 2023-01-17  20:40:22

Start-Date: 2023-01-17  20:40:26
Commandline: /usr/bin/unattended-upgrade
Remove: linux-signatures-nvidia-5.15.0-56-generic:amd64 (5.15.0-56.62+1), linux-modules-5.15.0-56-generic:amd64 (5.15.0-56.62), linux-modules-nvidia-525-5.15.0-56-generic:amd64 (5.15.0-56.62+1), linux-image-5.15.0-56-generic:amd64 (5.15.0-56.62)
End-Date: 2023-01-17  20:40:36

Start-Date: 2023-01-17  20:40:40
Commandline: /usr/bin/unattended-upgrade
Remove: linux-objects-nvidia-525-5.15.0-56-generic:amd64 (5.15.0-56.62+1)
End-Date: 2023-01-17  20:40:41

Start-Date: 2023-01-17  20:40:46
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-5.15.0-56-generic:amd64 (5.15.0-56.62)
End-Date: 2023-01-17  20:40:48

Start-Date: 2023-01-17  20:40:53
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-5.15.0-56:amd64 (5.15.0-56.62)
End-Date: 2023-01-17  20:40:56

Start-Date: 2023-01-19  01:46:42
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Install: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), gcc-11:amd64 (11.3.0-1ubuntu1~22.04, automatic), gcc-12:amd64 (12.1.0-2ubuntu1~22.04, automatic), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), libtsan0:amd64 (11.3.0-1ubuntu1~22.04, automatic), libtsan2:amd64 (12.1.0-2ubuntu1~22.04, automatic), gcc:amd64 (4:11.2.0-1ubuntu1, automatic), dctrl-tools:amd64 (2.24-3build2, automatic), libcc1-0:amd64 (12.1.0-2ubuntu1~22.04, automatic), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), dpkg-dev:amd64 (1.21.1ubuntu2.1, automatic), libasan6:amd64 (11.3.0-1ubuntu1~22.04, automatic), libasan8:amd64 (12.1.0-2ubuntu1~22.04, automatic), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-image-6.1.0-1004-oem:amd64 (6.1.0-1004.4, automatic), make:amd64 (4.3-4.1build1, automatic), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), lto-disabled-list:amd64 (24, automatic), linux-modules-5.15.0-58-lowlatency:amd64 (5.15.0-58.64, automatic), cpp-12:amd64 (12.1.0-2ubuntu1~22.04, automatic), libitm1:amd64 (12.1.0-2ubuntu1~22.04, automatic), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-image-5.15.0-58-lowlatency:amd64 (5.15.0-58.64, automatic), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-objects-nvidia-525-5.15.0-58-lowlatency:amd64 (5.15.0-58.64+1, automatic), linux-signatures-nvidia-5.15.0-58-lowlatency:amd64 (5.15.0-58.64+1, automatic), linux-modules-6.1.0-1004-oem:amd64 (6.1.0-1004.4, automatic), libubsan1:amd64 (12.1.0-2ubuntu1~22.04, automatic), liblsan0:amd64 (12.1.0-2ubuntu1~22.04, automatic), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-objects-nvidia-525-6.1.0-1004-oem:amd64 (6.1.0-1004.4+1, automatic), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic), libgcc-11-dev:amd64 (11.3.0-1ubuntu1~22.04, automatic), linux-signatures-nvidia-6.1.0-1004-oem:amd64 (6.1.0-1004.4+1, automatic), dkms:amd64 (2.8.7-2ubuntu2.1, automatic), libgcc-12-dev:amd64 (12.1.0-2ubuntu1~22.04, automatic)
Upgrade: openssh-client:amd64 (1:8.9p1-3, 1:8.9p1-3ubuntu0.1), libglx-mesa0:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), libglx-mesa0:i386 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), libpipewire-0.3-common:amd64 (0.3.48-1ubuntu2, 0.3.48-1ubuntu3), libgbm1:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), grub-pc-bin:amd64 (2.06-2ubuntu7, 2.06-2ubuntu7.1), software-properties-common:amd64 (0.99.22.3, 0.99.22.4), pipewire:amd64 (0.3.48-1ubuntu2, 0.3.48-1ubuntu3), python3-software-properties:amd64 (0.99.22.3, 0.99.22.4), libxatracker2:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), python-apt-common:amd64 (2.3.0ubuntu2.1, 2.4.0), mesa-va-drivers:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), libgl1-mesa-dri:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), libgl1-mesa-dri:i386 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), gstreamer1.0-pipewire:amd64 (0.3.48-1ubuntu2, 0.3.48-1ubuntu3), mesa-vulkan-drivers:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), mesa-vulkan-drivers:i386 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), python3-apt:amd64 (2.3.0ubuntu2.1, 2.4.0), software-properties-gtk:amd64 (0.99.22.3, 0.99.22.4), pipewire-bin:amd64 (0.3.48-1ubuntu2, 0.3.48-1ubuntu3), grub2-common:amd64 (2.06-2ubuntu7, 2.06-2ubuntu7.1), libglapi-mesa:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), libglapi-mesa:i386 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), libspa-0.2-modules:amd64 (0.3.48-1ubuntu2, 0.3.48-1ubuntu3), grub-common:amd64 (2.06-2ubuntu7, 2.06-2ubuntu7.1), sudo:amd64 (1.9.9-1ubuntu2.1, 1.9.9-1ubuntu2.2), libegl-mesa0:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), libpipewire-0.3-modules:amd64 (0.3.48-1ubuntu2, 0.3.48-1ubuntu3), mesa-vdpau-drivers:amd64 (22.0.5-0ubuntu0.1, 22.0.5-0ubuntu0.3), grub-pc:amd64 (2.06-2ubuntu7, 2.06-2ubuntu7.1), libpipewire-0.3-0:amd64 (0.3.48-1ubuntu2, 0.3.48-1ubuntu3)
End-Date: 2023-01-19  01:52:54

Start-Date: 2023-01-19  01:53:49
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Remove: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-headers-5.15.0-57-generic:amd64 (5.15.0-57.63), linux-modules-nvidia-525-5.15.0-57-generic:amd64 (5.15.0-57.63+1), linux-modules-5.15.0-57-generic:amd64 (5.15.0-57.63), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-modules-extra-5.15.0-57-generic:amd64 (5.15.0-57.63), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-objects-nvidia-525-5.15.0-57-generic:amd64 (5.15.0-57.63+1), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-headers-5.15.0-57:amd64 (5.15.0-57.63), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1), linux-signatures-nvidia-5.15.0-57-generic:amd64 (5.15.0-57.63+1), linux-image-5.15.0-57-generic:amd64 (5.15.0-57.63)
End-Date: 2023-01-19  01:54:54

Start-Date: 2023-01-19  01:55:13
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Install: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic)
End-Date: 2023-01-19  01:57:45

Start-Date: 2023-01-19  01:58:03
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Remove: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1)
End-Date: 2023-01-19  01:58:42

Start-Date: 2023-01-19  01:59:49
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Install: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic)
End-Date: 2023-01-19  02:02:14

Start-Date: 2023-01-19  02:03:08
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Remove: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1)
End-Date: 2023-01-19  02:03:48

Start-Date: 2023-01-19  02:04:46
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Install: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic)
End-Date: 2023-01-19  02:07:13

Start-Date: 2023-01-19  02:07:55
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Remove: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1)
End-Date: 2023-01-19  02:08:33

Start-Date: 2023-01-19  02:10:01
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Install: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1, automatic), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27, automatic), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33, automatic), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28, automatic), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10, automatic), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1, automatic), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1, automatic), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1, automatic)
End-Date: 2023-01-19  02:12:16

Start-Date: 2023-01-19  02:13:10
Commandline: aptdaemon role='role-commit-packages' sender=':1.112'
Remove: linux-modules-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-signatures-nvidia-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-objects-nvidia-525-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28+1), linux-image-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-image-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-image-5.17.0-1026-oem:amd64 (5.17.0-1026.27), linux-modules-5.15.0-1027-oracle:amd64 (5.15.0-1027.33), linux-modules-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-image-5.15.0-1023-intel-iotg:amd64 (5.15.0-1023.28), linux-modules-6.0.0-1010-oem:amd64 (6.0.0-1010.10), linux-objects-nvidia-525-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-objects-nvidia-525-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-6.0.0-1010-oem:amd64 (6.0.0-1010.10+1), linux-signatures-nvidia-5.17.0-1026-oem:amd64 (5.17.0-1026.27+1), linux-signatures-nvidia-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1), linux-objects-nvidia-525-5.15.0-1027-oracle:amd64 (5.15.0-1027.33+1)
End-Date: 2023-01-19  02:13:40

Start-Date: 2023-01-21  21:35:26
Commandline: /usr/bin/unattended-upgrade
Upgrade: libnvidia-fbc1-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-fbc1-525:i386 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-gl-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-gl-525:i386 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-extra-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), linux-signatures-nvidia-5.15.0-58-generic:amd64 (5.15.0-58.64, 5.15.0-58.64+1), nvidia-compute-utils-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), nvidia-driver-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-encode-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-encode-525:i386 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), nvidia-utils-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), xserver-xorg-video-nvidia-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), linux-modules-nvidia-525-5.15.0-58-generic:amd64 (5.15.0-58.64, 5.15.0-58.64+1), libnvidia-decode-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-decode-525:i386 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), nvidia-kernel-common-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), linux-objects-nvidia-525-5.15.0-58-generic:amd64 (5.15.0-58.64, 5.15.0-58.64+1), linux-modules-nvidia-525-generic-hwe-22.04:amd64 (5.15.0-58.64, 5.15.0-58.64+1), libnvidia-cfg1-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), nvidia-kernel-source-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-compute-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1), libnvidia-compute-525:i386 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1)
End-Date: 2023-01-21  21:38:22

Start-Date: 2023-01-21  21:38:26
Commandline: /usr/bin/unattended-upgrade
Upgrade: libnvidia-common-525:amd64 (525.60.11-0ubuntu0.22.04.1, 525.78.01-0ubuntu0.22.04.1)
End-Date: 2023-01-21  21:38:27
(END)









```

[/B]I might as well just include this. Here's a screenshot of "Advanced  options Ubuntu" in GNU GRUB. I'm just trying to provide as much info as  possible.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291700&stc=1[/IMG]

---

### Post by SpaceManJack on 2023-01-22
The red text was a glitch I have no idea why the text turned red, it just did for some reason, and I tried to fix it but I couldn't.

Actually some of the text might be blue for some viewers, on PC the text is red but here on my smartphone it's blue. Some of the text just turned red while I was typing it out and I couldn't figure out why, I think it might be a bug, but I'm not sure.

---

### Post by ajgreeny on 2023-01-23
Your problem seems to be a result of you choosing to use encryption which I do not use nor fully understand how best to use.

However, you must have made that choice at some point, probably during installation of 22.04 as it is never enabled by default in Ubuntu but is an installation option, so when you install this time do not enable encryption unless it is absolutely essential to you.

---

### Post by coffeecat on 2023-01-23
@scott130, I've merged two of your threads about the same problem into this thread here. A third - [https://ubuntuforums.org/showthread.php?t=2483183](https://ubuntuforums.org/showthread.php?t=2483183) - linking to askubuntu has already been closed by howefield. Please do not post multiple threads about the same problem. It causes confusion, dilutes community effort and offends forum members. Also, I note that the first thread - now comprising the first two posts in this thread - you had not revisited since starting it, despite there being a helpful response.      

I have edited your post above to reduce the huge off-site images to hyperlinks. Huge images are disrespectful to those few people still on limited bandwidth and to those using mobile devices. Please use the forum image attachment facility. In fact you did do so for two images, so I fail to understand why you linked to imgur for the others. 

> **scott130 said:**
> The red text was a glitch I have no idea why the text turned red, it just did for some reason, and I tried to fix it but I couldn't.

Actually some of the text might be blue for some viewers, on PC the text is red but here on my smartphone it's blue. Some of the text just turned red while I was typing it out and I couldn't figure out why, I think it might be a bug, but I'm not sure.

It is neither a glitch nor a bug. The red (or blue on a mobile device) text is a hyperlink that you created when composing your text. It links to an Askubuntu page. That you seem puzzled by it suggests that you created the hyperlink accidentally from inadvertent use of icons in the forum message editor toolbar.  Possibly you highlighted some text, and then accidentally clicked the link icon and pasted a url into that. In fact the hyperlink included one of your images, but I have tidied that up now. 

By the way, hyperlinks appear as dark orange (not red) on the standard forum skin, and blue on the mobile skin. That is why you saw two different colours on different devices. As I said, neither a glitch nor a bug. The forum software was behaving exactly as intended.

---

### Post by SpaceManJack on 2023-01-23
> **coffeecat said:**
> @scott130, I've merged two of your threads about the same problem into this thread here. A third - [https://ubuntuforums.org/showthread.php?t=2483183](https://ubuntuforums.org/showthread.php?t=2483183) - linking to askubuntu has already been closed by howefield. Please do not post multiple threads about the same problem. It causes confusion, dilutes community effort and offends forum members. Also, I note that the first thread - now comprising the first two posts in this thread - you had not revisited since starting it, despite there being a helpful response.      

I have edited your post above to reduce the huge off-site images to hyperlinks. Huge images are disrespectful to those few people still on limited bandwidth and to those using mobile devices. Please use the forum image attachment facility. In fact you did do so for two images, so I fail to understand why you linked to imgur for the others. 



It is neither a glitch nor a bug. The red (or blue on a mobile device) text is a hyperlink that you created when composing your text. It links to an Askubuntu page. That you seem puzzled by it suggests that you created the hyperlink accidentally from inadvertent use of icons in the forum message editor toolbar.  Possibly you highlighted some text, and then accidentally clicked the link icon and pasted a url into that. In fact the hyperlink included one of your images, but I have tidied that up now. 

By the way, hyperlinks appear as dark orange (not red) on the standard forum skin, and blue on the mobile skin. That is why you saw two different colours on different devices. As I said, neither a glitch nor a bug. The forum software was behaving exactly as intended.

My bad. I'm a novice when it comes to Linux to be honest. If I offended anyone sorry I'm a newbie.

Hey I tried to edit my post again, the one that says "Edit:", I need to add another image but when I'm all finished and click "edit" it takes me to a webpage that says I don't have permission to do that, do you know why?

---

### Post by SpaceManJack on 2023-01-23
Hey there should be 3 attached images but it's only saying 2 thumbnails are attached? Thats what I'm seeing I'm only seeing "2 attached thumbnails".

Can you guys see the pic below the text "I might as well just include this. Here's a screenshot of "Advanced   options Ubuntu" in GNU GRUB. I'm just trying to provide as much info as   possible."? I just wanna make sure it's showing up is all.

I think I've encountered a bug with the forum. It wouldn't let me edit the post in the advanced option, but would  let me successfully edit it in the stripped down version, does that make any sense? 

And yeah that orange text just appeared right after I uploaded a pic, I just started typing and the text was orange and I couldn't figure out why, I think its a bug.

---

### Post by SpaceManJack on 2023-01-23
> **ajgreeny said:**
> Your problem seems to be a result of you choosing to use encryption which I do not use nor fully understand how best to use.

However, you must have made that choice at some point, probably during installation of 22.04 as it is never enabled by default in Ubuntu but is an installation option, so when you install this time do not enable encryption unless it is absolutely essential to you.

I have to use encryption sorry. I prefer to be as safe as possible with my data.

---

### Post by SpaceManJack on 2023-01-24
Aren't there any Linux experts here who can assist me? I provided the apt logs, can you look at them for me?

---

### Post by SpaceManJack on 2023-01-25
Can anyone help me?

---

### Post by Impavidus on 2023-01-26
Your posts are very hard to follow.

Have you got good backups of your documents? You should alwys have those, but this is especially important on an encrypted drive, as there's no recovery when it gets damaged. Can you use a live disk to access the filesystem to create backups, if you need? When your documents are safe, nothing bad can happen.

It appears there was some packaging error recently for the proprietary nvidia drivers, which has messed up some systems with nvidia graphics. If you can still boot your system, at the very least to a command line, you could try to undo those changes. It won't be easy. Or, probably much faster, you could reinstall.

The way to prevent problems like this is to look carefully at the list of chages the software updater proposes and to cancel when something bad is about to happen. That's why many disable unattended upgrades.

---

### Post by SpaceManJack on 2023-01-26
> **Impavidus said:**
> Your posts are very hard to follow.

Have you got good backups of your documents? You should alwys have those, but this is especially important on an encrypted drive, as there's no recovery when it gets damaged. Can you use a live disk to access the filesystem to create backups, if you need? When your documents are safe, nothing bad can happen.

It appears there was some packaging error recently for the proprietary nvidia drivers, which has messed up some systems with nvidia graphics. If you can still boot your system, at the very least to a command line, you could try to undo those changes. It won't be easy. Or, probably much faster, you could reinstall.

The way to prevent problems like this is to look carefully at the list of chages the software updater proposes and to cancel when something bad is about to happen. That's why many disable unattended upgrades.

Thank you for taking the time to respond to me. How did you learn about the packaging error for the Nvidia drivers, where did you get this information? So this has happened to multiple people then?

And please go back to page 1 and check out the changes I made to my post to make it easier to understand? Just read what I said I explain in detail what happened to me.

Thanks.

---

### Post by Impavidus on 2023-01-27
Yes, there are several recent threads from people with somewhat similar problems with nvidia drivers. I didn't pay too much attention to them, as I've never used nvidia graphics.

---

### Post by ajgreeny on 2023-01-27
Have a read through this long thread which may give you some clues as to what is going on with your machine.
[https://ubuntuforums.org/showthread.php?t=2482558](https://ubuntuforums.org/showthread.php?t=2482558)

I always uninstall unattended-upgrades from my systems as I like to know exactly what's happening and not leave everything in the hands of the system, particularly when it comes to upgrades which, as in this case, have been shown to be potentially harmful.

---

### Post by #&amp;thj^% on 2023-01-27
Along with that link ajgreeny shows, there is this one:[https://ubuntuforums.org/showthread.php?t=2483319&p=14128058#post14128058](https://ubuntuforums.org/showthread.php?t=2483319&p=14128058#post14128058)
There are more as well.

---

### Post by SpaceManJack on 2023-01-28
> **1fallen said:**
> Along with that link ajgreeny shows, there is this one:[https://ubuntuforums.org/showthread.php?t=2483319&p=14128058#post14128058](https://ubuntuforums.org/showthread.php?t=2483319&p=14128058#post14128058)
There are more as well.

Hey thanks for helping me out.

I got a question for you cause I'm not sure, On page 1 can you see the image below the text that says "I might as well just include this. Here's a screenshot of "Advanced   options Ubuntu" in GNU GRUB. I'm just trying to provide as much info as   possible."? The reason I'm asking is because it's only showing 2 uploaded thumbnails on my end, when it should say 3 thumbnails, I uploaded 3 pictures.

You didn't ask for this but I thought it might help so here's the output of 
```
apt list --installed | grep linux-image
```

```
computer@computer:~$ apt list --installed | grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-5.15.0-58-generic/jammy-updates,jammy-security,now 5.15.0-58.64 amd64 [installed,automatic]
linux-image-5.15.0-58-lowlatency/jammy-updates,jammy-security,now 5.15.0-58.64 amd64 [installed,automatic]
linux-image-6.1.0-1004-oem/jammy-updates,jammy-security,now 6.1.0-1004.4 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,jammy-security,now 5.15.0.58.56 amd64 [installed,automatic]
computer@computer:~$ 


```

So I haven't actually done a clean install of Ubuntu just yet, because I'm wondering, so if I go ahead and do a clean install of 22.04LTS how do I know this bug won't happen again to me? Was it just bad luck that I ran into this nvidia packaging bug in the first place? And I'm seeing people say don't ever do an unattended update but honestly I'm a linux novice, I have to do unattended updates, I have no clue what the heck I'm even looking at lol. And my computer has an nvidia GTX 750 Ti so I have no choice but to use it.

Also you seem like you're a Linux expert, so what exactly happened to my computer? What exactly caused it to glitch out on me?

---

### Post by ajgreeny on 2023-01-29
I am not sure about that 6.1.0-1004 kernel which i do not have o my 22.04 installs all of which have the same 5.0.15-58 kernel as you, though not the low latency version you have also in the listed versions shown.

If you go to Advanced options in the grub menu and choose either of the 5.0 kernels does that allow you to login?

---

### Post by Impavidus on 2023-01-29
> **scott130 said:**
> 
I got a question for you cause I'm not sure, On page 1 can you see the image below the text that says "I might as well just include this. Here's a screenshot of "Advanced   options Ubuntu" in GNU GRUB. I'm just trying to provide as much info as   possible."? The reason I'm asking is because it's only showing 2 uploaded thumbnails on my end, when it should say 3 thumbnails, I uploaded 3 pictures.There are 2 images attached to the post, so 2 thumbnails. There are also links to external image hosting sites and you may have uploaded additional pictures, but those weren't attached to the post.
BTW, be careful with providing as much info as possible. You may end uploading the entire library of Alexandria, 99.99% of which is irrelevant and we can't sift through all of it.
> So I haven't actually done a clean install of Ubuntu just yet, because I'm wondering, so if I go ahead and do a clean install of 22.04LTS how do I know this bug won't happen again to me? Was it just bad luck that I ran into this nvidia packaging bug in the first place? And I'm seeing people say don't ever do an unattended update but honestly I'm a linux novice, I have to do unattended updates, I have no clue what the heck I'm even looking at lol. And my computer has an nvidia GTX 750 Ti so I have no choice but to use it.I have disabled unattended upgrades (by removing the entire unattended-upgrades package), but I let the system check automatically for updates every day and immediately show a pop-up when updates are available. So I get notified automatically, but I can review the list of proposed changes before agreeing.

In your case, kernel upgrades get pulled in by the linux-generic-hwe-22.04 package. The version number of that should match the version numbers of the new kernels that get pulled in, so that should be 5.15.0-58. The linux-image-6.1 therefore is a big red flag.
> 
Also you seem like you're a Linux expert, so what exactly happened to my computer? What exactly caused it to glitch out on me?
You have nvidia drivers installed. An update for those was available and installed, but the new version erroneously depended on the 6.1 kernel, which was automatically pulled in, but isn't ready for use on 22.04.

---

### Post by #&amp;thj^% on 2023-01-29
thanks to ajgreeny and Impavidus They seemed to have stated my view on the matter, with one unimportant difference, some of the kernels that were erroneously pulled in was an Oracle-Kernel. You don't seem effected by that one.
But I also agree that linux-image-6.1.0-1004-oem needs to be removed.
At this time I'm running all Devel/Repos and I'm using 5.19.0-21-generic
 and this Laptop has no Nvidia GPU, And another Laptop AMD and Nvidia, I've not had issues with any kernels.
This whole ordeal is kind of rare in my experience, I  wouldn't worry about it happening often.

---

### Post by SpaceManJack on 2023-01-31
Can someone please answer this for me?

On page 1 in my post, can you see the picture below this text "I might as well just include this. Here's a screenshot of "Advanced   options Ubuntu" in GNU GRUB. I'm just trying to provide as much info as   possible."?????

---

### Post by #&amp;thj^% on 2023-01-31
I don't do pictures, only copy and paste from terminal.
scott130 you seem resistant to remove the bad kernel and nvidia-driver.
If you can't follow our instructions, then we all set here in frustration.;)
for a dry run use this: (no changes will be made)
```
sudo apt-get purge linux-image-6.*  -s
```
This may help us but no pictures, just copy and paste the results back here in "code tags" please.
The same will need to be seen by us with Nvidia
```
sudo apt-get purge nvidia* -s
```

---

### Post by SpaceManJack on 2023-02-01
> **1fallen said:**
> I don't do pictures, only copy and paste from terminal.
scott130 you seem resistant to remove the bad kernel and nvidia-driver.
If you can't follow our instructions, then we all set here in frustration.;)
for a dry run use this: (no changes will be made)
```
sudo apt-get purge linux-image-6.*  -s
```
This may help us but no pictures, just copy and paste the results back here in "code tags" please.
The same will need to be seen by us with Nvidia
```
sudo apt-get purge nvidia* -s
```

Listen I'm a newbie when it comes to Linux. I'm not even going to try and rescue my computer, I'm just going to do a clean install of 22.04LTS.

So with that said. What are the chances of me running into this bug again? And I absolutely have to do unattended updates because like I said I'm a newbie. 

It's funny though because I actually know more about computers than your average person does, the average person basically only knows how to turn a computer on and browse the web and turn the computer off, that's it, that's basically what the average person knows about computers. Whereas I know how to take a computer and wipe the hard drive and install a different OS on it such as Linux, I even know how to get into the BIOS of a computer and change the boot sequence, I understand that when you delete a file from a computer it's not actually deleted at all, the only way to truly delete something is to take a program such as DBAN and literally wipe the entire hard drive. So I definitely know more about computers than the average person but I'm still a newbie compared to you guys, you guys are true computer experts.

I have to do unattended updates because I don't know what the heck I'm even looking at lol. And honestly it needs to be automated, if it isn't automated then it will drive the newbies back to Windows (Windows is where I came from), and Windows has the update process all automated, you must understand that not everyone is a computer expert like you guys are. In fact, the reason I even chose Ubuntu over the other Linux distros was because I was told Ubuntu was much more Windows-like than the other distros. It said on the internet that Windows users would be much more comfortable on Ubuntu than the other distros.

Thanks.

---

### Post by Impavidus on 2023-02-02
> **scott130 said:**
> Listen I'm a newbie when it comes to Linux. I'm not even going to try and rescue my computer, I'm just going to do a clean install of 22.04LTS.There's no shame in a clean install. It often is the easiest and fastest way to solve a nasty problem. And this is a particularly nasty problem. It's good you aren't scared for reinstalling; we encounter plenty of newbies who are so terrified by clean installs that they insist on fixing the problem, even when that's harder than a clean install.

> So with that said. What are the chances of me running into this bug again?Assuming this bug is gone from the repositories (I haven't checked; I don't really know about nvidia drivers), you won't run into this again. Really nasty upgrade bug like this pop up maybe once a year and never affect more than a small fraction of the users, so the probablity that you encounter another like it in the next five years isn't very large.

> And I absolutely have to do unattended updates because like I said I'm a newbie. The difference between doing unattended upgrades not not doing those is that in the latter case you'll get a pop-up sometimes where you can click "Install now". Just looking at the list of proposed updates will teach you more about the internals of Ubuntu. Once you learn what to expect of an update, you'll be able to recognise it when something's wrong. Then you can ask those friendly people at ubuntuforums if there's really something to worry about and if so, how to fix it.

---

### Post by #&amp;thj^% on 2023-02-03
> **scott130 said:**
> Listen I'm a newbie when it comes to Linux. I'm not even going to try and rescue my computer, I'm just going to do a clean install of 22.04LTS.
Ok and as said no shame in clean install.
> **scott130 said:**
> 
So with that said. What are the chances of me running into this bug again? And I absolutely have to do unattended updates because like I said I'm a newbie. 
again I agree with what is said, these things happen to any OS, even Windows, but rarely to they occur.
> **scott130 said:**
> 
 but I'm still a newbie compared to you guys, you guys are true computer experts.
once you get a little more comfortable with the terminal you will find it is your best friend. GUI's are just front ends to the terminal.
> **scott130 said:**
> 

I have to do unattended updates because I don't know what the heck I'm even looking at lol. And honestly it needs to be automated, if it isn't automated then it will drive the newbies back to Windows (Windows is where I came from), and Windows has the update process all automated, you must understand that not everyone is a computer expert like you guys are. In fact, the reason I even chose Ubuntu over the other Linux distros was because I was told Ubuntu was much more Windows-like than the other distros. It said on the internet that Windows users would be much more comfortable on Ubuntu than the other distros.

Thanks.
That's Ok we learn at our own pace.
I think you took offense at I don't do pictures, and most folks here feel the same on terminal or update pictures, it's just nicer to see a terminal return wrapped in code tags.
I always try to promote CLI or terminal commands, hang in there you be a pro in no time. ;)

---

