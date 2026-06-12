---
title: "I have Ubuntu &amp; Windows Server On And I Want 1 more"
date: 2008-07-07
forum: General Help
---

### Post by j0keman on 2008-07-07
Hi guys,

Since I am experiencing some problems with my video card under Ubuntu - Intel problem with drivers and I tried about 1000 "solutions" I decided to leave it that way and to install another system.

I have now installed 2 OS - Ubuntu 8.04 & Windows Server 2003 and they are loading through GRUB. I have 3 hdds. And I want to install XP for example on the third one so I can install there some games etc. But how can I make that up and running but you have in mind that the most important things are the Server OS and the third hard. These I don't want to lose because they are concerned with my job.

Thanks in advance guys!

---

### Post by justleen on 2008-07-07
just create a partition, and install xp on that.

The only catch is: xp will overwrite grub, you'd have to reinstall that from a live cd...

---

### Post by j0keman on 2008-07-07
And when I install windows I use the live cd to restore GRUB but will I find also Server there after that?

---

### Post by justleen on 2008-07-07
it will find the server there, since thats already in grub.
I wont add the new XP, but you can edit the menu.list manually. its just a matter of copying the server2003 entry, give it a new title and change the disk it points to.

Supergrub Disk might do a search for other OS'es, not sure..

you could do the long way, which is going trough the install setup (leaving the disks intact! so no formats..) and reinstall grub that way.. it does search for other OS'es

---

### Post by j0keman on 2008-07-07
OK I will give it a try now and write later.

Thanks for the help mate!

---

