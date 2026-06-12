---
title: "Get Grub to boot the media center partition on a dell 6400/E1505"
date: 2006-09-24
forum: General Help
---

### Post by punkinside on 2006-09-24
Hey all, the new Dells come with a 4 GB partition at the end of the drive that serves as a "media center" partition to view DVD's and such without actually booting any OS, I for one have no need for this partition but my gf wants to keep it on her computer. The thing is: I have to edit the menu.lst in grub to add an option at startup to boot in this partition. Has anyone done this? I'm not sure how to go about it.

---

### Post by H.E. Pennypacker on 2006-09-24
If Dell Media Direct is a seperate partition, you can add it to the Grub menu list, and have it show up on the list the next time you boot up.  If everything is as I assume it to be, you should add the following to your GRUB list (list it appropriately, at the position you'd like to to be - place it at the bottom for now to make sure everything goes fine - if it works at the bottom and you want to try it somewhere else, go ahead).

title		Dell Media Direct
root		(hd0,4)
savedefault
makeactive
chainloader	+1

This assumes that the partition is located on a harddrive, and that the harddrive is the first one if there are multiple ones.  The four ("4") designates the partition number, which you said is four.  The title can be changed to anything, but I recommend staying with what I chose.  

The three lines below "root," are probably not necessary, and if they trouble you, remove them, but leave them at first.  Leave them there unless something goes wrong.

Using Google, I found out that Grub has some difficulty with Dell Media Direct, and these directions may not go exactly as planned, but hopefully, they'll work.  Another individual, I found out using a Google search, is having the same problem as you are, and he/she is reporting an issue with Grub and Dell Media Direct.

Let me know whether this works.  It may not work, and the loading may get stuck somewhere.  If it doesn't, Grub may be required to load another boot loader and have that other boot loader start up the necessary operating system.  Directions for doings this are found at:

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#SEC14](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#SEC14)

---

### Post by punkinside on 2006-09-25
Thanx for the reply, I tried this already:

title Dell Media Direct
root (hd0,4)
savedefault
makeactive
chainloader +1

but grub failed with something about a filesystem type unknown. I'm going to try with the rootnoverify command from the link and see what happens

---

### Post by H.E. Pennypacker on 2006-09-25
If that attempt doesn't work, then you may have to use another boot loader specifically for Dell Media Direct.  You can still use Grub, but you'll load another boot loader, and then that boot loader will load Dell Media Direct.

Don't forget to keep us up to date.

---

### Post by punkinside on 2006-09-25
I will I just didnt get close to my gf's comp today... I've been reading another forums and it seems its a pain.

---

### Post by djgrandmarquis on 2007-06-05
My friend had a similar problem on his Dell Inspiron E1705. By default, GRUB picked up sd4, which is his Linux partition in menu.lst:

```

...
root (hd0,4)
...

```

However, he needed to boot the "Dell Utility" partition, which was sd1. This is a small (48 MB) partition that apparently contains the Media Direct software.

```

...
root (hd0,1)
...

```

Now everything works fine: GRUB boots Linux and Vista.

---

### Post by adammw on 2007-06-20
I'm not sure about this model of MediaCenter, but I have successfully boot the MediaCenter partition with GRUB on my Dell XPS m1210 laptop. Basically, GRUB detected "Microsoft Windows XP Embedded" when it was installed but the "makeactive" command has to be removed for it to boot.
By the way, does anyone know how to change the title of the GRUB boot things, "Microsoft Windows XP Embedded" sounds so stupid?
Thanks,

---

### Post by djgrandmarquis on 2007-06-20
Good to see it worked out for you.

To change the names, just edit the "title" fields in your menu.lst file. It's a good idea to make a backup first, in case you make a mistake:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Then edit the text as you see fit, using the text editor of your choice:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by f3ua on 2007-07-05
> **punkinside said:**
> I will I just didnt get close to my gf's comp today... I've been reading another forums and it seems its a pain.

Please... can you post your menu.lst file?
I have a similar problem.

---

### Post by confused57 on 2007-07-05
> **f3ua said:**
> Please... can you post your menu.lst file?
I have a similar problem.
You can probably remove both the savedefault & makeactive lines:
```
title Dell Media Direct
root (hd0,0)
chainloader +1
```

Change the root above to your Media partition.

---

