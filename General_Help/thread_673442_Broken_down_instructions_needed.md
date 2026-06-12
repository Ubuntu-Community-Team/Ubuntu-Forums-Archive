---
title: "Broken down instructions needed"
date: 2008-01-20
forum: General Help
---

### Post by Smush on 2008-01-20
Hi there can someone tell me 2 things in very basic detailed steps if possible if I am to install Ubuntu

1) How do I put Ubuntu on to the 50GB partition I created in partition magic via my windows OS when at the partition manager step of the Ubuntu installation?

2) How do I Increase my Swap partition I made as I try to edit it and it will only let me decrease it?

ScreenShot: [http://img251.imageshack.us/img251/9016/screenshot2qb2.png](http://img251.imageshack.us/img251/9016/screenshot2qb2.png)

Unrelated question:
Is ubuntu the only distro that can have the 3d effects like the desktop cube and awesome window effects like flames and wobble windows? If not which other distros can have it?

Thanks in advance

---

### Post by eltama on 2008-01-20
Hi,

1) First, you don't need Partition Magic to create the partition to install Ubuntu, you do it during the install process.
At step 4 you have to choose where to install the system. I don't recall the options by heart but I guess you have 3, one to use a portion of the disk, another to use it all and one to do it manually. Choose the third one and then on the 50GB partition that you created edit is options and put that it will be mount in "/" (without the quotes).

2) I couldn't see your picture, it says image not found.
To resize it you first have to free some adjacent space.

3) Nowadays most distros have desktop effects enabled by default.

---

### Post by Smush on 2008-01-21
> **eltama said:**
> 2) I couldn't see your picture, it says image not found.
To resize it you first have to free some adjacent space.

Ok sorry about that not working, how would I free up the space? or do I need to delete the swap and create it again in partition magic?

---

### Post by dark_phantom on 2008-01-21
You can do it both ways, by using partition magic on windows and creating two partitions one for / and one for swap.  Make sure to create / as ext3 and the other as swap.  Or you can just let the installation do it for you, much simpler.  It will ask you how to shrink your current windows partion and allocate the rest to linux.

Edit:
Here is a link [http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

---

