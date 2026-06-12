---
title: "GRUB issuse"
date: 2008-02-12
forum: General Help
---

### Post by articwolf939 on 2008-02-12
ok had vista and ubuntu on one partition dual booting just fine using GRUB and i decied i wanted to wipe everything clean and start all over, i like to do it time from time so i put in my windows vista reinstallation DVD and let it do its thing,

when it came time i put in my windows driver DVD to load the drive in then in restarted to continue to load drivers and GRUB kicked in and gave me a error 22 and would let me contine the installtion and i cant figgure out how to get past it.

i was able to reinstall ubuntu just fine cos it was GRUB but i cant install vista because of it. is there anyway to get ride of GRUB from ubuntu so when i restart i can load vista? so far everything ive tried, doesnt work so any ideas?

---

### Post by erginemr on 2008-02-12
From this post on Grub Error 22:
[http://www.neowin.net/forum/lofiversion/index.php/t405091.html](http://www.neowin.net/forum/lofiversion/index.php/t405091.html)

two notable possible solutions are:

> for those who are having this problem but have Vista instead of XP, you have to re-install Boot Loader only.

boot up from Vista Installation DVD and select Repair your Computer.(its below Install Icon).select Windows Vista and select Command Prompt.

execute this code:

bootrec.exe /fixmbr
bootrec.exe /fixboot

close command prompt window and restart.

and using "Super Grub Disk" from: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

