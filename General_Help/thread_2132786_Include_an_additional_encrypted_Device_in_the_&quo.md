---
title: "Include an additional encrypted Device in the &quot;Startup Decrypting Process&quot;"
date: 2013-04-05
forum: General Help
---

### Post by Steven McTowelie on 2013-04-05
Hi everyone,

I hope this is the right place to ask this question. I've been searching the web for weeks now and I didn't find similar topics in the forum, so I made this new thread.

**What I've done so far:**
I've installed Ubuntu 12.04 LTS with the Alternate Installation CD on my HTPC. As partitioning method, I chose **Guided - use entire disk and set up encrypted LVM** because I wanted to have a fully encrypted system.
I also have a luks encrypted mdadm RAID 5 device which contains all my video and audio files. At the moment I have to enter a password for the root partition on startup and after having logged in, I have to manually mount my data RAID device (from command line, since I use XBMC as HTPC user session).

**What I would like to do:**
_I only want to type in one password at boot time but I want to decrypt the boot partition and the encrypted data RAID at the same time._
I read that it is possible to decrypt other devices with key derivation. I tried several steps mentioned in wikis but I didn't get it to work. I probably don't have enough knowledge about fstab and crypttab and how these two files work together.

Does anybody know a way to achieve this?

---

### Post by Steven McTowelie on 2013-04-11
I've figured it out (with the help of this German wiki page: [http://wiki.ubuntuusers.de/LUKS/Schl%C3%BCsselableitung](http://wiki.ubuntuusers.de/LUKS/Schl%C3%BCsselableitung)). If anyone else is interested, here is a short walk through:
(I'm not a Linux pro - any suggestions on how it might have been done better are welcome).


_[SIZE=3]**Step 1**[/SIZE]_

Open [COLOR=#a52a2a]**/etc/crypttab**[/COLOR] in order to find out what "mapper name" your root partition has:
[COLOR=#000080][SIZE=2][FONT=courier new]**vi /etc/crypttab**[/FONT][/SIZE][/COLOR]

You should then be able to see an entry like this one (the xxxxx... stands for the disk's UUID):
[COLOR=#006400]**sda5_crypt UUID=**[/COLOR][COLOR=#a52a2a]**xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx**[/COLOR][COLOR=#006400]** none luks**[/COLOR]

(So in my case the encrypted root partition's name is [COLOR=#a52a2a]**sda5_crypt**[/COLOR].)



_[SIZE=3]**Step 2**[/SIZE]_
The next step is to derive the encryption key into the already encrypted drive. 

[COLOR=#000080][FONT=courier new][B]sudo -i
mkdir /mnt/ram && mount -t ramfs -o size=1m ramfs /mnt/ram && chmod 600 /mnt/ram
/lib/cryptsetup/scripts/decrypt_derived [/B][/FONT][/COLOR][COLOR=#a52a2a][FONT=courier new]**sda5_crypt**[/FONT][/COLOR][COLOR=#000080][FONT=courier new]** > /mnt/ram/tmp.key && cryptsetup luksAddKey /dev/disk/by-uuid/**[/FONT][/COLOR][COLOR=#a52a2a][FONT=courier new]**UUID-OF-YOUR-ENCRYPTED-DISK-YOU-WANT-TO-DECRYPT-ON-STARTUP-TOGETHER-WITH-BOOT**[/FONT][/COLOR][COLOR=#000080][FONT=courier new][B] /mnt/ram/tmp.key && rm /mnt/ram/tmp.key

[/B][/FONT][/COLOR]**[COLOR=#ff0000]EDIT:[/COLOR]**
You don't need to use the UUID here; It should also work this way
[COLOR=#000080][FONT=courier new]**/lib/cryptsetup/scripts/decrypt_derived **[/FONT][/COLOR][COLOR=#a52a2a][FONT=courier new]**sda5_crypt**[/FONT][/COLOR][COLOR=#000080][FONT=courier new]** > /mnt/ram/tmp.key && cryptsetup luksAddKey /dev/**[/FONT][/COLOR][COLOR=#a52a2a][FONT=courier new]**sd**[/FONT][/COLOR][COLOR=#000080][FONT=courier new]**[COLOR=#a52a2a]X1/2/...[/COLOR] /mnt/ram/tmp.key && rm /mnt/ram/tmp.key**[/FONT][/COLOR][COLOR=#ff0000][FONT=courier new][B]
(END EDIT)[/B][/FONT][/COLOR][COLOR=#000080][FONT=courier new][B]

umount /mnt/ram && rmdir /mnt/ram[/B][/FONT][/COLOR]

You will be asked to type in the password for your encrypted disk which you should type in of course.



[SIZE=3]_**Step 3**_[/SIZE]
Next thing I did was editing the file** [COLOR=#a52a2a]/etc/fstab[/COLOR]** (I'm not sure whether this is necessary).
 [COLOR=#000080]**[FONT=courier new]vi /etc/fstab[/FONT]**[/COLOR]  or[FONT=courier new] [COLOR=#000080]**sudo vi /etc/fstab**[/COLOR][/FONT] if you're no t in sudo mode anymore

Add a new line with the following:
[COLOR=#006400]**/dev/mapper/MAPPER-NAME-OF-YOUR-ENCRYPTED-DISK /mnt/MOINTPOINT-DIRECTORY ext2/3/4 defaults 0 1**[/COLOR]

(Of course the directory in [COLOR=#a52a2a]**/mnt**[/COLOR] needs to be created first. In my case the line I added was the following:
[COLOR=#006400]**/dev/mapper/data /mnt/data ext4 defaults 0 1**[/COLOR]
since I always mounted my **[COLOR=#006400]ext4[/COLOR]** formatted data RAID with these commands:
[COLOR=#000080][B][FONT=courier new]sudo cryptsetup luksOpen /dev/md/0 data
sudo mount /dev/mapper/data /mnt/data
[/FONT][/B][/COLOR]
Save the file by typing **[COLOR=#006400]:wq![/COLOR]**



[SIZE=3]_**Step 4**_[/SIZE]
Re-open the file [COLOR=#a52a2a]**/etc/crypttab**[/COLOR].
[COLOR=#000080]**[FONT=courier new]vi /etc/crypttab[/FONT]**[/COLOR] or[FONT=courier new] [COLOR=#000080]**sudo vi /etc/crypttab**[/COLOR][/FONT] if you're not in sudo mode anymore.

Add a new line with the following:
[COLOR=#006400]**data UUID=**[/COLOR][COLOR=#a52a2a][FONT=courier new]**UUID-OF-YOUR-ENCRYPTED-DISK-YOU-WANT-TO-DECRYPT-ON-STARTUP-TOGETHER-WITH-BOOT sda5_crypt**[/FONT][/COLOR] **[COLOR=#006400]luks,keyscript=/lib/cryptsetup/scripts/decrypt_derived[/COLOR]**

Save the file by tpying [B][COLOR=#006400]:wq!
[/COLOR][U][SIZE=3]

Step 5
[/SIZE][/U][/B]Refresh the boot/start files and reboot with this/these command(s);
 [COLOR=#000080]**update-initramfs -u -k all && init 6**[/COLOR] or [COLOR=#000080]**sudo update-initramfs -u -k all && sudo init 6**[/COLOR] if you're not in sudo mode anymore.


That's it. I hope it's useful for some security obsessed people out there :)

---

