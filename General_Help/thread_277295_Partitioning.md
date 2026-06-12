---
title: "Partitioning"
date: 2006-10-14
forum: General Help
---

### Post by calvinthomas on 2006-10-14
I got a free CD with a magazine of SUSE 10 Enterprise and whilst it is nice I prefer Ubuntu I think and so want to remove it, However I had to repartition my Ubuntu partition to install it, is there a way I can simply format that partition and put it all back together? Alternatively, can I simply make that like a second harddisk, a bit like having C: & D: on Windows? If so how would I tell Ubuntu to install to the second partition?

Calv

---

### Post by Kateikyoushi on 2006-10-14
Sorry it is a bit hard for me to interpret your sentences.

You have ubuntu installed and want to install suse.
Why do you want to format and put it together ?

You can resize the ubuntu partition and make space for the suse, I think suse's installer can do it as well. This would be just like you wrote a C and a D partition.

Could you try to make it a bit more clear ?

---

### Post by katalyst23 on 2006-10-14
You could probably use a GParted LiveCD to delete the partition, and then resize your Ubuntu partition to include it, or you could just reformat the partition.  If you were just using it as a second hard disk, I don't know why you would want to install Ubuntu to it, if you format in the right filesystem Ubuntu will be able to read/write files to it fine.  

Just be veeeery careful using GParted, and don't delete the wrong partition or anything.

---

### Post by calvinthomas on 2006-10-14
Sorry I'll try and be clearer:

I had Ubuntu installed on a 35Gb partition, I then installed Suse and repartitioned to allow it 11GB from my Ubuntu harddisk, so my partition now looks like this:

Ubuntu - 24Gb
Suse - 11Gb.

What I actually want is to go to back to what I was at which is:

Ubuntu - 35Gb

Does that make more sense?

Calv

---

### Post by fatsheep on 2006-10-14
Delete the Suse partition in GPARTED and resize Ubuntu to fill up the now empty space.  If the gparted program in ubuntu doesn't do the trick then you might want to try the [GPARTED Live CD](http://gparted.sourceforge.net/livecd.php).

---

### Post by calvinthomas on 2006-10-14
Do I need to worry about the Grub Boot Menu with doing this? Since I installed Suse after Ubuntu?

Calv

---

### Post by Kateikyoushi on 2006-10-14
No, you just make the ubuntu partition bigger, won't cause booting problems, only for suse. ^^; 
The only thing you have to do is remove the suse entry from your grub menu.

---

### Post by calvinthomas on 2006-10-14
Sorry to be a pain but how would I do that, I've heard its quite easy to corrupt grub!

Calv

---

### Post by Kateikyoushi on 2006-10-14
The first line mkes a backup from your grub menu, the second opens it for editing.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_old
gksudo gedit /boot/grub/menu.lst
```

Then search for the suse entry and uncomment it if you are afraid to delete those lines by putting a # as the first character.

---

### Post by calvinthomas on 2006-10-14
I now have a grub 22 error, I have opened as a seperate thread but it anyone knows the solution that would be helpful. I will post solution here also if I get one.

Calv

---

### Post by calvinthomas on 2006-10-14
Fixed via:

[URL="http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+22"]
http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+22[/URL]

Thankyou all for your help, I have Ubuntu back perfectly now :)

---

### Post by frenchfry929 on 2006-10-14
If have the ubuntu cd, then you should just be able to clear your entire harddrisk, and just allow all of it for Ubuntu.

---

