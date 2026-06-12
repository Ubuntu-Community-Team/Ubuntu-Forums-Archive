---
title: "No win 7 option in grub"
date: 2012-11-19
forum: General Help
---

### Post by BAGGS8880 on 2012-11-19
I had a problem  yesterday starting windows from the grub menu it would give me an error. So after searching for a solution i came across a post that just said to reinstall Linux alongside windows, so I did and it worked. So today I got to work and started my laptop up and it booted straight into Linux. I thought that was weird so i restarted  and same thing no grub menu just straight into Linux. I found a post that said  hold shift on startup to see grub and i did that but the grub menu it brings up doesn't have windows 7 listed. I've been looking around but haven't found anything that works and my boss is giving me hell for not getting work done fml, thats what he gets for making us use our personal computers i guess. Any help would be greatly appreciated.

-Tom

---

### Post by BAGGS8880 on 2012-11-19
I just tried updating grub, it didn't work

---

### Post by BAGGS8880 on 2012-11-19
I just tried using my windows 7 installation cd to get into widows repair but it just goes to lunix ( yes i selected boot from cd)

---

### Post by oldfred on 2012-11-19
You can install this to your Ubuntu install, liveCD/USB flash drive,  or download a full repair ISO.

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by BAGGS8880 on 2012-11-19
[http://paste.ubuntu.com/1370680/](http://paste.ubuntu.com/1370680/)

---

### Post by BAGGS8880 on 2012-11-19
Ok I did the boot repair and now the grub menu comes up like its supposed to on startup, but still no windows 7

---

### Post by BAGGS8880 on 2012-11-19
i honestly don't know where to go from this point. can anybody point me in the right direction?

---

### Post by BAGGS8880 on 2012-11-19
so i was looking into the boot info report and although most of that looks like an alien language to me i take it that it doesn't bode well for me that my windows partition  was sda4 and it doesn't show up on there all i see is sda 1,2, & 5.   Does this mean i lost everything?

---

### Post by oldfred on 2012-11-19
When you installed Ubuntu you did not install along side, but to the entire drive. It gave you warnings that it was going to erase everything.

If you want to try to recover something, STOP USING hard drive.

You may be able to use testdisk to restore partitions, but any parts overwritten will be gone. Unlikely that system will boot. You may be able to recover some files. Linux installs are not large, but place files all over the drive.

If testdisk does not recover partition(s), you also may be able to use photorec to find files. It only finds file extensions and takes a very long time as it scans entire drive for anything that looks like a file. You also have to have another drive with enough room as it will copy a lot of files.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

    
       repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
    
       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

    
       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

---

### Post by Rebelli0us on 2012-11-19
You can install Grub Customizer.

---

