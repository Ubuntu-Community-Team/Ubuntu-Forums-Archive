---
title: "Windows 7, Ubuntu 12.04 and 14.04 operating systems - Not all in the boot-up menu."
date: 2015-07-08
forum: General Help
---

### Post by stuart18 on 2015-07-08
I have Windows 7 and Ubuntu 12.04 and 14.04 systems on my computer.  After installing Ubuntu 14.04, it would not show the new version.  Below is some boot information that may help identify the problem.  Thanks.

[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"][/TD]
[TD="class: code"][COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 9Feb2015[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos5[COLOR=#666666])[/COLOR]/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS 
    Boot files:        /etc/fstab

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *          2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2           3,074,048   486,225,919   483,151,872   7 NTFS / exFAT / HPFS
/dev/sda3         944,003,072   976,771,071    32,768,000   7 NTFS / exFAT / HPFS
/dev/sda4         486,227,966   944,003,071   457,775,106   5 Extended
/dev/sda5         486,227,968   588,797,951   102,569,984  83 Linux
/dev/sda6         927,465,472   944,003,071    16,537,600  82 Linux swap / Solaris
/dev/sda7         588,800,000   927,463,423   338,663,424  83 Linux[/COLOR][/TD]
[/TR]
[/TABLE]

---

### Post by monkeybrain20122 on 2015-07-08
You have ubuntu 12.04 controlling boot, right? Just boot into it and run in the terminal

```
sudo update-grub
```

Why do you need 12.04 and 14.04?

---

### Post by oldfred on 2015-07-08
If the sudo update-grub does not find other install, please post link to full Summary report from Boot-Repair. 
If posting terminal output please use code tags. Code tags are easy to add if using the Advanced Editor with the # icon.

---

### Post by stuart18 on 2015-07-09
The update-grub did not work.  Here's a link to the full summary report from boot-repair.  I'd like to  boot up from the 14.04 version.  

paste.ubuntu.com/11845509

---

### Post by oldfred on 2015-07-09
[http://paste.ubuntu.com/11845509](http://paste.ubuntu.com/11845509)

Use Boot-Repairs advanced mode and choose install in sda7. You are not showing any grub files in that install?  Did it otherwise complete the install? If so run the full uninstall/reinstall of grub2 using sda7.

Your install of 12.10 is obsolete. So it will not update any more. end of life: [May 16, 2014]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2014-April/002488.html")
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

