---
title: "Scanner driver"
date: 2008-06-08
forum: General Help
---

### Post by Bushytail on 2008-06-08
Hi Everyone

Just trying to get Mustek scanner working by dropping the correct driver into user/share/sane/gt68xx but it will not allow me to paste!

This is what i have done in Linspire, mepis & pclinoxos in the past and it was good

Any help would be much appreciated

Other than that all is OK

Dave

---

### Post by plucky on 2008-06-08
> Just trying to get Mustek scanner working by dropping the correct driver into user/share/sane/gt68xx but it will not allow me to paste!




Try ```
usr/share/sane/gt68xx
``` There is no **user** directory but there is a **usr** directory.

Good Luck

---

### Post by Bushytail on 2008-06-08
Hi Plucky

Sorry I did mean usr

The problem seems to be permissions and I get the message about not being the owner and cannot change access and paste the driver

Dave

---

### Post by plucky on 2008-06-08
> The problem seems to be permissions and I get the message about not being the owner and cannot change access and paste the driver



To copy or paste anything into that directory you need to use super user mode.In a terminal window ```
gksudo nautilus
``` will open Nautilus file manager in super user mode.You should then be able to copy and paste your driver into that directory.

Good Luck

---

### Post by Bushytail on 2008-06-08
Thank you Plucker

That is great and will be so useful for future reference

Nearly got my system as I like it

Just need to edit boot time in grub and install win4 lin or Parallels VM for work or mates who are in Windoze land and I will be done

Great Distro. Just need to learn how things are done a little different than the other Distros I have used

Used pcLinuxos 0.93a for a few years and I must say it was great, but finally installed 2007 version and have not been that impressed with it, which is why I am here

What are your thoughts re software firewall and anti virus for Ubuntu?

I am behind a Netgear firewalled router and use Clearmymail online antispam/antivirus? So do I bother 

I have used ClamAv and AVG for Linux plus Guard dog and Firestarter in the past but wonder if they are really needed?

Again, Thank you for your help. I will keep you posted on progress and I may have some requests for knowledge in the future if you do not mind

Best regards

Dave

---

