---
title: "Find the serial number of a laptop with its old hard drive"
date: 2013-02-01
forum: General Help
---

### Post by Kenjitamura on 2013-02-01
Well, my problem is that I lost my laptop on a public bus and I am having no luck finding it at the bus depots lost and found.  I've contacted the police and they said they can enter it into the National Crime Information Center database which is used by pawn shops and police departments to cross reference serial numbers of items recovered.  Problem is, I threw away the packaging and don't know what my serial number was.  I've already sent an e-mail to the manufacturer I bought it from to see if they happened to have kept the serial number associated with my laptop purchase and I'm waiting for a reply.  What I still have from the laptop is its power charger and its original hard drive.

A month after purchasing the laptop I replaced its original hard drive with a 120 gb SSD.  I put the original hard drive in an external enclosure and didn't bother wiping the windows 7 installation.  I've just been using it as backup storage and other than uploading newly downloaded media files into its Downloads folder I haven't changed a thing.

Is there a way I can extract the serial number of my missing laptop, from ubuntu, with it attached as an external drive?  I've been googling several different queries but they haven't really given anything useful except that I can access its registry with chntpw.  I haven't been able to figure out if there is a registry value for the serial number in the registry as all I can find are mentions of SystemBiosVersion and SystemBiosDate when online articles talk about getting bios information from the registry.

---

### Post by tgalati4 on 2013-02-01
Does your old drive have a maintenance partition?  Dell and IBM computers have maintanence partitions which may have service tag numbers and from there you may be able to get serial numbers.

---

### Post by DeMus on 2013-02-01
You have Ubuntu installed on the new SSD drive, right? And Windows 7 on the original drive which is now an external drive used for back-up?
When you give the police the type of computer you lost, including the Ubuntu OS, other programs which are installed, description of your desktop (picture, color, etc), **log-in** name, maybe there are pictures of yourself on disk, isn't that enough to let them know you are the owner? When you can give them such a detailed description it should be enough.
How many laptops with Ubuntu have been found? Shouldn't be many, I guess.

---

### Post by Impavidus on 2013-02-02
This is a long shot, but your ISP or a local network administrator may have logged the MAC address of your network card. This is encoded in the hardware, so it should be traceable even if a thief has wiped the SSD.

---

