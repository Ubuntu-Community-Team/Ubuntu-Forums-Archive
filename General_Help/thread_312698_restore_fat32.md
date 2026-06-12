---
title: "restore fat32 ?"
date: 2006-12-04
forum: General Help
---

### Post by damu on 2006-12-04
While I was trying to repair WinXP with the Win cd, somehow my partition of datas in fat32 has been transformed in a split of a second in a nice free space of 115 Go! :-k 
I know that the partition has not been physically formated. Is there any way to recover it so that it is again recognised as fat32 , or should I forget about it and reformat it?

BTW, I am going to seriously investigate in VMware, so that I don't need to dual boot, just to be able to work with these few macromedia/adobe softwares!

---

### Post by RAOF on 2006-12-04
While I can't remember details, I'll give you hope.  It may well be possible.

It sounds like only the partition table has been changed.  If you edit that (with a LiveCD and **fdisk**, for example) you should be able to fix it by just marking that free space as a FAT32 partition.

I can't remember any HOWTO links, and the details will change depending on your system, but it should be able to be done.

---

### Post by damu on 2006-12-04
You gave me some hope... :)
I found [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") which can be installed on Edgy with synaptic.

When I asked to analyse the Hard drive, at first, the extented partition has been recognised as fat32 with its proper name (DATA1):
> D  FAT32 LBA    4826   0   1   20022   254   63   244139805   [DATA1]

So hope is not lost that I could recover the data that were not backed up before the crash...

For now, though , I still can't access it from Edgy. It was hda4, and I see all my partitions but hda4 with 'Storage device manager' (that I installed with synaptic as it's not installed by default on edgy).

Any idea of what could be the right procedure with testdisk to have hda4 mounted again?

thanks

---

### Post by damu on 2006-12-04
I also discovered that I can browse the folders and files with testdisk. So I can see that my files are here, the structure is just fine. But I can't get to have hda4 mounted in Ubuntu to access it. Any idea?

---

### Post by RAOF on 2006-12-04
It looks like, from this page ([http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)), that you want to go to the Analyse menu (where you found your old partition, and it had "D" (for deleted) next to it).

Then you want to select that partition, and press "A" to add it back in.  Check that it still says "Structure: OK", and browse the partition, etc, to make sure it's right, then hit the "Write" button to write the new, corrected partition table back to disc.

Incidentally, thanks for introducing me to that program.  It looks exceedingly useful.

---

### Post by damu on 2006-12-04
thanks for your help. I am not done yet, and wouldn't like to mess up now that I just managed to reinstall WInXP and  rebuilt a grub with an alternate edgy cd ! ...

So, what I get so far :
I select analysis and I get the 5 partitions of my HD, including the one to restore:

> 4 E extended  4743  0  1  4824  254  63   1317330

I select this partition and click enter to proceed, I get the five partition again but presented in another way, including the one to restore :

> D FAT32 LBA 4826 0 1 20022 254 63 244139805 [DATA1]

I click A, and I get :

> empty    0  0  1  20022 254 63 321669495


At the bottom of this page, there is a menu which gives the options of changing the head (beginning or end) , or the sector, or the cylinder, or to change the type of the partition, or to select 'done'

I don't have anything at that point which says "Structure: OK".

What do you think? You should I go for the 'change partition type" and select fat32?  It is the only option which makes slightly sense to me at this stage, even though it's not logical as testdisk already recognised this partition as fat32 on the previous screen...:-k

---

### Post by RAOF on 2006-12-05
Um, that doesn't seem right.

Although that looks like an awesome program, I don't think the documentation is too good :(.

I think it's probably a good idea to wait, and not possibly break anything, until someone with actual experience chimes in :-|.  I've never used that program, nor am I going to delete a partition just to try it out ;)

---

### Post by damu on 2006-12-05
thanks anyway. 

The good thing is that testdisk could find my lost partition. As you said, after that, the selection of the right procedure to recover the partition is not obvious. For example I can change the type to 'primary', 'bootable', '*', but not 'logical'. 
It might be something else that I need to restore. At the moment I am trying to generate a log file that I will send to the creator of this great app and see how it goes on.

Obvioulsy, if anyone knows another solution to restore my lost partition, any contribution is very welcomed ;)

---

