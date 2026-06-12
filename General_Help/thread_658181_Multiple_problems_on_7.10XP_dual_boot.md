---
title: "Multiple problems on 7.10/XP dual boot"
date: 2008-01-04
forum: General Help
---

### Post by Neotonian on 2008-01-04
I'm new to Ubuntu, having used RH and descendants until a couple of months ago. I bought a machine with Ubuntu preinstalled (Feisty, since upgraded to 7.10) and XP as dual boot. 

I have a strange series of problems. To keep it short, I now find that my home dir has had permissions changed so that only root can write to it. Execute and read are still there for all. I went one dir above home and did 

sudo chmod -R u+w user/ 

but this had no effect. (Nothing changed, no error messages.)

I went to virtual console 1 and logged on with my usual user account, then did the same command. Again, no change, no error messages. 

I noticed that my gnome session is on virtual consolel 9, whereas I thought that 7 was standard. Could this be an error? Console 7 is completely blank, with 1 to 6 giving text consoles. 

In 8 there is a console of startup messages which terminates at the line

Starting lirc daemon: lircd
Running local boot scripts (/etc/rc.local)

The end of the line runs offscreen, so I can't see if this was OK or not, but  it looks suspicious to me as if this has hung. Can anyone advise on this?

I'm completely puzzled. I've got very keen on Ubuntu and don't want to abandon it. 

The disc is a 500GB SATA with 200GB XP, 200GB Ubuntu and 100GB unallocated (as yet). The system did its routine fsck at 20th logon this
morning and did not show any errors. 

All help appreciated ...

N

---

### Post by markharding557 on 2008-01-04
although there probably is a means of fixing your user directory i think it would be much simpler to create a new user for you and just copy over any date/preferences you need

---

### Post by Neotonian on 2008-01-04
Brilliant. 

Many thanks. 

Neo

---

