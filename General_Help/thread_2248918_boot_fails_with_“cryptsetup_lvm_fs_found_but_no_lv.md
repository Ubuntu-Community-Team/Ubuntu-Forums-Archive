---
title: "boot fails with “cryptsetup: lvm fs found but no lvm configured”"
date: 2014-10-18
forum: General Help
---

### Post by the-stupidest-thing on 2014-10-18
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]                #this is cross-posted elsewhere because I have horrible luck getting responses.

I have a dual-boot(xubuntu/#!) setup LVM with dm-crypt+luks as follows

  ```
/dev/sda1 = /boot (xubuntu)
/dev/sda2 = /boot (#!)
/dev/sda3 = encrypted LVM[INDENT]/dev/mapper/volgroup-xroot = / (xubuntu)
  /dev/mapper/volgroup-yroot = / (#!)
  /dev/mapper/volgroup-home  = /home (/home/xubuntu & /home/crunchbang)
  /dev/mapper/volgroup-swap  = swap
[/INDENT]

```
  I have Grub installed only from xubuntu on the MBR 
  
I was able to set this up successfully get this working initially.  Recently, upon installing Libre Office on the xubuntu OS, I unwittingly  let the network manager get uninstalled. I attempted to reinstall it by  booting into crunchbang and then chroot-ing into the xubuntu file  system. It worked but it messed the crunchbang boot process up somehow. 
  First Grub dropped the crunchbang OS listing. I updated it and it  found it again. Now, when I attempt to boot crunchbang it seems to  process everything fine up to requesting a passphrase. After entering my  passphrase, it quickly  fails and reports the message "cryptsetup: lvm  fs found but no lvm configured" and reprompts for the passphrase again.
  looking into it, I found this error message comes from the   /usr/share/initramfs-tools/scripts/local-top/cryptroot script and occurs  when 
   ```
if [ "$FSTYPE" = "LVM_member" ] || [ "$FSTYPE" = "LVM2_member" ]; then
   if [ -z "$cryptlvm" ]; then
     message "cryptsetup: lvm fs found but no lvm configured"
     return 1
```
  $FSTYPE is just the type of the dmname, the decrypted lvm container  which is set as $cryptroot and then $crypttarget - apparently  successfully in order to reach this error.
  It seems like the script is checking for $cryptlvm to be an empty  string and if so fails with my error. I have found only one reference to  $cryptlvm, setting cryptlvm="" earlier in the cryptroot script, and no  reference to it otherwise.
  I have been checking things against my xubuntu install and all  relevant files so far are equivalent, including setting cryptlvm="" at  the beginning of the script. 
  
And this is where I'm stuck.
  
Can someone point me in the right direction here?
      [/TD]
[/TR]
[/TABLE]

---

