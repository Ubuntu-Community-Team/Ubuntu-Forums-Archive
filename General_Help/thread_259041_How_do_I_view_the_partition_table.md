---
title: "How do I view the partition table?"
date: 2006-09-16
forum: General Help
---

### Post by megamanXplosion on 2006-09-16
I have just installed Edgy Eft and I am liking what I see. I am fairly new to the linux scene so I do not have much experience--please bare with me. I have already managed to install the Opera web browser, XAMPP for a web server solution, Windows fonts, and installed some graphics drivers for my ATI Radeon 9250. So far everything has worked as it should; however, I am at a loss on how I view the partition table. I am currently following the instructions found on the [Partitions and Booting](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html) documentation page--step one. The first step on the [Check disk space usage and view the partition table](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#listpartitiontables), which the Partitions and Booting page links to, shows that I should go to System -> Administration -> Disks. I do not have a "Disks" entry in that menu...

Could someone show me another way to accomplish this task or how I can make the "Disks" option available? I want to start listening to the music I have stored on another partition...

---

### Post by Littleweseth on 2006-09-16
I've never used the graphical partitioning tool to mount Windows partitions, but if you're alright with the command line this should help you out : [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

Be careful with mounting NTFS partitions, though - usually you'll want to mount them read-only. Apparently the NTFS write drivers aren't 100% reliable yet - though many people seem to be using them with no issues, I don't trust them yet.

-lws

---

### Post by megamanXplosion on 2006-09-16
I figured out where I went wrong. I did not install gparted like the instructions told me to. I thought that because I seen it during installation that it didn't need to be installed. I installed gparted and figured out that my music, videos, and images were on HDA5 (figuring this out was what I was trying to do--I should've mentioned that in the first post, sorry about that.) I continued following the instructions and manually mounted the drive, now I have access to my multimedia. I have just installed the gstreamer codecs and now my music and videos work :)

Thanks for the response anyways Littleweseth, it is certainly appreciated :)

---

### Post by Littleweseth on 2006-09-16
No problem :)

---

