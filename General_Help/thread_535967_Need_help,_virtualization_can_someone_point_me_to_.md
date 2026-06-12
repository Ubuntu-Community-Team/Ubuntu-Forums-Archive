---
title: "Need help, virtualization: can someone point me to the right direction?"
date: 2007-08-27
forum: General Help
---

### Post by r_l on 2007-08-27
Hi,

I have been dual booting and it is really not very efficient.  I am trying to find a way to run Window directly in Ubuntu.  

I am thinking about some kind of virtualization.  However, I don't have an XP installation disk (just an OEM restoration disk).  

I read that Virtualbox 1.4 can boot a preinstalled XP partition in Virtualbox and I have successfully installed Virtualbox in Feisty.

Yet, I cannot find any good tutorials around on how to use my existing XP partition in Virtualbox; and the "Advance Topic" in the manual is beyond me (and to be honest, I am not even sure which section in the manual point exactly to that, either).  

I also saw a "how-to" here

[http://www.virtualbox.org/wiki/Migrate_Windows]("http://www.virtualbox.org/wiki/Migrate_Windows")   

but it is too difficult for me to understand what it says - and all the "warnings" about this I came across some where else kind of scared me (especially when I saw the "warnings" but didn't even quite understand what it exactly means).  

I am hoping that knowledgeable people here can guide me to  the right direction and any useful pointers will be much appreicated. 


Thanks!

RL

---

### Post by b20963a2 on 2007-08-27
Another option would be [vmWare converter]("http://www.vmware.com/products/converter/"). It allows you to duplicate your real setup to a virtual one + it's easy to use.

---

### Post by r_l on 2007-08-27
> **b20963a2 said:**
> Another option would be [vmWare converter]("http://www.vmware.com/products/converter/"). It allows you to duplicate your real setup to a virtual one + it's easy to use.

This looks pretty easy.  I will try that.

---

### Post by r_l on 2007-08-28
> **b20963a2 said:**
> Another option would be [vmWare converter]("http://www.vmware.com/products/converter/"). It allows you to duplicate your real setup to a virtual one + it's easy to use.

Sigh....I've spent too many hours on this than I would like to - and it still doesn't work.  I guess I am booting back to XP - but just to share here and may be some other will have better luck to do this than I did.

Well, I downloaded vmware converter and took me a long while to convert my partition into a "huge" image and put it in my NTFS partition.  Then I installed Vmware Player (it took me a while again because the Automatric copy didn't work and I needed to use the tar with a patch due to my Gusty kernel in Feisty).  After much work, I got Vmplayer working and tried to read the image - it didn't work (no operation permission).  I had another copy of that image in the external drive, I use that with VMmare - it didn't work, either (forgot what errors it was).  

Then, I went back to rethink VirtualBox and uninstalled Vmware - afterall the  new Vbox 1.4 version says it can open Vmware image - I tried to power-on, but it just showed me that there was an error and told me to press crl-alt-del.  After I did that nothing happen. 

Now, I decided to try the "raw disk" access from VirtualBox.  I didn't like to have a 20gb+ image in my drive anyway and I finally figured out that it calls to boot directly from you existing partition the "raw-disk access" in the manual and it is a new feature for 1.4.  I follow the command line indicated in the manual, type in something similar to this:

VBoxManage internalcommands createrawvmdk -filename /home/file.vmdk -rawdisk /dev/sda -partitions 2 -register

Which I figure to create a small vmdk pointing to the partition to boot. The vmdk image was created.  Then when I boot from it in VirtualBox, I got a Grub error 17 message.


Well, since 1.4 is still new and I could not find much information, either.  I lost my patience on this for now and I guess I will just have to boot back to XP to do my work .....:(:mad:

---

