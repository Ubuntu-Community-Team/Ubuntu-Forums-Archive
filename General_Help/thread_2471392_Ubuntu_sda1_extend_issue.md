---
title: "Ubuntu sda1 extend issue"
date: 2022-01-28
forum: General Help
---

### Post by tashman89 on 2022-01-28
Dears,

[COLOR=#474B51][FONT=Tahoma]Please advise what I have to do to extend /dev/sda1 I have tried many ways but no luck ...

[/FONT][/COLOR][IMG]https://www.howtoforge.com/community/attachments/upload_2022-1-4_23-58-10-png.7042/?ezimgfmt=rs:775x509/rscb5/ng:webp/ngcb5[/IMG]
[IMG]https://www.howtoforge.com/community/attachments/upload_2022-1-4_23-58-17-png.7043/?ezimgfmt=rs:758x330/rscb5/ng:webp/ngcb5[/IMG]


[IMG]https://www.howtoforge.com/community/attachments/upload_2022-1-4_23-58-28-png.7044/?ezimgfmt=rs:796x262/rscb5/ng:webp/ngcb5[/IMG]

[IMG]https://www.howtoforge.com/community/attachments/upload_2022-1-4_23-58-40-png.7045/?ezimgfmt=rs:884x361/rscb5/ng:webp/ngcb5[/IMG]

[IMG]https://www.howtoforge.com/community/attachments/upload_2022-1-5_0-0-45-png.7046/?ezimgfmt=rs:698x264/rscb5/ng:webp/ngcb5[/IMG]




[IMG]https://www.howtoforge.com/community/attachments/upload_2022-1-6_11-19-10-png.7050/?ezimgfmt=rs:884x570/rscb5/ng:webp/ngcb5[/IMG]

Thanks

---

### Post by oldfred on 2022-01-28
Please do not post screen shots of terminal output. Better to just copy & paste the terminal output. And if more than just a few lines use code tags which are easy to add with Forum's Go Advanced editor and # icon.

Moving partitions always has risk.
Any power failure or interruption will totally damage data.
So you must have good backups.

You have to use gparted from live installer.
You can move sda5 all the way right, then shink the extended partition so the unallocated is then next to sda1 outside of the extended partition.

But it does not look like you are using /home?

---

### Post by grahammechanical on 2022-01-29
GParted lists sda1 as having the xfs file system which is a default file system for Redhat according to the internet. The GParted manual says this about xfs:

> [2] You need kernel support for this file system if you want to grow it (or shrink if shrink is supported).
[3] Although it's not possible to shrink an xfs file system directly, you can shrink it using GParted's copy functionality.
[5] Copy performed using xfsdump and xfsrestore.

[https://gparted.org/features.php](https://gparted.org/features.php)

That being said, you need to expand the extended partition sda2 to the right into unallocated space. This should create unused space to the right of sda5 which is a logical partition inside sda2.

Having done that you then move sda5 to the right and close to the right boundary of sd2. This will put empty space to the left of sda5 but still inside sda2.
Now, shrink the left boundary of sda2 to take up the unused space. This will create unallocated space between sda 1 and sda 2 which you can expand sda1 into.

I guess that a Redhat utility might be more useful for doing that.

Regards

---

### Post by ajgreeny on 2022-01-29
Why enlarge the sda1 partition which is only currently half used?  My OS root partition is only 20G and still after two and a half years only 50% used, but I'm not a gamer which I believe can use a lot of space in the root partition.  I would leave sda1 at its current size and simply extend sda5 into an enlarged sda2: see more detail below.

NB:
I don't know xfs at all so I am answering this as if dealing with an ext4 system.  Bear that in mind in case it affects the ability to do what I suggest.

If this machine was mine and using ext4 filesystem, not xfs, I would boot to a live system, run gparted from that and
[LIST=1]
[*]Enlarge the current extended sda2 to the far right by dragging its right edge, then
[*]Enlarge the current sda5 home partition to the far right by dragging its right edge to fill the full size of the now partly empty extended sda2.
[*]
[/LIST]

This will give you an enlarged /home partition which you should be able to start using if not doing so already, though how it is not being currently used, as suggested by oldfred, I do not understand.  It appears to be mounted at /home according to your df -h output so I can only assume this is a new installation with very few data files, ie, documents, music, videos, photos, etc etc, in the /home partition.

---

### Post by tashman89 on 2022-02-06
Thanks Dears for your kind reply, but unfortunately the most of these options didn't work with me .

---

