---
title: "How to recover NTFS partitions after Installing Ubuntu"
date: 2016-12-25
forum: General Help
---

### Post by Mohamed_Saber on 2016-12-25
Usually I install Ubuntu Alongside windows , this time I decide to  make Ubuntu the main system so I choose erase disk blah blah option  which has a description say "It will delete my documents , photos ,  videos and the windows system" in installation screen , After Ubuntu  successfully installed
  **I found my NTFS partitions [C:,D:,E:,F:] Deleted**

  I know this question is duplicated , but I really don't know how to recover it
  Also TestDisk is not available choice ; Because I'm not going to buy a new hardDisk to recover files on it

  [HR][/HR]  Please I beg you guys, about 200GB of my work and 80GB of programs deleted

---

### Post by papibe on 2016-12-25
Hi Mohamed_Saber.

Could you open a terminal, run this command, and paste back the result? (you can copy/paste the text with your mouse)
```
lsblk
```
Regards.

---

### Post by oldfred on 2016-12-25
You are not going to be able to recover in place.
If attempting to recovery STOP using system. The more you use it, the more your overwrite your data. Only use live installer.

And when Linux installs it uses the entire drive/disk, while small at least some data throughout drive has been overwritten.
In Linux a drive is the entire physical disk. So when it says it is going to erase drive it means everything. You have to use Something Else if you want to manage partitions. Windows confuses issue by calling partitions as drives. 

If your data was valuable you should have been backing it up anyways. So best to have another drive for backup anyway. Hard drive do fail even if just running Windows. 

If deeper search with testdisk shows files that is best case. Other tools often only recovery files by type, not full file name. I used photorec for some text files and it took weeks to sort thru, compare to last backup and update data.
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 

      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

