---
title: "Can't boot after using Ubuntu Live - Please Help"
date: 2015-01-27
forum: General Help
---

### Post by alasdair3 on 2015-01-27
I'd be eternally gratefull if anyone can help with a problem I've got myself into:

I have an ubuntu server 14.04 LTS install running from a 16gb USB 3.0. It has been working fine. 

Today I noticed that my 4GB root partition had become completely full while the 10GB partition for home folder was barefly being used. I decided I would use GParted from an ubuntu live USB to resize the partitions.

I put ubuntu desktop on a usb and ran it in live mode with no problem.

Looking at the USB with my ubuntu server install on, I couldn't see an obvious way to resize the root partition when looking with GParted. I didn't actually make any changes at to the USB with my main install on.

I rebooted the computer with only the USB containing my principal ubunter server install on and now I just get a message telling me to put  a valid boot media in. The USB shows up in BIOS correctly and is selected as the first boot device. If I boot up in ubuntu live the usb containing my ubuntu server install is accesible which suggests to me that it works.

I can't understand why ist would suddenly stop working. Could it be because the root directory on the server install is completely full? If so, how can I delete files from it now? I can see files to delete from a ubuntu live but because I don't have the correct permissions to delete them. Or could running ubuntu live have changed something with how the computer boots?

If anyone can offer some advice on how to procede I'd be very grateful - I'm worried that its irrecoverable.

Many thanks in advance.

---

### Post by yancek on 2015-01-27
> Looking at the USB with my ubuntu server install on, I couldn't see an  obvious way to resize the root partition when looking with GParted.

It's not difficult to resize with GParted.  Your problem is having a separate /home partition.  I would suggest that since you don't have much on the /home partition, you copy the data from it to some other medium then delete the /home partition.  You will then have unallocated space and you can resize the root partition to use the entire flash drive or just make it larger.  Booting from the Live CD on your flash and access the /home partition and copy the data off, then open GParted and and right click on the /home partition and select unmount from the options.  Do the same with the root partition.  Then go to the Partition tab at the top with the /home partition highlighted and select the option to Delete and click Apply.  Click the root partition to highlight it and then go back to the Partition tab and select resize to whatever size you want.  If you want a separate /home partition, click the Partition tab and select New and use the remainng space.

Having a full partition will often prevent logging on but I don't know about not booting.
Just booting from the Live flash shouldn't cause any problems.

In order to delete anything on the installed USB from the Live flash, you need to use sudo.  I'm not sure what you would delete though.  Probably be easier to resize the partitions.

---

