---
title: "Trying to move unallocated space to /dev/sda2"
date: 2013-02-19
forum: General Help
---

### Post by ordonak on 2013-02-19
Hi all,

I am trying to move my unallocated space into /dev/sda2. Can anyone give me the exact steps needed to do this without screwing up my windows installation? I have windows 7 on /dev/sda1 and my linux installation is on /dev/sda2. Attached is a screenshot of what gparted looks like.

Thanks for all the help!

---

### Post by mcduck on 2013-02-19
You should boot into Windows, and use it's own disk management tools to move sda1 to the end of the desk so you'll have the free space next to sda2. After that you can boot with Ubuntu CD, unmount swap, grow sda2 to use the free space, move sda6 to the end of the extended partition and then finally grow sda5 (which I assume is your goal here).

Quite many steps, but it's not as complicated as it sounds. Just make sure you have proper backups of all important files before editing your partitions. :)

---

### Post by dino99 on 2013-02-19
Thats a great screenshot  :p , but please take the time to watch it, and you will get the answer to your question.  ):P):P

- your linux is on /dev/sda5 (not sda2)
- sda2 is an "extended" partition, which mean you can create (in case you get room) some other partitions (like sda5 is)
- but sda2 is small, and sda5 even more (really too small to work with)
- and sda1 have plenty of unused room

so, resize sda1 to be able to extend sda2; and then set more room to sda5

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: always use gparted from a livecd/liveusb, so you get unmounted partition (mandatory)

---

### Post by Bucky Ball on 2013-02-19
Hi ordonak and welcome to the forums.

I have attached your screen shot and deleted it from the body of your post. Please attach large images (spare a thought for those with slow connections). This can be done by clicking 'Go Advanced' when editing or creating a post and clicking the paperclip icon. Cheers. ;)

---

