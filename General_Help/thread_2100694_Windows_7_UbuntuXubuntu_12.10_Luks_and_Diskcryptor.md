---
title: "Windows 7 Ubuntu/Xubuntu 12.10 Luks and Diskcryptor"
date: 2013-01-02
forum: General Help
---

### Post by optimumpro on 2013-01-02
A few days ago, I posted instructions on how to install Windows 7 and Ubuntu 12.10 both encrypted on the same machine: Ubuntu using Luks and Windows 7 - Truecrypt. Today, I am providing instructions on the same process using Diskcryptor ([www.diskcryptor.net]("http://www.diskcryptor.net")) in place of Truecrypt . 

In my view, Diskcryptor is much more advanced than Truecrypt. Unlike Truecrypt, Diskcryptor is a true open source and it uses XTS/sha512 method of encrypting a system partition, which truecrypt does not support. In addition, there are claims all over the internet that Truecrypt open source binary files are different from those in the actual program, which gives credence to suspicion that Truecrypt may contain a back door, since it cannot be thoroughly examined. 

The idea is: to have Dskcryptor prompt at startup: when you enter Diskcryptor password, Windows 7 will start loading; when you press enter (wrong password), *buntu 12.10 starts. Here are the instructions:

You need Ubuntu/Xubuntu 12.10 live CD and Windows 7 CD.
 
 First, start Windows installation and choose custom install.  Pick the size for your  Windows 7 partition. Windows will automatically create a 100mb  additional boot partition for itself. Leave the rest of your space  unallocated. Install Windows and configure it the way you like it. Next,  insert Ubuntu/Xubuntu 12.10 CD and reboot your computer. Start installation. At  installation type prompt, pick &#8220;something else. &#8220; Next, you will be  taken to partition editor. You will see your 2 windows partitions and  perhaps some other stuff depending on your computer. Highlight "free  space" and create your *buntu boot partition by clicking &#8220;+&#8221; in the left  bottom corner of the partition editor.  Boot partition is usually about  250mb in *buntu 12.10. Pick the size of your boot partition, set it as  /boot and use it as Ext2 or 4. Leave other options untouched. In other  words, you will be creating a logical partition with boot mount point.  Click OK. Next, you will again be presented with partition editor  reflecting your newly created boot partition. Highlight "free space"  again and create your root partition for Ubuntu install. Pick the size  and this time use it as &#8220;physical volume for encryption.&#8221;  You will  immediately be presented with an option to enter your Luks password. Do  it  and press OK (there will also be an option to overwrite your empty  disk space, which is optional). You are not done yet. Once you get to  the partitioner again, you will see your newly created second partition  as &#8220;dev/mapper/sda*.&#8221;  Now, highlight it and choose &#8220;change&#8221; (again in  the left bottom corner). This time, set the mount point as root, i.e.  &#8220;/&#8221; and use Ext4.   Next, you will again be taken to the main  partitioner window, which should show your boot and root partitions.  DONE. Install your *buntu and reboot when instructed.

You will be presented with a familiar Grub2 menu. Now, choose *buntu and make sure it loads properly. Next, restart your computer and this time choose windows 7. Download and install the latest version of diskcryptor. Install it and reboot. Choose windows again. Open diskcryptor. It should show your windows 7 partitions: Boot and System (c). Install bootloader. Then configure bootloader as follows:

Main tab: Booting method - First partition with appropriate password;
Authentication tab: Password request; Password prompt message - Enter (or your own message); Show entered password - hide; Authentication timeout - disable;
Invalid Password: mark "use incorrect password action if no password entered"; 
Invalid Password message: Booting System (or your own message)
Invalid Password action: Load boot disk MBR.

Save your boot loader configuration. Now, encrypt your windows boot partition first. Next, encrypt your windows 7 drive (C).  **USE THE SAME PASSWORD FOR BOTH PARTITIONS, **as you need both windows partitions mounted at the same time**. **Otherwise, you will ruin your windows 7.  Once finished, reboot. At Diskcryptor prompt, press enter and load *buntu. Open terminal and update grub to get rid of windows 7 entries in your grub menu:
[B]
sudo update-grub[/B]

You are done...
 





[FONT=&quot] 
 [/FONT]

---

