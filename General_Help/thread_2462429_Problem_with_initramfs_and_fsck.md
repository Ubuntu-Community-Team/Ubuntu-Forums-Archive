---
title: "Problem with initramfs and fsck"
date: 2021-05-20
forum: General Help
---

### Post by stereotomy2 on 2021-05-20
Hello everyone.

First of all, I want to say that I'm kinda newbie to Ubuntu, so I'm not really familiarized with complex commands.

When I turned on my PC today, Ubuntu 16 would not boot. Last time I used my PC I turned it off correctly and there wasn't any problem with it. But today I got this screen:

[IMG]https://i.imgur.com/wBlv0An.jpeg[/IMG]

So I investigated on Google and I found a solution that worked for a lot of people. Basically I had to use the command "fsck -c -y /dev/sda3" (sda3 is the partition so it may change the number). But when running that command, some error messages were displayed. At the end I've got this two messages:

Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?

[IMG]https://i.imgur.com/qEhCpHK_d.webp?maxwidth=760&fidelity=grand[/IMG]

After that, the process end but the problem is not solved at all. I've searched for other solutions but nothing seems to work. One thing I noticed is that it doesn't recognize common commands such as sudo or whereis, which seems really strange. Is there any way to make this command work, or any other solution that may help?

I use this PC for working so I need help as soon as possible. I don't really care about restoring files since I don't have a lot of things, but I really need to know if I can fix this problem without having to reinstall Ubuntu and every program I use to work, that would take me hours and even days.

---

### Post by grahammechanical on 2021-05-20
First thing to know is that the busybox prompt that you are seeing is  not a Linux command line. So the usual Linux commands do not work. I  would guess that the loading of Linux has failed.

Do you get a  Grub menu? If you do then select Advanced Options for Ubuntu and select  another kernel other than the one at the top of the list. If that loads  correctly then continue using that kernel. Another thing to try from the  Advanced Options menu is to select a kernel with recovery mode.

If  that loads to the recovery menu select fsck to check all file systems.  When the file system check is finish it will bring you back to the  recovery menu. Selecting Resume will resume loading of Ubuntu. It may  get you to a desktop using a low resolution video mode. A reboot should  load Ubuntu using the normal video driver. There are other options on  the recovery menu that might all be useful but let us not complicate  matters at this point.

You should also know that Ubuntu 16.04 has  reached end of life. Unless you are intending to purchase a Ubuntu  Extended Service Maintenance package you should upgrade to 18.04 which  has support until April 2023. Better still move on to 20.04 LTS. Many of  us would recommend re-installing in preference to doing an on-line  upgrade. A re-install with 20.04 might be quicker than fixing this 16.04  and then upgrading to 18.04 which only 2 years life support left.

Regards

---

### Post by stereotomy2 on 2021-05-20
> **grahammechanical said:**
> First thing to know is that the busybox prompt that you are seeing is  not a Linux command line. So the usual Linux commands do not work. I  would guess that the loading of Linux has failed.

Do you get a  Grub menu? If you do then select Advanced Options for Ubuntu and select  another kernel other than the one at the top of the list. If that loads  correctly then continue using that kernel. Another thing to try from the  Advanced Options menu is to select a kernel with recovery mode.

If  that loads to the recovery menu select fsck to check all file systems.  When the file system check is finish it will bring you back to the  recovery menu. Selecting Resume will resume loading of Ubuntu. It may  get you to a desktop using a low resolution video mode. A reboot should  load Ubuntu using the normal video driver. There are other options on  the recovery menu that might all be useful but let us not complicate  matters at this point.

You should also know that Ubuntu 16.04 has  reached end of life. Unless you are intending to purchase a Ubuntu  Extended Service Maintenance package you should upgrade to 18.04 which  has support until April 2023. Better still move on to 20.04 LTS. Many of  us would recommend re-installing in preference to doing an on-line  upgrade. A re-install with 20.04 might be quicker than fixing this 16.04  and then upgrading to 18.04 which only 2 years life support left.

Regards

I get the Grub menu, yes. I've just tried every option on the advance menu but none of them load correctly, they all lead to the same error. I also tried that fsck command on every option but I keep getting the same error, so it's basically the same. Is there any other command I could try or any other option?

I know Ubuntu 16 is an old version, but I used to work on a project that needed that version of Ubuntu. If this can't be fixed, I'll sure install Ubuntu 20 but right now it would be better for me if I can fix it.

---

