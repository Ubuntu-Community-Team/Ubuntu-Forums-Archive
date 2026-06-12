---
title: "Which Partition do I delete?.."
date: 2008-07-07
forum: General Help
---

### Post by elbone on 2008-07-07
Well I installed Kubuntu, Eh didn't hate it.

I liked XFCE better though and I forgot which partition I need to delete to get rid of Kubuntu and GRUB.

but what size would the Kubuntu partition be?
if I can't find out by size tell me other ways to find out which partition I need to delete.

I did install is on Sda3 (drive D) but the D drive isn't showing up when I click Computer it only shows C... is that normal...?

I hope you guys can answer all of mu questions yes I am a Lin-oob (linux noob)
at the moment

---

### Post by DJYoshaBYD on 2008-07-07
you cannot view linux partitions in windows.. you need to use the original install disc, or use partition magic.. word to the wise.. you better know EXACTLY what you are doing, because its very easy to screw up MBRs and file systems.. 

and you would know the size of the partition if you installed it.. lol

---

### Post by elbone on 2008-07-07
Again, I'm a noob...

Can someone please help and not criticize me.

---

### Post by DJYoshaBYD on 2008-07-07
I did help.. you need to use partition magic to format that partition and make it blank.. I figured that would help..

sda3 will show up as an unknown partition that is active, or an ext3 partition in Partition Magic.. that depends on what version you have.. you cannot see ext3 partitions using my computer in windows... windows sucks, for anything besides gaming anyway.. hahaha:guitar:

so yeah.. get partition magic, and you can find and format that partition.. just dont touch your windows partitions at all...


boooyaaaaa

---

### Post by forger on 2008-07-07
He actually did help you in a way :)

I don't know which live cd you have, but these tips are by using Ubuntu live cd:
You can boot from a live cd and load (mount) the partitions you want to take a look at. (The drives should be on the desktop, you can mount them by double-clicking most of the times, or right-click and there should be a mount option)

Then double-click to open the drive, head to the folder **[COLOR="Red"]etc[/COLOR]** **of that drive** (don't go to /etc/ of the live cd!!) and double-click on the file **[COLOR="Red"]lsb-release[/COLOR]**.

Logically in that file it should mention if it's Ubuntu (gnome) or Kubuntu (kde) or Xubuntu (xfce).

For example, I use Ubuntu, and my /etc/lsb-release file says:
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

If the above is the same for all the partitions, head to the file **[COLOR="Green"]etc/X11/default-display-manager[/COLOR]** of each partition you examine, it should mention desktop manager you're using:
gdm = GNOME (Ubuntu)
kdm = KDE (Kubuntu)
xdm = XFCE (Xubuntu)

---

### Post by elbone on 2008-07-07
He did help, by telling me to buy a $65.00 Product :P

or I could get it by other means hehehe!!! But I would never do that Riiight FBI :)

---

### Post by wilbbe01 on 2008-07-07
gparted is good for partitioning things.  Never buy stuff like partition magic, just not worth it.  Maybe if it were 5 bucks.......but probably not.

---

### Post by forger on 2008-07-07
sooo.. elbone, how did it go?

---

### Post by elbone on 2008-07-08
I decided just to install a different Desktop-Enviroment and now Kubuntu isn't all slow any more I installed XFCE and now KDE is as fast as XFCE :)

---

