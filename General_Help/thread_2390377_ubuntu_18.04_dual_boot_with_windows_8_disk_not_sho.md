---
title: "ubuntu 18.04 dual boot with windows 8 disk not showing data of windows"
date: 2018-04-28
forum: General Help
---

### Post by ajay1990 on 2018-04-28
i am using ubuntu 18.04 along with windows 8.i have 1 TB hard disk that has three partition one for ubuntu another for windows and third partition for data that i want to use from both OS and share data among them. but currently i can not see data saved from windows into ubuntu and vice versa. i did change partition to NTFS also but did not share data screen shot of partition attached.
How could i share data among ubuntu and windows with one shared partition i am new to ubuntu.
thanks in advance.

---

### Post by yancek on 2018-04-28
Is the partition you refer to the FAT32 partition shown as sdb3?  There should be no reason why you can't read/write to it from both Ubuntu and windows.  Not sure why you are using FAT32 when ntfs would also work.  It is not likely that you will be able to see data on the Ubuntu partition from windows, that has historically been the case unless you install 3rd party software drivers.  If you are only trying to write to sdb3 and it is failing, what warning/error messages do you see?

---

### Post by ajay1990 on 2018-04-28
data of sdb3 is not being shared even if it is NTFS.as data is available  to ubuntu if data saved by ubuntu and same goes for windows but data  saved by ubuntu is not visible from windows NTFS and FAT 32 both were  checked data locally available to OS but not to other. when i am using  portable hard disk having format of NTFS it is working fine data saved  is shown to other OS. i want to use sdb3 as separate hard disk.

---

### Post by oldfred on 2018-04-28
Check that fast start up is off.
Note that Windows updates may turn it back on.
When Windows is hibernated, the Linux NTFS driver will not mount the NTFS partitions to prevent damage. And if you force write, when Windows restores hiberfile the new data is not recognized.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by ajay1990 on 2018-04-29
my PC is booting in windows and ubuntu. there is no problem with OS.i think you misunderstood.i have problem with data sharing partition.

---

### Post by pqwoerituytrueiwoq on 2018-04-29
I think you missed what oldfrad said
> **oldfred said:**
> Check that fast start up is off.
Note that Windows updates may turn it back on.
When Windows is hibernated, the Linux NTFS driver will not mount the  NTFS partitions to prevent damage. And if you force write, **when Windows  restores hiberfile the [COLOR=#ff0000]new data is not recognized.[/COLOR]**

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by ajay1990 on 2018-04-29
thanks [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("https://ubuntuforums.org/member.php?u=865458") and [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711") i did misunderstood what he was saying for now i found problem. it was because of fast startup of windows because
 

  "When you shut down a computer with Fast Startup enabled, Windows  locks down the Windows hard disk. You won&#8217;t be able to access it from  other operating systems if you have your computer configured to  dual-boot. Even worse, if you boot into another OS and then access or  change anything on the hard disk (or partition) that the hibernating  Windows installation uses, it can cause corruption. If you&#8217;re dual  booting, it&#8217;s best not to use Fast Startup or Hibernation at all."


  disabled fast startup from control panel > system & security  > power option >what power button do > unchecked checkbox and now it is working fine.
thanks for useful links.
Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.p...2#post13488472]("http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472")
[http://www.tenforums.com/tutorials/4...dows-10-a.html]("http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html")
[http://www.tenforums.com/tutorials/2...dows-10-a.html]("http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html")

---

### Post by ragallo on 2019-02-17
Thnks. 

I can solve it with that info!

---

