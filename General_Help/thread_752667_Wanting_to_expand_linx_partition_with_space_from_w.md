---
title: "Wanting to expand linx partition with space from windows one"
date: 2008-04-11
forum: General Help
---

### Post by nanajeebus on 2008-04-11
I'm a bit confused about what to do here. My ubuntu partition has run out of space, at somewhat worryingly rate, and I'm hoping to use some of the space from my windows partition. It has 97 gigs of space and 30 gigs of it are free. I'd like to shrink that partition by 10gigs and add that to my ubuntu partition. I'm just not sure how to.

---

### Post by tvtech on 2008-04-11
okay I'll tell you what!  you may need to uhh reinstall grub after this so you should do a good bit of research before you tweek too many things on your linux partition.  the windows thing is EASY though  just do the following 

[COLOR="Red"]username@localhost:~$sudo apt-get install gparted

username@localhost:~$sudo gparted  [/COLOR]

this is the gui way it's easier than the non gui way,  then you can simply resize your windows partition to whatever size you feel is worthy of it   [COLOR="Magenta"][SIZE="4"][SIZE="5"]your going to want to do a little book keeping first though.  [/SIZE][/SIZE][/COLOR]

if your on XP  do the following,  right click my computer and change your virtual memory to 0  also change your drive restore size to 0 as well  and then defrag your disk until you can defrag no more.    this will open up a lot of free space and remove the ugly green unmovable blocks in the defrag window.  please note if you plan on using windows again you should leave enough space for at least 2gig of virtual paging memory and it's not a bad idea to allow it to have a system restore file as well.  which should be about 2 gig of space as well.  other than that just keep as much space as you think you'll use on your ntfs partition.  and use gparted to resize it from there.   simple and easy you can A.  just use the new rezise as a new partition or resize your ext3 partition but do a little research on that becuase I'm pretty sure that will cause you to have to reinstall grub.  you can also download the gparted live cd from [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

---

### Post by nanajeebus on 2008-04-11
Oh wow, thanks for this. I'll look a little more into the expanding the ext3 one. I'll do this later tonight as right and report back on it.

Thanks again.

---

