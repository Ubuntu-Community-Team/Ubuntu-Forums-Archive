---
title: "System fails to boot up after installing upgrades"
date: 2014-09-26
forum: General Help
---

### Post by Snowripper on 2014-09-26
Hi guys

I am relatively new to ubuntu and after being prompted to run the  software update tool the system installed the updates it deemed  necessary. It then asked for a reboot which I did. However following the  Grub selection screen I now get a variation of these screenshots upon  each boot. The system hangs on the final message and never boots into  the Ubuntu GUI.

I am using xubuntu-13.10-desktop-amd64

I am not entirely sure how I go about debugging this? Selecting the  recovery option in grub allows me access to the recovery tools. I have  tried repairing the packages along with autoclean through the shell  access. However this is where my knowledge is now lacking. I have spent  many hours on the forums today to no avail, half the time I think I'll  make the issue worse if I am not confident in what I am entering through  the terminal. Can anyone advise what steps would be best to solve this?

Thank you very much in advance.

---

### Post by Michael_McKenney on 2014-09-26
[http://askubuntu.com/questions/256013/could-not-reliably-determine-the-servers-fully-qualified-domain-name](http://askubuntu.com/questions/256013/could-not-reliably-determine-the-servers-fully-qualified-domain-name)

---

### Post by Bashing-om on 2014-09-26
Snowripper; Hey;

Also
Consider:
> 
I am using xubuntu-13.10-desktop-amd64
 Is End-Of-Life and has no support. Highly recommended to upgrade to a current release !

[INDENT][INDENT]no point in beating
[INDENT][INDENT][INDENT]on a dead horse
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Snowripper on 2014-09-27
Hi guys thanks for your replies I really appreciate it i followed the domain tutorial however it didn't affect the behaviour I'm experiencing on boot. Concerning upgrades thats exactly what I tried to do through the software updater tool which lead to this problem. Any advice to debug and find the cause would be appreciated. I read that xorg conf maybe the issue so I rebuilt that but the boot problem still remains.

---

### Post by Bashing-om on 2014-09-27
Snowripper; Hey'

I say again, that 13.10 has no support.
There is no easy way to fix it, You have no access to what used to be the software repository. That software repository no longer exists as you may have known it.
The better thing is to upgrade to a current release (12.04, 14.04) . Release 14.04 will be supported 'til April of 2019.

EDIT: Tutorial to do and End-Of-Life upgrade:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
Though old it is still apt.

[INDENT][INDENT]past time to move on
[/INDENT][/INDENT]

---

