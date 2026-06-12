---
title: "GPT partition issue in usb external sata hard disk"
date: 2014-06-09
forum: General Help
---

### Post by bingo999 on 2014-06-09
i have a West Digit 1T sata disk and need to get all the data out from this disk. The disk was "GPT" partitioned. 

I tried Windows 8 but no luck... I installed Ubuntu in VMware and connected the harddisk via usb,  Ubuntu can detect it successfully and list all the partitions. However, only number 1 partition was ext3 and can mount it. All other partitions whose "File System" was empty. I opened the mount of partition 1 but was disappointed that the data was not what i needed. the real data could probably in partition 6, but i don't know how to access it, can anyone tell me how to mount/access partition 6?  thanks a lot!

[COLOR=#000000][FONT=Arial][IMG]https://lh4.googleusercontent.com/239EW9uuVIS6H8wQALxOw_VF8KsmGGqCQQMuhHf9TQAbkTFLTXgpjfDp_CiYGdL-T_kQVXHxv6xBcr-hsF2L3dBETw_GwYhhYrU_w0LF42u-bmZyYAak-NpoG7qGBZ-kKw[/IMG][/FONT][/COLOR] 

[COLOR=#000000][FONT=Arial][IMG]https://lh5.googleusercontent.com/TIfoHHUEYckpVDjNNK-LdmjDniLc1VCGLzGtdh3QLL2trFGPcTny-eD1JtwSdXqk6zNrFuxzVAJVVwBpwzuPdoXb6alj_fXXfOBQH1rd8vw-8dv-oAuk6twZ5yXWQZJLyw[/IMG][/FONT][/COLOR]

---

### Post by oldfred on 2014-06-09
What does gdisk show?
You probably have to install gdisk
sudo apt-get install gdisk
sudo gdisk -l /dev/sdb

 [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

      
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

All those little partitions look like they may be invalid, but then are they corrupting the main partition?

---

### Post by bingo999 on 2014-06-09
[COLOR=#000000][FONT=Arial][IMG]https://lh5.googleusercontent.com/oBCPFUVXkCYrcMlXX1QyYYKypDZHuFPbTyYu71oqowOxiQcw65l0iG8_PeKl6Xplb6RI0v6-5we5EWiFaI1YAa594FPfpwgoE9Unph5gTx3FgNxneZd65BY6m8JRAfdBsg[/IMG][/FONT][/COLOR]

---

### Post by bingo999 on 2014-06-09
Can anyone suggest how can i mount/access the data in partition 6?

---

### Post by oldfred on 2014-06-09
Please do not post screen shots of terminal, just copy & paste. If long then use code tags which are easy to add in advanced editor using # icon. Or if a screen shot attach with paperclip icon.

Gdisk is not showing any mismatch between primary gpt partition table and its backup.

I would then see if testdisk shows anything. Choose the efi-gpt at the partition type screen.
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

