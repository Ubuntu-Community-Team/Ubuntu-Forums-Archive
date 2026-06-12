---
title: "Can't boot windows 7 with UBUNTU"
date: 2012-11-13
forum: General Help
---

### Post by darroosh on 2012-11-13
I'm new to linux world. Just downloaded ubuntu and installed it alongside with windows 7 . In grub when I choose ubuntu, it opens with no problem, but when I try to open windows 7, this message appears: "A Disk Read Error Occured. Press CTRL+ALT+DEL to restart."

I googled for that problem which directed me to download a boot repair tool, when I choose : advanced options / restore MBR --> apply, then restart computer , It boot to win 7 without loading the grub menu.

then I opened the live ubuntu from a USB, launched the "boot repair" again, choose : recommended repair , then restart, It returns to the first problem , grub menu appear, from which I can choose only ubuntu , but win 7 show this msg again : "A Disk Read Error Occured. Press CTRL+ALT+DEL to restart."

I repeated more and more with the same results ...

What should I do?

I created a boot info summary using the "boot repair tool" if this can help , it's in this URL : [http://paste.ubuntu.com/1356081/](http://paste.ubuntu.com/1356081/)

Any trial to help is apprecited,
Dr Mostafa

---

### Post by oldfred on 2012-11-14
Welcome to the forums.

Your grub2 in the MBR seems a bit strange but I have not paid close attention to the details of the new grub2 2.00 and how bootinfo reports it. If it boots Ubuntu you are ok.

You show /grldr several times in your Windows partitions. Is that from EasyBCD? I do not know EasyBCD.

[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Did you resize Windows before the install with Windows tools or as part of the Install? Best to use Windows and reboot as it does want to run chkdsk and make other repairs based on its new size.

You show boot files in both sda1 & sda2 with both having entries in grub's menu. Have you tried both?

---

### Post by smss on 2012-11-14
If you can not see windows in boot list but the windows partition is correctly and healthy, try with this : ```
sudo update-grub 
```

---

### Post by darroosh on 2012-11-14
Thank u for sharing ..

[[COLOR=#DD4814]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711") : I didn't resize partitions , And yes I tried  both partitions ...
[smss]("http://ubuntuforums.org/member.php?u=1209266") : No , I can see it  in GRUB , but  when clicking it , It says : "A Disk Read Error Occured. Press CTRL+ALT+DEL to restart" ..

---

### Post by darroosh on 2012-11-14
I think this may help identifying the problem :

When  I open boot repair  ,  choose the  "repait with  recommended settings ", 
It start repair , after small time the following error msg appear :   
"Embedding-error-in-sda detected. You may want to retry after activating the [Separate /boot partition:] option."
Then I click OK , It continues to repair , At the end of the repair , the following msg appear : 
"Boot successfully repaired.   
 Please write on a paper the following URL: 
 [http://paste.ubuntu.com/1358413/](http://paste.ubuntu.com/1358413/) 
  
 In case you still experience boot problem, indicate this URL to: 
 [email]boot.repair@gmail.com[/email] or to your favorite support forum. 
  
 You can now reboot your computer. 
  
  
 The boot files of [Ubuntu 12.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)".


Note the last part of this msg ! ...
 
I didn't understand wt should  I do ...

Can someone help wt  should I do ?

---

### Post by oldfred on 2012-11-14
We see some  BIOS or grub issues with either very large / (root) partitions or partition where the boot files are beyond some point on drive. Moving boot files inside that has just about always worked. Boot-Repair suggests a separate /boot. I normally suggest a smaller / (root), but you already have a smaller / partition of 11GB.

It can also be BIOS settings. Do you have fast-boot or quick-boot or something similar enabled on drive. Do you have AHCI not IDE for hard drive settings?

If BIOS settings are ok then you need the separate /boot partition within the first 100GB of drive. It does not look like you have a lot of data in sda3. You may be able to backup any data in it. Convert it to a small ext2  /boot partition of 200 or 300MB. Then move extended partition left and create new NTFS partition that will be almost as large as sda3 was. It will end up as sda9, but that should not matter.

If a new install, it may be easier to reinstall using Something else to choose existing partitions including your new /boot. 

If knowledgeable you can copy boot files to new boot partition, edit fstab and reinstall grub from liveCD. If you just want to learn I may be able to walk you thru it as I did it 3 or 4 years ago.

---

