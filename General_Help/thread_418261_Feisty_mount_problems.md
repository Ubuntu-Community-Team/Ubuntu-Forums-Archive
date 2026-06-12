---
title: "Feisty mount problems"
date: 2007-04-22
forum: General Help
---

### Post by fschaefer on 2007-04-22
Hi!

I have two sata and one pata harddisks installed, whereas sda1 (my main boot partition) is mounted correctly at boot. You might want to take a look at my fstab:

```
proc            		/proc			proc    		defaults        				0       	0
/dev/sda1 		/               		ext3			defaults,errors=remount-ro	0       	1
/dev/sda5 none	swap    			sw              							0       	0
/dev/cdrom        	/media/cdrom0		udf,iso9660 	user,noauto     			0       	0
/dev/hdc        		/media/cdrom1		udf,iso9660 	user,noauto     			0       	0
/dev/hdd        		/media/cdrom2		udf,iso9660 	user,noauto     			0       	0
#/dev/           		/media/floppy0		auto    		rw,user,noauto  			0       	0
/dev/sdb1			/home/flo/sdb1		ext3 		user,defaults 				0	 	0
/dev/sdc1			/home/flo/pata		ext3 		user,defaults 	
```

Running edgy, everything worked fine for me. After upgrading to feisty, I really got problems mounting /dev/sdb1 and /dev/sdc1.

Running edgy, the pata-drive that is now located at /dev/sdc1 was at /dev/hdc1. Now, I don't even have any /dev/hd* in /dev.

When I boot with the above-mentioned fstab, /dev/sda1 is mounted at / AND /home/flo/sdb1 whereas /dev/sdb1 should be mounted there. Funny enough, /dev/sdc1 
is mounted at /home/flo/pata. Sometimes, none of both are mounted.

If i comment out the last line "/dev/sdc1     /home/flo/pata..." from fstab before rebooting, everything is working fine and I can manually mount /dev/sdc1.

What am I doing wrong?

---

### Post by fschaefer on 2007-04-22
Ok, meanwhile I found that with Feisty, all hds are adressed as scsi-devices... but that doesn't solve the problem either... ;(

---

### Post by taurus on 2007-04-22
You are missing two 0's at the end for /dev/sdc1.

---

### Post by fschaefer on 2007-04-23
Hmmm... the two missing zeros are at the end of my fstab; it seems like I just forgot them while copy-pasting. Meanwhile I found a solution on my own: instead of using /dev/sd*-adressing, I used the UUIDS to distinguish between the drives:

```
UUID=f59b48ee-a4ed-4a4a-a917-f072d027a313  /home/flo/sdb2 ext3  ....  
UUID=3dd318d9-083b-4a91-949b-78c267c77adf  /home/flo/pata ext3  ....
```

---

