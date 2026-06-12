---
title: "Trouble resizing partition"
date: 2012-11-06
forum: General Help
---

### Post by LuigiAntoniol on 2012-11-06
Hi, people.

I would like to resize a partition but it simply is not working.

Details:
OS:
Ubuntu 12.04 Server with Lubuntu DE, all the latest updates.

Partitions look as thus (in gparted):
/dev/sda1   Unknown        94 MiB bios_grub flag
........2   ext2          572 MiB (boot loader)
........3   linux-swap   1.86 GiB (SWAP)
........4   ext4        13.40 GiB (/)
........5   ext4       216.63 GiB (/home)
unallocated unallocated 698.63GiB


I used advice from a Debian forum to get the above, too long ago to remember which one it was but it's worked very well for me.

My original HD is a 250GiB, but since I'm running out of space, I recently bought a 1TB HD.

(PC hardware:  AMD X4 3.2 GHz with 6 GiB RA, asus M4A series motherboard, HD's are all SATA)

Using a live USB (Ubuntu 12.04_64), I commanded "sudo dd if=/dev/sda of=/dev/sdb" plus something about bs=4096k and noerr, I copied it from an ubuntu help site.

Anyway, everything copied perfectly, no problems there.

And now the fun begins.

Time to resize, so I use gparted from the same live USB.

Try as I might, every time I try to resize the partition to take up the rest of the 1TB HD, it simply won't do it.

I commanded "sudo gparted" in terminal and while I'm running the resizing, I get the following error in terminal:

"Unable to satisfy all constraints on the partition.
The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/sda appears to be used, you can fix the GPT to use all of the space (an extra 1465128000 blocks) or continue with the current setting?"

and then it stops with the partition going back to it's original size of 216GiB.

I don't know what all that means and searching this error for hours on the internet revealed little other than that nearly all of the solutions involve RAID setups or dual boot systems.

In using fdisk, there was an error about the partition being out of alignment.  Further searching lead me to understand that the partition needs to start on a full cylinder instead of writing and reading across two as this would impact drive speed.  I haven't found a solution to that yet either.

I must be doing something wrong and I cannot figure out what it is.

---

### Post by amjjawad on 2012-11-06
Hi,

I'm going to make it as simple as possible and it could be just a thought or at least, this is what I would do if I were you.

1- If you still have your files on the old HDD, keep them there.

2- If you have deleted your old file from the old HDD, I would copy the files from the new one (1TB) to the old one (250GB) - yes, backing them up again and send them to the old one.

3- Run GParted from the LiveUSB (It is much faster and better than the LiveCD - if you don't have for whatever reason, that is different story).

4- GParted > Device > Create Partition Table

[IMG]http://i44.tinypic.com/2whfaxw.jpg[/IMG]


5- Click Apply ONLY if you have already followed step 1 and 2 above.

[IMG]http://i40.tinypic.com/11qsumc.jpg[/IMG]


Now, your HDD is back to the condition you bought it, no partitions at all.


6- Start creating your partitions

[IMG]http://i43.tinypic.com/s4behe.jpg[/IMG]

Usually, it is highly recommended (if you ask ME) to plan and create your partition BEFORE anything else. This is what I do for 2 years now since I have started using Linux and this is what I recommend to new users and everyone else.

7- After that, just copy your files using the classic way - sorry, not sure how to do this using the dd command.

dd command could be easy but one needs to be very careful when using it.


That is what I would do to fix this.

I would never bother to go another route.

---

### Post by LuigiAntoniol on 2012-11-06
Hi, amjjawad

Thank you for taking the time to reply to my query.

Although I marked this as Solved, it wasn't really as I decided on a different direction.

Ok, I must confess that the process you suggested intimidated me somewhat as I'm pretty much used to the concept of the "dd" command and not the mere copying of system files across to a new HD using your method, so I decided on a different direction.

After "cleaning" the HD with your method, I have decided to use the entire 1TB, in a shared setup, networked for myself and my wife on our home network (though ideally, I wanted two separate partitions, that experience is another story that caused me some grey hairs, which prompted me to try "dd").

I called the drive "Data".

I have created two folders, one for me and the other for wife (also on Lubuntu 12.04).  Hers will be shared out and my folders will simply be pointed to my folder there in.

---

### Post by amjjawad on 2012-11-06
> **LuigiAntoniol said:**
> Hi, amjjawad

Thank you for taking the time to reply to my query.

Although I marked this as Solved, it wasn't really as I decided on a different direction.

Ok, I must confess that the process you suggested intimidated me somewhat as I'm pretty much used to the concept of the "dd" command and not the mere copying of system files across to a new HD using your method, so I decided on a different direction.

After "cleaning" the HD with your method, I have decided to use the entire 1TB, in a shared setup, networked for myself and my wife on our home network (though ideally, I wanted two separate partitions, that experience is another story that caused me some grey hairs, which prompted me to try "dd").

I called the drive "Data".

I have created two folders, one for me and the other for wife (also on Lubuntu 12.04).  Hers will be shared out and my folders will simply be pointed to my folder there in.

Hi,

I'm sorry if my post came on a totally different direction from what you wanted or planned for but I posted that for a purpose and a reason.
I have decided to make my posts as simple as possible and not only for one person/OP but for almost everyone who may come across this thread and read it :)

I'm a member of Lubuntu and lately, this made me believe it is much easier and better to keep everything simple and light, same as Lubuntu.

I use dd command to write zeros to a HDD specially if I want to fix some errors or bad blocks. I know it can be used to copy but I just don't do this.

I always use that method and recommend it (Create New Partition Table) for anyone who has problem with HDD and to be more specific, partitions problems. It's very easy and fast. But of course, it is not general and not for each and every case as some cases can be fixed in a different way, that is for sure :)

Anyway, I'm glad everything is okay with you so far.

If you need anything regarding Lubuntu, feel free to ping me :)

Take care!

P.S.
Is that HDD an external one? if yes, does it have a Network port?

---

### Post by LuigiAntoniol on 2012-11-17
> **amjjawad said:**
> 

P.S.
Is that HDD an external one? if yes, does it have a Network port?


Hi,

No, it's an internal one.

My first option was to get a NAS drive and backup all my and wife's stuff to that once per week.

The problem is, here where I live, they cost about as much as a mid-range PC with a 1TB HDD and everything to make it work, like monitor, keyboard, mouse, etc..  Go figure.... :confused:

---

