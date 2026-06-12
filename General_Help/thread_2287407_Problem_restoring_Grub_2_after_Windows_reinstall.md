---
title: "Problem restoring Grub 2 after Windows reinstall"
date: 2015-07-19
forum: General Help
---

### Post by rdh61 on 2015-07-19
Hi,

I reinstalled Windows XP on my dual boot computer. I am now attempting to reinstall Grub 2 using the live CD, which requires an Internet connection.

But my Ethernet connection doesn't work (probable hardware fault). And the live CD doesn't let me connect by wireless. I have configured the wifi connection as normal, with the checkbox ticked to connect automatically. But no connection. If I click on the network in network manager, a box appears asking for the network encryption key. I fill it in and click OK, but nothing happens. This wireless connection worked well with my regular lubuntu installation (i.e. before reinstaslling Windows). What can I do to get Grub back?

Thank you.

---

### Post by Bucky Ball on 2015-07-19
Have you tried:

```
sudo grub-install /dev/sda
```

... then:

```
sudo update-grub
```

? You may need to change the sda to something else. See [here]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System").

---

### Post by oldfred on 2015-07-19
From live CD you need to mount partition first. Buckey's instructions work from inside an install that perhaps you booted with another install or Supergrub.

       #Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Only after you have rebooted:
sudo update-grub

Otherwise it trys to update grub on live installer and gives errors on live installer path /cow not update-able.

---

### Post by rdh61 on 2015-07-20
Thank you. Grub was successfully reinstalled. But I got the following warning message:

"Warning: sector 32 is already in use by the program 'FlexNet'; avoiding it. This software may cause boot or other problems in the future. Please ask its authors not to store data in the boot track."

Should I be concerned? I have never heard of "FlexNet" and certainly didn't knowingly install it. Yet I am the only user of this computer.

---

### Post by yancek on 2015-07-20
>  I have never heard of "FlexNet" and certainly didn't knowingly install it.

Probably the commercial software below?

  [http://www.flexerasoftware.com/producer/products/software-monetization/flexnet-connect/](http://www.flexerasoftware.com/producer/products/software-monetization/flexnet-connect/)

---

### Post by oldfred on 2015-07-20
You should not have to worry about flexnet.

Originally grub2 was a lot larger than grub legacy. Both legacy & grub2 write more code into the sectors after the MBR for booting. Windows does not normally use that for booting, but had more code in partition boot sector.
But then Windows rights management software particularly flexnet started writing in the same sectors after the MBR. For a while major conflicts occurred, but grub2 ended up modifying code to work around it.
Generally better not to have to use proprietary software, or have two drives, so you have two MBRs and can boot Windows on one drive and Ubuntu on another drive.

You may have installed one of these which use flexnet:
 Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others

With new UEFI/gpt systems, both Windows & grub have separate partitions for this type of code, so they never conflict.

---

### Post by Bucky Ball on 2015-07-20
> **oldfred said:**
> You should not have to worry about flexnet.

Originally grub2 was a lot larger than grub legacy. Both legacy & grub2 write more code into the sectors after the MBR for booting. Windows does not normally use that for booting, but had more code in partition boot sector.
But then Windows rights management software particularly flexnet started writing in the same sectors after the MBR. For a while major conflicts occurred, but grub2 ended up modifying code to work around it.
Generally better not to have to use proprietary software, or have two drives, so you have two MBRs and can boot Windows on one drive and Ubuntu on another drive.

You may have installed one of these which use flexnet:
 Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others

With new UEFI/gpt systems, both Windows & grub have separate partitions for this type of code, so they never conflict.

Informative as always, oldfred. Cheers.

---

### Post by rdh61 on 2015-07-21
Found this thread on the FlexNet sector 32 error: [http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254) It suggests how to clear sector 32 if there are boot problems. It sounds involved though, so I won't interfere unless I do experience problems. Thanks for the reassurance oldfred.

---

