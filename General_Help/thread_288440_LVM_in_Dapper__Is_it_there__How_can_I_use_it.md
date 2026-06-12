---
title: "LVM in Dapper?  Is it there?  How can I use it?"
date: 2006-10-29
forum: General Help
---

### Post by Schammy on 2006-10-29
Via Synaptic I see that there are LVM packages included with the standard install of Dapper.  How the heck do I use them?  I've been searching the forums and can't seem to find a clear answer...

-- How do I use a package (i.e., LVM in this case)that I see is installed on the system (in Synaptic)?
-- Can I convert to LVM without loosing the data on my 4 hard drives?
-- Is there a GUI to launch, set up and manage LVM?

Thanks in advance for any assistance!

---

### Post by angryfirelord on 2006-10-29
I may be wrong, but I think setting up LVM is on the ubuntu alternate cd. 

[http://www.linuxemporium.co.uk/products/ubuntu/#pid84629]("http://www.linuxemporium.co.uk/products/ubuntu/#pid84629")

>  The Ubuntu Alternate CD uses the text installer instead of the new GUI installer. It needs less system memory and permits advanced installs with preseeded options as well as LVM or RAID disk configurations.


---

### Post by DarkN00b on 2006-10-29
I installed off the regular liveCD and it was set up by default. During the boot process on my laptop it pauses of a couple seconds at "Setting up LVM groups...[OK]".

---

### Post by Schammy on 2006-10-30
I agree with both of the replies above.  The alternate install CD allows you to set up LVM during installaiton.  I also see the "setting up LVM groups..." dialog in the start up screen.

My qustions is still:  How do I use it?  I don't see my hard drives set up with LVM, no Volume Grous etc...  How do I get LVM working on my machine short of using the alternate install CD.  Also, I don't want to loose any data in the process of converting to LVM.

Thanks!

---

### Post by AusIV4 on 2006-10-30
Depending on your setup, you may not be able to avoid losing data. You can't create an LVM on a drive that has data on it and expect the data to still be there when the LVM has been created. However if you have enough space and different devices, you can add devices to the LV one at a time and move things to the LV before adding the device. The Linux Documentation Project has a pretty good howto: [http://tldp.org/HOWTO/LVM-HOWTO/]("http://tldp.org/HOWTO/LVM-HOWTO/").

---

