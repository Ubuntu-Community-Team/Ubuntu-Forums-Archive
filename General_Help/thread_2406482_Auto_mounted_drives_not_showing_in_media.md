---
title: "Auto mounted drives not showing in media"
date: 2018-11-21
forum: General Help
---

### Post by sneakyhox on 2018-11-21
Hey all!

I'm having difficulty when using the terminal to try and change my directory into one of my mounted drives. I have set them to auto mount upon login to my system and they show up as mounted within the file gui and as icons on my desktop. However, when I try to go into the terminal and access them there, I get an error coming back with "no such file or directory". I've tried a couple of different methods:

cd /media/Programs   (I've set the name of my drive to Programs)
cd /media/username/Programs
cd /dev/nvme0n1p1

None of these options worked and each one came back with "no such file or directory". I went through with the gui to browse the drives and they function fine, but when I checked the media folder, nothing was listed in there at all. I've tried searching for an answer to this issue, but I can't seem to find one that works. Any help would be very much appreciated.

Using Ubuntu 18.04.1

---

### Post by howefield on 2018-11-21
Try pressing Ctrl + L keys in the file manager, should change the breadcrumbs to a text path. Assuming that you are using the default ubuntu file manager.

---

### Post by sneakyhox on 2018-11-21
> **howefield said:**
> Try pressing Ctrl + L keys in the file  manager, should change the breadcrumbs to a text path. Assuming that you  are using the default ubuntu file manager.

So when I do that it indeed shows me the location and when I put that in terminal I am able to change to that directory. It reads out as:

/mnt/"long string"

Is there a way to not use that long string for the drive? Would I have to set it somehow? Or is this my only option?

It does work! So I do thank you, but just curious if there is a way to use the name I created for the drive or if I'm stuck just copying the location every time by using the Ctrl + L?

---

### Post by oldos2er on 2018-11-21
The long string is the [UUID]("https://help.ubuntu.com/community/UsingUUID"). You only need to type the first two or three characters, then hit Tab for it to auto-complete.

---

### Post by sneakyhox on 2018-11-21
> **oldos2er said:**
> The long string is the [UUID]("https://help.ubuntu.com/community/UsingUUID"). You only need to type the first two or three characters, then hit Tab for it to auto-complete.

... Fair enough! I suppose that's not too difficult to remember. Thanks for your reply and for both of your help!

---

### Post by deadflowr on 2018-11-21
You can set a label which would have an easily remembered and readable name instead of those pesky long uuid strings.
Brief summary and howto at this custom grub wiki page:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labeling_the_partitions]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labeling_the_partitions")

---

### Post by sneakyhox on 2018-11-21
> **deadflowr said:**
> You can set a label which would have an easily remembered and readable name instead of those pesky long uuid strings.
Brief summary and howto at this custom grub wiki page:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labeling_the_partitions](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labeling_the_partitions)

Thank you so much! That is exactly what I was hoping to do!!

---

