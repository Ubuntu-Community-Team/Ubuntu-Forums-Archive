---
title: "Laptop duel boot:  vista sleeps/hibernates but ubuntu wakes?"
date: 2008-05-08
forum: General Help
---

### Post by SirLawrence on 2008-05-08
I have vista and ubuntu dual booted on a laptop through GRUB.  So I'm booted and working in vista, close the screen to take a break and when I lift the screen up, the login prompt for ubuntu is showing!   Has anyone run into a similar problem?  I have a sneaky feeling it's vista screwing with something but I'm not sure what.

---

### Post by hermes0710 on 2008-05-09
What is the swap device of your system? Could you post the fstab contents ("cat /etc/fstab")?

---

### Post by ryanhaigh on 2008-05-09
Sounds like vista power management is trying to suspend/hibernate when you shut the lid, that may be failing resulting in a restart or the computer may simply be turning back on and grub has ubuntu as your default os so it boots into that on restart.

---

### Post by SirLawrence on 2008-05-09
> **hermes0710 said:**
> What is the swap device of your system? Could you post the fstab contents ("cat /etc/fstab")?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7a4bba47-fd2f-445e-b566-49db042c5749 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=1bd67568-194e-413b-a8ec-8a5592e2dcc7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by SirLawrence on 2008-05-09
> **ryanhaigh said:**
> Sounds like vista power management is trying to suspend/hibernate when you shut the lid, that may be failing resulting in a restart or the computer may simply be turning back on and grub has ubuntu as your default os so it boots into that on restart.

I've may have eliminated sleep has the problem because I just got back home from a short commute.  I lifted up the screen and vista emerged.  So I think you might be right about it being hibernate.  One of these days when I remember I'll try some of the other modes to see if I can isolate the behavior.

What was puzzling to me was that the laptop booted (default is to ubuntu) while the lid was closed!?!  I was under the impression this couldn't happen, but now I know it can. :)



Anyway, once I get a vpn set up(wireles took a while, but i got it :) ), I'll be booting to ubuntu a majority of the time.

---

### Post by ryanhaigh on 2008-05-09
If its a MS vpn server then it is likely using PPTP. [This]("http://www.ubuntugeek.com/howto-connect-to-windows-vpn-server-pptp-with-ubuntu-710-gutsy-gibbon.html") is a pretty simple howto on configuring such a connection.

---

### Post by SirLawrence on 2008-05-10
> **ryanhaigh said:**
> If its a MS vpn server then it is likely using PPTP. [This]("http://www.ubuntugeek.com/howto-connect-to-windows-vpn-server-pptp-with-ubuntu-710-gutsy-gibbon.html") is a pretty simple howto on configuring such a connection.

Hey! Thanks a bunch for that link, it will be usefull.

---

