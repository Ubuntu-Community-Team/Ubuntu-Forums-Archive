---
title: "Downgrade 12.04 to 10.04 (Grub issue)"
date: 2012-10-28
forum: General Help
---

### Post by sig357 on 2012-10-28
I currently have 12.04 64-bit installed on my machine. I would like to downgrade to 10.04 to setup an android build environment. I tried a fresh install of 10.04 (formatting all partition), however I get a grub error at startup, stating "incompatible license. "

I believe this because 12.04 upgraded grub. How do I accomplish this downgrade / fresh install of 10.04 

Thanks.

Also when booting to a 10.04 live CD I am unable to get internet access?

---

### Post by jerrrys on 2012-10-28
You can't downgrade to 10o4, you must reinstall or leave 12o4 where it is and create another partition for 10o4.

---

### Post by sig357 on 2012-10-28
> **jerrrys said:**
> You can't downgrade to 10o4, you must reinstall or leave 12o4 where it is and create another partition for 10o4.

I tried reinstalling 10.4. When I reboot I get a grub error. For some reason 10.4 is not able to overwrite 12.4 grub???

Basically I want to remove 12.4 and install 10.4

---

### Post by NikTh on 2012-10-28
Hi , 

try to use the boot-repair program from a LiveCD-USB of Ubuntu to correct the grub problems.

Boot-repair 2nd option .
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

Thanks

---

### Post by jerrrys on 2012-10-28
+1 to NikTH

---

### Post by hgergo on 2012-10-28
Or if you have a separate /home partition then reformat and install

---

### Post by sig357 on 2012-10-28
> **NikTh said:**
> Hi , 

try to use the boot-repair program from a LiveCD-USB of Ubuntu to correct the grub problems.

Boot-repair 2nd option .
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

Thanks

Thanks, I will try to reinstall 10.4 and give this a shot. However I am trouble connecting to the internet with 10.4 live CD. it works fine with 12.04. Can I install 10.4, reboot to 12.04 live CD (try) and fix grub that was way. (using the 12.04 utility on a 10.04 installation?

---

### Post by sig357 on 2012-10-28
Used the grub-repair tool. All is well. Thanks everyone!!!

---

