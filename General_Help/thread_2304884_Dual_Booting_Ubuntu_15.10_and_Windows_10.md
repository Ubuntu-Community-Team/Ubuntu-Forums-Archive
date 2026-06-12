---
title: "Dual Booting Ubuntu 15.10 and Windows 10"
date: 2015-11-30
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-11-30
Okay I asked this here and not getting a response so any information would be greatly appreciated!  
[h=2]Setting Up Ubuntu 15.10 and Windows 10[/h][COLOR=#000000][INDENT]Okay I know I have to install Windows 10 first before Ubuntu! I setup Windows 10 today then immediately booted to my Ubuntu 15.10 disk which got an error! The 15.10 must be corrupt, but i'v tried downloading it twice and get the same error so I'm using my 15.04 disk and then upgrading. Anyway after installing Windows and then going to Ubuntu I create a 700 GB partition using ext4 and then try to install and get this error. "No root file system is defined. Please correct this from the partition menu." First off I do not know how to get to the partition menu and I do not know how to resolve this! Any help would be greatly appreciated![/INDENT]
[/COLOR]
[COLOR=#000000]
[LIST]
[*][[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/navbit-home.png[/IMG]]("http://ubuntuforums.org/index.php")
[*][Forum]("http://ubuntuforums.org/index.php")
[*][The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")
[*][Other Discussion and Support]("http://ubuntuforums.org/forumdisplay.php?f=423")
[*][Other OS Support and Projects]("http://ubuntuforums.org/forumdisplay.php?f=446")
[*][Other Operating Systems]("http://ubuntuforums.org/forumdisplay.php?f=447")
[*][Windows]("http://ubuntuforums.org/forumdisplay.php?f=170")
[*]Setting Up Ubuntu 15.10 and Windows 10
[/LIST]
[/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by yancek on 2015-11-30
Did you do an md5 checksum on the download of 15.10 to verify the download was good?  Explained at the link below.  The md5sums to compare to are at the second link.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://releases.ubuntu.com/wily/MD5SUMS](http://releases.ubuntu.com/wily/MD5SUMS)

Did you install windows 10 using UEFI?  If so, you must boot Ubuntu UEFI.  Both systems need to be either UEFI or MBR.
Use the manual installation type which is called "Something Else" in Ubuntu.  You will see an option to edit partitions when you click on a partition in the main window.  At that point, select the / symbol for the root filesystem to the right of Mount point.   This is all explained with images at the link below.  Scroll about half way down the page to see it.

 [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

