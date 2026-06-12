---
title: "loading EXT3 into Windows Vista"
date: 2006-08-14
forum: General Help
---

### Post by Elrohir on 2006-08-14
just wondering, there any other Beta Tester that has successfully loaded an ext3 partition into Windows Vista?
 
already tried ext2fs project with no success... any other idea?

---

### Post by Elrohir on 2006-08-20
guess no one has done it...

---

### Post by tuxcantfly on 2006-08-20
have you tried ext2fsd?

---

### Post by Sam on 2006-08-21
I haven't tried it yet, but there is also [Ext2IFS](http://fs-driver.org/).

---

### Post by Elrohir on 2006-09-08
I'll give this last one a try...

but for now, I'll wait until RC1 comes out for public and then I'll give it a shot once again...

---

### Post by justinlilly on 2007-05-10
confirmed: ext2IFS does work in Windows Vista Business 32-bit edition

---

### Post by Elrohir on 2007-05-12
Confirmed since RC1... ;) but good to know that on release versions it keeps working...

just one question, does it install right away or installer has to be modified to Recommended values?

---

### Post by Hairy_Palms on 2007-05-12
also what i use is explore2fs, 
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

although i have recently switched back to XP for games, vista makes me sad.

---

### Post by akvik on 2007-05-14
Hi,

when ext2ifs is already installed in XP and you do an upgrade, it works, but the installer won't allow you to install it in vista if you haven't done so already in XP before the upgrade. Or has anyone managed to install it in Vista straight up?

---

### Post by MoxJet on 2007-05-14
You can install ext2ifs under Vista by right clicking on the .exe install file and find some option to make it run under faked XP environments.

I'm sorry if that was not what you asked for.

---

### Post by dannymichel on 2007-06-27
ext2ifs is useless.
It doesn't work on Vista 64 Bit.
What's the point?

---

### Post by Qu4k3R on 2007-06-27
I had.

I have successfully installed an ext3 partition into Win Vista (Business) and Ultimate.

Just run the ext2ifs ([http://www.fs-driver.org/](http://www.fs-driver.org/)) with compatibility mode for windows XP and Administrative Privileges.
It should be easy and run as like as if you would be using win xp.

PS:
I hope it works.

Be aware that windows files are not case-sensitive and Linux files are case-sensitive.

PS: on 32 bit version (not 64 bit) I think :s

---

### Post by dannymichel on 2007-06-27
> **Qu4k3R said:**
> I had.

I have successfully installed an ext3 partition into Win Vista (Business) and Ultimate.

Just run the ext2ifs ([http://www.fs-driver.org/](http://www.fs-driver.org/)) with compatibility mode for windows XP and Administrative Privileges.
It should be easy and run as like as if you would be using win xp.

PS:
I hope it works.

Be aware that windows files are not case-sensitive and Linux files are case-sensitive.

PS: on 32 bit version (not 64 bit) I think :s
There you go.

---

### Post by syxbit on 2007-06-27
fs-driver.org was great back on XP, but it's pretty terrible on Vista.
the so called update to fix this (and x64 is taking a while to arrive)
everytime i reboot vista, the drive i mounted to is gone, so i have to remount.
the problem is, i can't remount to the same letter, so i have to keep going down the alphabet....eventually i'm going to run out of letters!

---

### Post by Qu4k3R on 2007-06-27
EDIT: You could initiate your ext3 - mount program at the startup :s
The manual might tell you about that.

---

### Post by MushyMaestro on 2007-07-01
*Post Deleted*

---

### Post by aaniao999 on 2007-07-01
thx, i use "Explore2fs" , it works now , right click on the exe file, & select run with administrator, 
& i seclect WIN XP SP2 MODE, (i do not know if it is needed), thnx all, i'm new here

---

### Post by 4tro on 2007-07-06
i was able to install ext2IFS under vista,
it complained that the software might not be installed properly, adn after i tried it again with recommend settings it installed normally :S
it doesn't work however... can Vista please Die a slow and painfull death?
i still have a legal disk of xp pro, but it's a upgrade-disk
can I upgrade Vista to XP pro?
explore2fs does work with admin rights nicely ^_^

---

### Post by ShirishAg75 on 2007-07-09
Another thing as I constantly format/jump to the next release as & when things hit stable I have to always unload the ext2ifs driver. Reload it & it finds the ext2/3 partition. There are rumored to be some updates on fs-driver but no roadmap on the site yet :(

---

### Post by Johnathan Yew on 2007-07-15
Hi Friends,

After setting the compatibility of the install exe file you can install ext2ifs and mount the ext2/3 partitions but you will encounter a rundll32 error in the control panel ifstool icon. So you will not be able to access the ifstool after that. Use this workaround to get it to work, not elegant but does the job.

[http://www.reviewingit.com/index.php/content/view/52/1/](http://www.reviewingit.com/index.php/content/view/52/1/)

:popcorn:

---

### Post by jss1941 on 2007-07-21
I was able to install the XP/SP2-compatible version of ext2isf into Vista.  My Ext3 partition comes up in read/write mode on booting Vista.  If I invoke the driver from the CP, then I do get the run32dll error message, but it doesn't seem to affect correct perfpormance at boot time.

Thanks to those in this thread that pointed out that one needs to change the installer properties to enable XP compatibility.

---

### Post by cvmostert on 2007-09-19
> **justinlilly said:**
> confirmed: ext2IFS does work in Windows Vista Business 32-bit edition

dont know what vista this pc has but it does not work for me... does not even want to install.. i will have to seek for the vista installs..

---

### Post by brandonjp on 2007-11-03
first off, let me say that the Ext2IFS driver from [fs-driver.org](fs-driver.org) is very very amazing - i've been using it for over a year with no problems (in winXP) - However, we're still waiting to get it functioning properly in Vista....so I put these three articles together:
[INDENT]- [http://ubuntuforums.org/showthread.php?t=236274]("http://ubuntuforums.org/showthread.php?t=236274")
- [http://ubuntuforums.org/showthread.php?t=410291]("http://ubuntuforums.org/showthread.php?t=410291")
- [http://www.reviewingit.com/index.php/content/view/52/1/]("http://www.reviewingit.com/index.php/content/view/52/1/")[/INDENT]

and in the meantime you can use the tips from that third link to get **access to the EXT2IFS control panel app in Vista**:
[INDENT] - make a copy of your 'rundll32.exe' file (i called mine 'rundll32xp.exe'), then right click on it and set it to: Compatability for Windows XP and Run as Administrator - Make sure you save this new file in the same folder as the original rundll32.exe -- C:\Windows\System32
 - create a new text file and save it as 'something.bat' (i called mine 'ext2ifs.bat') and  in the file put:
```
rundll32xp.exe shell32.dll,Control_RunDLL c:\windows\system32\ifsdrives.cpl
```
where the 'rundll32xp.exe' part will be whatever your copied rundll32 file was called
 - then you'll need need to right click on your .bat file and select 'Run as Administrator'
- now you can change the Ext2IFS drive settings[/INDENT]

ALSO...if you need to **UNINSTALL the IFS Driver in Vista's Remove Programs **you'll get an error saying something about CPL legacy when using Vista's Add or Remove Programs control panel app....here's the workaround for that (as always be careful editing your registry):
[INDENT] - in the Registry Editor (regedit.exe) find the following entry: ```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Ext2Ifs_for_NT501]
```
 - under that entry you'll find:   "UninstallString"="RunDll32..... 
 - simply change the "RunDll32" to whatever your new XP compatible rundll file was called - for example, my full line changed to:  ```
"UninstallString"="RunDll32xp setupapi.dll,InstallHinfSection DefaultUninstall 130 Ext2Ifs_for_NT501.inf"
```
 - now you should be able to easily remove the EXT2 IFS Driver from your Windows Vista Control Panel > Remove Programs[/INDENT]

but...i'm still hoping for a fully Vista compatible version of the driver from fs-driver.org
--bp

---

### Post by ThA-LaN-LaW on 2007-12-20
Hi,

this howto work very nice!
But if i execute an *.exe File(s) on the ext3 Filesystem, Vista show an error.
Has someone else these problem?

Thanks and Greetz, TLL.

---

### Post by brandonjp on 2007-12-20
> **ThA-LaN-LaW said:**
> Hi,

this howto work very nice!
But if i execute an *.exe File(s) on the ext3 Filesystem, Vista show an error.
Has someone else these problem?

Thanks and Greetz, TLL.

You know...I ended up having so many problems with the ext filesystems under Vista that I finally formatted and installed Vista again from scratch without using an ext3 drive in Vista - then about 3 days later I got so fed up with Vista in general that I formatted again and went back to XP

---

### Post by ames89 on 2008-01-15
omg is that so bad vista???

so many money to buy a thing that even not work, i guess that mac almost work better ><...(never tried mac)

---

### Post by redlabour on 2008-02-10
> **ames89 said:**
> omg is that so bad vista???

so many money to buy a thing that even not work, i guess that mac almost work better ><...(never tried mac)

The only Thing that is not working is the Ext2IFS Driver for Vista. It is not a failure of Vista.

---

### Post by ediulia on 2008-03-03
windows vista sp1 doesn't support this program.

---

### Post by redlabour on 2008-03-03
[http://www.ext2fsd.com](http://www.ext2fsd.com)

works great with Vista Ultimate 32bit and Servicepack 1!!!

---

### Post by Dax0r on 2008-06-06
> **redlabour said:**
> [http://www.ext2fsd.com](http://www.ext2fsd.com)

works great with Vista Ultimate 32bit and Servicepack 1!!!

are u sure?

---

