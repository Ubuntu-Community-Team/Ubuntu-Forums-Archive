---
title: "Help with fstrim: &quot;the discard operation is not supported&quot;"
date: 2016-03-02
forum: General Help
---

### Post by irvine_himself2 on 2016-03-02
I have two external drives,and both are now formatted as EXT4.  To synchronise the two drives, I have written a bash that checks they are mounted and then runs rsync.  However, since Backup1 is an SSD, I also want to run fstrim before they are synchronised.  

 While the mount and rsync bits appear to work perfectly, depending on whether or not I use sudo, I get one of the following errors for fstrim.
 
 ```
**# Without sudo**
 fstrim: /media/memyself/Backup1: FITRIM ioctl failed: Operation not permitted
  
 **# With sudo**
 fstrim: /media/memyself/Backup1: the discard operation is not supported

``` 
 
 Here is the bash
 ```
#!/bin/bash  

** # Define paths**
 Backup1="/media/memyself/Backup1"
 Backup2="/media/memyself/Backup2"
 
** # Mount Backup 1**
 #Note uuid is a permanent way of identifying the disks and is found using "ls -al /dev/disk/by-uuid/"
 if mount|grep $Backup1; then
   echo "Backup1 already mounted"
 else
   udisksctl mount --block-device /dev/disk/by-uuid/720c2af1-cc24-4cd3-ae6e-2a671f944487
 fi
  
** # Mount Backup2**
 #Note uuid is a permanent way of identifying the disks and is found using "ls -al /dev/disk/by-uuid/"
 if mount|grep $Backup2; then
   echo "Backup2 already mounted"
 else
   udisksctl mount --block-device /dev/disk/by-uuid/6e36624a-d91c-4bd0-86d0-45bfa22fc172   
 fi
 
** # Check both drives have been successfully mounted and run fstrim and rsync**
 if mount|grep $Backup1; then
   echo "running fstrim on Backup1"
   **fstrim $Backup1                             # fstrim**
   if mount|grep $Backup2; then
     # see http://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/?PageSpeed=noscript
     echo "Backing up with rsync"  
     rsync -av --delete /media/memyself/Backup1/Docs/ /media/memyself/Backup2/Docs/
   else
     echo "Backup2 failed to mount"
   fi
 else
     echo "Backup1 failed to mount"
 fi

``` 
 
 Would anybody care to shed light on what the problem is?
 
 Thanks in advance
 Irvine

---

### Post by QIII on 2016-03-02
Is your external SSD connected via eSATA or USB 3.0?

---

### Post by oldfred on 2016-03-02
I thought I saw somewhere that USB does not support trim.
I have seen where AHCI is required on internal drives to support trim, but AHCI is not used for USB.

---

### Post by QIII on 2016-03-02
Even if the SSD reports that TRIM is supported, and even if the enclosure supports UASP, I don't think there are any USB bridge controllers that support SCSI/ATA Translation Pass Through, which would be needed to pass the TRIM command.

Thus, the "operation not allowed" message.

---

### Post by irvine_himself2 on 2016-03-02
It's connected through USB 3

---

### Post by QIII on 2016-03-02
That'll likely be the problem, then.

As I said above, you won't be able to pass the TRIM command over USB.

---

### Post by irvine_himself2 on 2016-03-04
Okay, because I have been doing some heavy reading, it's taken me a while to get back to this. I have a partial, (though inelegant,) solution detailed below. However, I also have a couple of questions.

**Note**: Querying the device with [hdparm]("http://manpages.ubuntu.com/manpages/trusty/man8/hdparm.8.html") works and has some functionality, so there is some kind of SCSI/ATA communication.

**Questions:**
**1)** Would[ sg_unmap ]("http://manpages.ubuntu.com/manpages/trusty/man8/sg_unmap.8.html")be likely to work any better?
[LIST]
[*]If so, does anybody know of a practical tutorial on how to implement this? All I have been able to find are very dry technical articles. 
[/LIST]
 **2)** This [blog post]("https://blog.oxplot.com/make-usb-flash-write-fast-again/") suggests using the **hdparm** "secure-delete" function to recover a USB device's performance. As a test, I set and disabled the password, so I am fairly sure the controller does have this functionality. On the other hand, querying the device suggests "secure-delete" would take 196 minutes. Would reformatting the SSD have the same effect?

**Partial solution:**
Basically, the idea is to minimise the number of deletes. So, rather than using the SSD as the primary external  drive, I have set it up so that my documents are stored on the HD. Then, I can periodically sync the SSD with the HD. When combined with the "secure-delete" option, (from a functional point of view,)  I believe this becomes almost identical to fstrim(?) 

I am not certain about any of this and would very much like to hear from people who know more about it than me. So, for the moment I am not marking this as solved, and look forward to hearing comments or criticisms.

Thanks, Irvine

Edit
I just re-read the bkog-post. It was refferring to  "secure-erase", not "secure-delete"

---

### Post by mc4man on 2016-03-04
ssd's can be returned to 'virgin' state thru Secure Erase, this process is extremely fast , ( a min or 2 at most) & should never be done on a usb3 ssd.
If what you are referring to with secure-delete involves writing/overwriting a ssd then that would be a big mistake from what I see on a ssd no matter where it's located. (you are in effect filling the drive 100%

Any decent usb3 ssd drive should handle garbage collection quite fine on it's own & should be left alone. If you want you can over-provision the drive, period

---

### Post by irvine_himself2 on 2016-03-04
Thanks for pointing that out. I just re-read the blog-post, and it was referring to  "secure-erase", not "secure-delete". Out of curiosity, why should it not be done on a USB3 SSD?

---

### Post by mc4man on 2016-03-05
> **irvine_himself2 said:**
> Thanks for pointing that out. I just re-read the blog-post, and it was referring to  "secure-erase", not "secure-delete". Out of curiosity, why should it not be done on a USB3 SSD?
You should be able to find a lot of info online concerning that, here's one.
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

### Post by irvine_himself2 on 2016-03-07
Okay, after doing some serious checking, (and a final proof test,) I am in a position to mark this as as solved.

For reference, I am working with a “Seagate 1TB Backup Plus Slim”
 
 [COLOR=#ff0000]**Warning:**[/COLOR] **The following can be extremely dangerous to the health of a USB mounted SSD! Proceed with caution and check specifics against your own device.**
 
 **1) According to [this]("https://www.thomas-krenn.com/en/wiki/SSD_Over-provisioning_using_hdparm") article**:
 Over-provisioning is not just a case of leaving unused space, you have to physically enable a “**Host Protected Area**”.
 
 Checking my SSD:
 ```
sudo hdparm -N /dev/XXX
 
 /dev/XXX:
  max sectors   = 1953525168/1953525168, HPA is disabled
```
 
 So, since fstrim couldn't pass through the SSCI/ATA bridge and over-provisioning wasn't enabled, there was nothing whatsoever in the way of optimisation on my SSD.  
 
 With reference to the above article:
 > Before increasing the size of the spare area, all SSD blocks must be deleted. Only in this manner can the SSD controller actually use the hidden data areas for wear levelling.  
 All SSD blocks will have been deleted, when:  
 
[LIST]
[*] the SSD is in its delivery state     or 
[*] a [secure     erase or manual TRIM]("https://www.thomas-krenn.com/en/wiki/SSD_Secure_Erase") (depending on the specific SSD) has been     performed 
[/LIST]
 
 
 **2)** S**ecure-erase**.
  Running
   ```
sudo hdparm -I /dev/XXX
```
  
  The bits of interest are:
  ```
Security:  
      Master password revision code = 65534
          supported
      **not    enabled**
      not    locked
      not    frozen
      not    expired: security count
          supported: enhanced erase
      **196min for SECURITY ERASE UNIT.** 196min for ENHANCED SECURITY ERASE UNIT.  

```
  
  The main thing to note are:
 
[LIST]
[*] Secure-erase can take a long time. In my case, approximately 3     hours. 
[*] It is not guaranteed to work with all USBs, so check device specifics 
[*] There is a danger that that you could lock or freeze the device 
[/LIST]
    
 **3)** [COLOR=#ff0000]**Proceeding at your own risk and peril**[/COLOR][COLOR=#ff0000]**:**[/COLOR]
 From this [blog-post]("https://blog.oxplot.com/make-usb-flash-write-fast-again/"), the steps are  
 ```
**# Set a user password (Nine is an example, you could use anything):**
 sudo hdparm --user-master u --security-set-pass Nine /dev/XXX
**#**** Make sure password is set successfully ****by once again running**
 sudo hdparm -I /dev/XXX
**#**** Run the ATA Secure Erase command**
 sudo hdparm --user-master u --security-erase Nine /dev/XXX
```
  
 **Be patient and under no circumstances, close the terminal, nor switch off the device or computer. ** 
  
 If things have gone according to plan, after the indicated time, (in my case three hours,) you will get a command prompt and the device will be completely wiped, (it will not even have a partition table.)
  
 As above, verify that security is disabled  
 ```
[FONT=Liberation Serif]sudo [/FONT][FONT=Liberation Serif]hdparm -I /dev/X[/FONT][FONT=Liberation Serif]XX[/FONT]
```
  
 In case of problems see[ this]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase") article:
 > [COLOR=#ff0000]**WARNING:**[/COLOR] If the SECURITY ERASE fails, use **--disable-security** to set your drive back to normal. Do not set the password to an empty string or NULL. The Lenovo BIOS at least will not allow you to change the password if it's blank. It also freezes the drive so that you can't change the password later, after booting into an OS. I'm now stuck with three drives that are passworded and I cannot unpassword. I finally found a board with a Phoenix TrustedCore BIOS which does allow clearing an empty password - Chris.  
  
 
 **4) Assuming no problems:**
 You can now set the “**host protected area”** to allow over-provisioning. ([See here]("https://www.thomas-krenn.com/en/wiki/SSD_Over-provisioning_using_hdparm").)
  
  In my case:
 
[LIST]
[*] From section **1/** above, I have  1953525168  sectors of 512 bytes each. 
[*] To allocate 10 GB for over-provisioning, we need 10737418240     / 512 = 20971520 sectors 
[*] So, maximum  visible sectors = 1953525168     -  20971520 =     1932553648 
[/LIST]
    
  Thus, (in my case,) I run:
  ```
sudo hdparm -Np1932553648 --yes-i-know-what-i-am-doing /dev/XXX
```
  
  And I get the following output confirming HPA is enabled with 10 GB of over-provisioning:
  ```
/dev/XXX:
   setting max visible sectors to 1932553648 (permanent)
   max sectors   = 1932553648/1953525168, HPA is enabled
```
  
 
 **5)** **Create a new partition table and re-partition.**
  Before you can fire up Gparted, you need to re-boot. The reason for this is because the UUID of the device has changed, and various internal paths are still using the old one.
 
[LIST]
[*]      After the re-boot, use Gparted to give the drive a new partition table 
[*]      Set your new partition(s) 
[*]      Give it/them a label(s) 
[*]      Re-boot, (again,) to get the drive paths set properly 
[/LIST]

     You now need to reset the ownership of the device back to user:user
  ```
sudo chown -R memyself:memyself /media/memyself/Backup1
```
  
  And finally, return ownership of “lost+found” to root
  ```
sudo chown -R root:root /media/memyself/Backup1/lost+found
```
  
  That's it, your “USB mounted SSD” should now be in an “as new” condition with over-provisioning enabled.  
 
 [COLOR=#ff3333][B]Remember: Proceed with great caution, read the supplied links carefully, do your own research and consider the dangers before applying “secure-erase”. This is not guaranteed to work for every USB mounted device. 

[/B][/COLOR][COLOR=#000000]Best of luck, Irvine[/COLOR]

---

