---
title: "Change Hard disk drives"
date: 2006-09-11
forum: General Help
---

### Post by HereInOz on 2006-09-11
Hi All,

I have Dapper running on a 80GB HDD and I would like to transfer the entire system on to a 160GB HDD.

Is there a way to do this, like you can with Ghost in Windows.  I have checked out dd and it looks like it might do it, but I am not sure of the process.

I am not dual booting or anything like that, just a straight Dapper installation with Grub boot loader.

Can anyone assist in letting me know the way that I can get my system on to a new HDD without having to re-install?

Cheers,

Alan.

---

### Post by Ramses de Norre on 2006-09-11
[This]("http://www.psychocats.net/ubuntu/partimage.html") page may help you =)

---

### Post by turbojugend_gr on 2006-09-11
If you are about to keep your 80gb disk, I c no reason... 

Imho you can partition the 160 gb disk , one partition for your "home" to grow bigger, and another for the "/" (root) to grow also. After you 've made these partitions you can mount them (using fstab) inside /home and / correspondigly. 

Then you will see your home and root are bigger but you won't see the partitions in it... yet again you can manage them under diskmanager (disks-admin).

 It is a nice, easy, way to get by it. So when edgy eft is released, or whenever you feel like changing your system, you can take your important folders-files (usually inside your home) and then set up your system as you would now, till then though less trouble for you!

Plz let me know if you need any help on how to perform the above suggestion, I 'll be glad to give you a hand.

---

### Post by HereInOz on 2006-09-11
Thank you for the info, but I want to use the 80GB HDD for something else, so what I want to do is exactly the same as using Ghost in Windows - that is, to create an identical copy of the existing HDD on another HDD, so that I release the 80GB disk for other work, and end up with a larger drive for Ubuntu.

I will have a look at partition image as the previous post suggested.  Are there any other ways?

Alan

---

### Post by turbojugend_gr on 2006-09-11
Sorry m8 none that I know of.
Oh except of an ugly one. If you can't use partition image, you can always have you 160gb drive mounted, then have a full copy of "/" excluding home directory, in your new 160gb partition you created for "/" then repeat for home dir in home partition you created in 160gb drive, then create a swap partition sized 2x your RAMemory and you are ok... 

To do the above you should gain super-user (administrative) priviledges, a "sudo" is enough most of the times. If you need a more verbose how-to on that, post asking for it, I hope that partition image will do the trick, but just in case...

Oh Notice even with partition image you will have to end up with a way to create a swap partition in your new drive! I do not know if it does it for you so be carefull on that.

Glad to help.

---

### Post by monktbd on 2006-09-11
i would partition the new harddisk as i see fit then dd all the partitions to the new harddisk, make the proper partition bootable and tell then my bios to boot from it.

it depends quite a bit of how your current partition setup looks like and if you would like to change something in it. (e.g. putting /home on an extra partition if it isnt yet).

---

