---
title: "sudo not working"
date: 2007-01-06
forum: General Help
---

### Post by Gris on 2007-01-06
Hi everyone

I have an up-to-date Ubuntu 6.06 installation. When I try to use sudo it tells me my password is wrong. I can log in using my password. 

I tried rebooting using recovery mode, which left me as root. Thinking that I was all powerful at this point I tried adding my username to to the admin group. It said I was already in admin. So my password is good and I am in admin, but I can't sudo.

My /etc/sudoers file is bog standard and if I cat it, it has just the 2 normal entries for root and admin.

I think what started this is that my clock was set about a day into the future. So I set it to the current time and date. Then sudo complained about the time stamp being too far into the future so I issued 'sudo -k'. But then the trouble started. My time and date is currently back to a day into the future, but still no go, it just refuses my password.

Anyone know how to fix this? I've just spent a day bringing up this new installation and would hate to have to start over!!

Cheers

Gris

---

### Post by Gris on 2007-01-06
Hi again

I've found the problem: keyboard layout!

Cheers

Gris

---

