---
title: "help with rollback in synaptic without internet"
date: 2007-11-30
forum: General Help
---

### Post by ktru on 2007-11-30
Hey everyone, I'm a window's user trying to learn how to use Ubuntu. I recently bought a sony vaio vgn nr140e laptop, so I figured i'd install ubuntu on it. 

I've been trying to get it to become compatible with the wireless internet, but no luck. Currently I'm trying to install Wicd. But the silly goof i am when I tried to install wicd it deleted the network manager that was recently allowing me to connect to the internet with an ethernet cord.

Now I'm stuck with no connection to the internet at all. So I'm wondering if there's a way to rollback this change? 

I've tried installing the network manager and the gnome one, but I guess i need an internet connection in order to download it?

Any hope for me?:(

---

### Post by louieb on 2007-11-30
Ask me how many time I wound up reinstalling Linux - can't remember. Don't think theres any type of rollback for the OS - just backup and restore. Without a backup and no internet a reinstall is probably the easiest route to go. If you have another Ubuntu PC you could use APTonCD to get the packages you need.

---

### Post by ktru on 2007-11-30
I see okay then I'll try to reinstall. Is there any sort of guide to remove ubuntu or to reinstall it? From the cd the only option i get is to install it. And I heard if I just delete the partition with ubuntu on it GRUB won't work properly. Anyone got any clue?

---

### Post by ktru on 2007-12-01
sorry for the double post but, i just realized that with the live cd I can still access the internet through an ethernet cord. Is it somehow possible to take the network manager from the cd and install it into synaptics?

Also, any help on reinstalling would be greatly appreciated. It doesn't seem like there are any uninstalling guides out there :confused:

---

### Post by louieb on 2007-12-01
There is a way to use the live CD to add a package to your hard drive install. Never done it. but  the basic is boot to the live cd then run **chroot** to switch to your hard drive install.  It an advanced fix it method and I'm not going to be any help with it.

As far a reinstalling goes. Run the **mount **command while in the hard drive install and note which partitions are used for / (root) and swap. 

Then when you get to the partitioning part of the install choose manual and choose the same partitions  for / (root) and swap and check the format box. It will reuse them for the fresh install. GRUB will be installed again too.

If you decide its to much and you just want to go back to a windows machine. You will have to replace GRUB. Look here:   [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by ktru on 2007-12-01
So it seems simple enough. I just want to double check and see if we're on the same page. 

To reinstall just run the live cd
then install ubuntu agian as if it's the first time
but this time when it asks to partition just  go to manual and select the partition that's being used by ubuntu

That's it?

---

### Post by ktru on 2007-12-01
> **louieb said:**
> 

As far a reinstalling goes. Run the **mount **command while in the hard drive install and note which partitions are used for / (root) and swap. 

Then when you get to the partitioning part of the install choose manual and choose the same partitions  for / (root) and swap and check the format box. It will reuse them for the fresh install. GRUB will be installed again too.

If you decide its to much and you just want to go back to a windows machine. You will have to replace GRUB. Look here:   [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

I'm not sure what you mean by mount command while in hard drive install, can you please clarify?

Also when I try to format both the root and swap hds it only allows me to select one or the other. Am I suppose to just select the root partition?

---

### Post by louieb on 2007-12-01
The **mount  **command without any options just lists what is mounted where. 

And yes if you select the root partition that all you need. The installer should reuse the current swap partition.

---

### Post by ktru on 2007-12-02
I checked format for the sda3 and then moved forward but it spits back an error saying 

"no root file system is defined. Please correct this from the partitioning menu"

 Am I doing something wrong?

---

### Post by louieb on 2007-12-02
There should be a column labeled mount point. for sda3  is should say something like /media/sda3 - also should be a drop down box with / as one of the options. By selecting the / that how you tell it "this is my root partition".

its explained much better here with screen shots too: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ktru on 2007-12-02
ahh works great! Thanks so much for your help!!!:)

---

