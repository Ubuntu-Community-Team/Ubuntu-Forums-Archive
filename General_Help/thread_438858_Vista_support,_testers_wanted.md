---
title: "Vista support, testers wanted"
date: 2007-05-10
forum: General Help
---

### Post by ago on 2007-05-10
It should be possible to make grldr work with Vista, which means that it should be possible to have Wubi working with Vista but at the moment it is a manual operation. Here are the instructions courtesy of grub4dos:

[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_Vista_boot_manager](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_Vista_boot_manager)

1. Run wubi as usual
2. Before rebboting, use bcdedit to configure the startup menu: 

```

bcdedit /create /d "Ubuntu" /application bootsector
bcdedit /set {id} device boot
bcdedit /set {id} path \grldr.mbr
bcdedit /displayorder {id} /addlast

```

Then copy grldr.mbr to C:\, grldr and menu.lst to the root directory of any FAT16/FAT32/NTFS/EXT2 partition. grldr.mbr can also be used to start GRUB for DOS in Windows NT/2000/XP/2003 (in fact, grldr.mbr is basicly the first 16 sectors of grldr). To use grldr.mbr as the boot file, use the following line in boot.ini: 

   C:\grldr.mbr="Start GRUB4DOS"
As in Windows Vista, you need to copy grldr and menu.lst to the root directory of any FAT16/FAT32/NTFS/EXT2 partition.


NOTE1: You will find the relevant files in [http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/) . Use the menu.lst file that comes with wubi (c:\wubi\boot\grub\menu.lst).

NOTE2: you need to replace the {id} with a number. I guess the id number is returned by the first command.

NOTE3:  these commands need elevated privileges, they should be used inside cmd.exe which is started with "Run as administrator".


Let us know how it goes

---

### Post by nevarath on 2007-05-10
I was introduced to wubi by a friend using Vista,so i think the current wubi already supports vista,and my friend is not dual-booting. hes pure vista..

He is using Vista Ultimate for your info.

---

### Post by ago on 2007-05-10
> **nevarath said:**
> i think the current wubi already supports vista..

Only if XP is also installed. The above should work with Vista, even without XP.

---

### Post by ago on 2007-05-11
hmm nobody with vista? Is it that bad?

---

### Post by leibowitz on 2007-05-11
Yes, it is.

(I'm trying to add an entry in the Vista Beta right now)

---

### Post by leibowitz on 2007-05-11
Right now: I can't boot the entry.

Why: some error in the boot manager. This entry shows something related to a file not found (if I remember correctly). 

Note: I first try to install wubi from windows xp because I knew it was not supporting vista. Anyway it did add an entry to the vista boot menu (I don't know how). But this entry did the same way, not bootable.

Note²: wubi did add a new entry in the windows xp old boot manager aswell. This entry boots, but hangs during the boot. I will report the error message later, but it seems related to something important (for me).

I have 5 partitions in an SATA disk

1) Windows XP
2) Linux Ext3
3) Extended
-5)Vista
-6)Swap

When booting from XP, C:\ is 1) and D:\ is 5)
When booting from Vista, C:\ is 5) and D:\ is 1)

I think it may be related to some errors I have... but don't know at all so I must investigate further.

This is what I did
> 
-Boot XP
-Download wubi 7.04 test1
-Download alternate 7.04 iso
-Start wubi install
-reboot
-try to select Ubuntu in vista boot loader (failed to start, bootloader related)
-try to select Ubuntu in Old legacy (Xp) boot loader (failed during the boot, boot mgr related)

-boot in Vista
-start a cmd.exe from start menu (I think it's from an administrator account because no error reported)
1) bcdedit /create /d "Start GRUB4DOS" /application bootsector
> Shows an id like this {45dza54az65d41ad}
Copy paste this id in 2, 3, and 4)
2) bcdedit /set {id} device boot
3) bcdedit /set {id} path \grldr.mbr
4) bcdedit /displayorder {id} /addlast


That successfully added an entry in the vista boot loader, but it cannot boot.

I did put grldr.mbr from the archive ( [http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-09.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-09.zip) ) into the Vista c:\ (that is partition 5, don't be fooled by vista naming partition) 
Then just did nothing for grldr and menu.lst because it has already been copied to C:\ (XP that is partition 1) during wubi process from wubi-7.04-test1.exe

I like to remember that lady in the 5th element in the film of the same name, in the Cab with Bruce Willis. She was praying bruce for help saying... "Please, help!"

---

### Post by ago on 2007-05-11
I would test it first with a very simple menu.lst that simply launches grub commandline, not with full blown wubi. If it works with the commandline then it should be easier to see how to make it work with wubi.

---

### Post by leibowitz on 2007-05-11
I checked the menu.lst put on the c:\ (whatever it is) 

The configuration is weird, only three lines. And it does look for another menu.lst which is in the c:\boot\wubi\..\menu.lst

Then it loads this menu.lst

Which is even more weird, consisted of another look for linux now.

That's kind of unexpected behavior for me. And even if I read what grub4dos is.

> At startup, boot code in grldr.mbr will dynamically scan the root directory of every local partition for grldr, and load the first one found. Using this scheme, the location of boot file is no longer fixed, users can move it across partition boundary without causing booting problems.

Great, but I do not understand why it can't do that with one menu.lst only.

What should I put in the c:\menu.lst file to have a minimalist configuration to see if it loads.

Anyway I think it doesn't load grub4dos at all from the vista boot loader. The error is

grldr.mbr File missing or corrupt

I will try placing it in both disk (vista and xp)

---

### Post by leibowitz on 2007-05-11
It works.

I just put grldr.mbr in the partition 1) (Windows Xp)

Now all files are on this partition. That's ok since it's the system partition for Vista (containing the boot files)

The XP partition contains each files
menu.lst
grldr.mbr
grldr

And ubuntu is loaded from Vista boot loader.

Everything seems ok. Anything else to try ?

---

### Post by ago on 2007-05-11
timeout 10
default 0

title Command Line
commandline

---

### Post by ago on 2007-05-11
> **leibowitz said:**
> It works.

I just put grldr.mbr in the partition 1) (Windows Xp)

Can you try to use only Vista partition? Our target are users with only Vista installed on a single partition

---

### Post by leibowitz on 2007-05-11
Can't.

As I said earlier, Windows use the first partition of the primary disk of the system for it's boot files. Whatever it is.

So if you have Vista only, you just have to put every files on the c:\

But as for me, I need to put them on the Xp partition (that's the first partition of the disk).

PS: if your first partition is a linux and you put them there, I think grub will not find them. At least AFAIK

---

### Post by ago on 2007-05-11
Thanks, that will help.

---

### Post by Spegelius on 2007-05-11
Ok, i finally dug up my Vista DVD and painstakingly restored Vista bootmanager. Once Vista booted, edited bcd as instructed and copied grldr files to WindowsXP partition, as it is the active partition and Vista bcd is installed to it.

Rebooted and chose Ubuntu. Ubuntu menu was displayed and i chose the kernel i usually use. Some stuff about sector mismatches was displayed, but it booted and seemed to work fine in Ubuntu. I'll try to get the error messages written down when i have time to fool around with it.

---

### Post by ago on 2007-05-11
Since none of us has vista I'll assign this bug to you [https://bugs.launchpad.net/wubi/+bug/113297](https://bugs.launchpad.net/wubi/+bug/113297)
Relevant files are in wubi/src/installer. I am sure Ecology2007 will also be able to help out on that.

---

### Post by MethodOne on 2007-05-12
I installed Wubi 7.04-test2 in Windows Vista as usual, but followed the instructions in the first post to get it to boot.  After installation, I got a full-working desktop.

---

### Post by BK553 on 2007-05-12
Just wanted to let you guys know, the technique in the first post worked perfectly.  I have vista installed on one drive, no XP or anything else.  The initial install gave the "cannot find file" when Ubuntu was selected in the boot screen, but after following the steps and rebooting, it booted right up.The only issue I can see is that I after following the step i had two entries for Ubuntu in the startup manager, one working and one not.  I had to remove the first one manually.  I see no reason you guys couldn't write a batch file to perform these steps in vista installations, and include the files needed to make it work.

---

### Post by Jerick on 2007-05-13
Hi, I put in the settings, and yes I was able to go into the installer. However when it was formatting it appeared as if it froze and I am assuming it wasn't doing something right. so I came back and here is how I set it up:

-I had used the test2 wanting to install wubi onto my C:\ although I put those extra two files into a logical drive (should I have done that?) when it said "
Then copy grldr.mbr to C:\, grldr and menu.lst to the root directory of any FAT16/FAT32/NTFS/EXT2 partition" and, I did. But all I know is it worked and I think I need to get those drives reformatted.

Edit: I must have done something wrong, because after deleting those two partitions that were created, I rebooted to go into it again and it said it couldn't read the alternative iso, and it went into a kernel panic. What should I do? Well I'm going to reinstall wubi to see what happens.

Edit2: Apparently it isn't  what I did that messed it up, cause it happens again. When its formatting the home partition, it freezes at 83% and no HDD I/O happens. Is this a bug, and if it is, it it a known one? I'll look around.

Edit3: possibly final edit: I see that there is in fact something known about this, so besides the fact that that is occurring, it at least boots into it. :)

---

### Post by STREETURCHINE on 2007-05-13
> **ago said:**
> hmm nobody with vista? Is it that bad?

it only had a life span of 3.5 days on my computer,i reinstalled xp now i have to ring them again and validate it again:(

---

### Post by Jerick on 2007-05-13
...SUCCESS! After redownloading the iso file, I managed to install Kubuntu through Wubi via Vista using the instructions (: it works pretty well.

---

### Post by ago on 2007-05-14
Here is a build that includes preliminary Vista support (untested) , thanks to ecology2007.

[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.8.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.8.exe)

try it out and let us know.

---

### Post by XOSag on 2007-05-15
ago, I'm currently downloading the iso through the installer. My connection isn't great, but hopefully I'll be able to see whether it works or not in ~4 hours.

---

### Post by ago on 2007-05-15
Thx. Try with ubuntu

---

### Post by Atae on 2007-05-15
i just tried the miefield 0.8 file with 0 luck, on boot of the Ubuntu option i get an error about grldr being missing or corrupt. All files are accounted for on my main windows vista partition.

---

### Post by XOSag on 2007-05-15
Unfortunately, I have to mirror Atae's experiences; I'm getting an error on the Vista Bootloader (Status: 0xc000007b; will do research on that later), and it's saying that the grldr file is corrupted. 

However, I'm also dual-booting with XP, so when I go to the boot menu, and select the XP option, I see Ubuntu as well. Wubi has added an Ubuntu option to both the Vista **and** the XP bootloaders; Ubuntu loads up fine from the XP bootloader.

---

### Post by ago on 2007-05-16
Can you guys can try to "integrate" with the instructions above and see if anything is missing? We have no vista and are walking blind.

---

### Post by ecology2007 on 2007-05-16
Atae, XosAg can you tell me if you see a file named grldr.mbr on your vista drive ?


I also need to know 
how many partitions you have.
which is your primary boot drive.
where is vista.
where is xp.
where is wubi.
on how many drives you have ntldr and boot.ini.
and the more details you can think of.

I also need you to launch regedit.exe and browse to
HKLM "Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi" "bootmgr" and tell me the content of it.

As soon as i have it, i will add the code to take your setup into account.

---

### Post by XOSag on 2007-05-16
ecology2007:

On the main Vista drive, I don't see a grldr.mbr (this is with show hidden files/show system files checked. grldr.mbr is only present in the winboot section of the Wubi folder).

I have 3 partitions:
C = primary boot drive/vista drive/Wubi drive 
D = XP drive
E = XP logical drive

I'm only seeing ntldr and boot.ini on the XP partition. I suppose this is because Vista uses the first partition for boot files, as leibowitz stated earlier.

There is no "bootmgr" string value in HKLM "Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi", but there is a BootDrive, which says "D:" (the xp partition). 

ago, integration works perfectly after putting my boot files into the XP drive. I'm experiencing the same thing as leibowitz.

---

### Post by ecology2007 on 2007-05-16
New revision will be up in a few minutes.

---

### Post by ecology2007 on 2007-05-16
[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.9.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.9.exe)
> 
Erases first 2 Mb of the virtual disks files.
Updated grub4dos files to new revision thanks to bean123 (15 may).
Improved vista detection.
Improved vista support when using both xp and vista.
- Tell me if wubi warns if you have "Vista is detected: support is experimental",
- Inspect the root folder of your drives and tell me on which of them you see grldr, grldr.mbr and menu.lst.
- Tell me what you have under ```
"HKLM "Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi" "VistaBootDrive""
```

---

### Post by Atae on 2007-05-16
I seemed to have solved the problem last night by adding the grldr.mbr to the main partition and using the following in my boot.ini


[operating systems]
c:\grldr.mbr="Ubuntu"
[boot loader]
timeout=15


hope this helps

---

### Post by Atae on 2007-05-16
ok, i started clean with 0.9 with the same problem.


Tell me if wubi warns if you have "Vista is detected: support is experimental": Yes ( Still see registry errors)
 Inspect the root folder of your drives and tell me on which of them you see grldr, grldr.mbr and menu.lst: Yes to all.
I also need to know
I have 2 drives with 3 partitions. 1:Vista 2:NTFS Storage + Mac OS
which is your primary boot drive: Vista
where is vista: c:\windows
where is xp: N/A
where is wubi: C:\wubi\
on how many drives you have ntldr and boot.ini: my main drive has boot.ini but no ntldr.

I have attached my registry screen. I will once again try changing the boot.ini to point to the .mbr file and report. 

**Update**

using the .mbr seemed to let me install but after the install i got an "grub for dos error 17" seems it couldnt find the menu.lst
I will try and reinstall again tommorow.

---

### Post by Spegelius on 2007-05-17
I'll try the latest version if i have time later today.

---

### Post by Dolfhin01 on 2007-05-17
Does NOT work, I get the error that grldr.mbr is missing, might it be due the fact that I use NFTS compresion? I have disabled the compresion on those files but it dindt make any difference.

*Tell me if wubi warns if you have "Vista is detected: support is experimental"*: Yes (It did give an error about not being able to read some valua from registy
*Inspect the root folder of your drives and tell me on which of them you see grldr, grldr.mbr and menu.lst*: Yes
I also need to know
*which is your primary boot drive:* Vista
*where is vista*: c:\windows
*where is wub*i: C:\wubi\
*on how many drives you have ntldr and boot.in*i: 1, My boot drive

Thanks in advance.

edit :
[i]
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]
"InstallationDrive"="C:"
"InstallationDir"="wubi"
"InstDir"="C:\\wubi"
"BootDrive"="C:"
"systemsize"="3"
"homesize"="0.25"
"swapsize"="0.25"
"DisplayName"="Wubi"
"UninstallString"="C:\\wubi\\uninstall.exe"
"VistaBootDrive"=" {f18780c7-03eb-11dc-ba1e-005056c00008"
[/i]

---

### Post by ecology2007 on 2007-05-17
**Does NOT work.**
[I]I need exact description. I know it is annoying, some people take screenshots with a camera, you can do so if you do not want to type the error messages yourself.
[/I][B]
might it be due the fact that I use NFTS compresion?[/B]
[I]Yes, since you have only one drive and if i understand correctly the line for ubuntu was installed in vista bootloader with success.
[/I][B]
It did give an error about not being able to read some valua from registy
[/B]I need exact error message.
[I][B]
"VistaBootDrive"=" {f18780c7-03eb-11dc-ba1e-005056c00008"[/B]
is it 
[/I]* "VistaBootDrive"=" {f18780c7-03eb-11dc-ba1e-005056c00008}" ?*
If not the error is there.

---

### Post by clpo13 on 2007-05-17
All right, I am running Vista and I tried out Wubi today. Here's my experience:

I ran the minefield (Vista) installer, but it still gave me an error regarding grldr when I rebooted. I went back into Vista and followed the manual instructions (including copying grldr.mbr to C:\, which hadn't automatically happened), rebooted, and the Ubuntu installer started right up.

Unfortunately, the installer hung up when it came to automatically configuring my network connection through DHCP. I do have a wired connection, so I don't know why it was hanging up. It was something about a malformed IP address. Anyways, I forced the installation to continue, and things went all right up until the reboot, when the X server failed to start. I know that's a problem with my laptop, so I fixed that up. Interestingly, the fix I did required downloading files and my internet connection worked fine during all of that.

My final problem was when Ubuntu finally started up (X and all). The login screen showed and I logged in with my username and password, but that's all that happened. It looked like it logged me in but stopped doing anything afterwards. No GNOME, nothing except the cursor. It wasn't frozen, but nothing was happening.

I don't know what the problem could be. Any ideas?

---

### Post by Dolfhin01 on 2007-05-18
> **ecology2007 said:**
> **Does NOT work.**
[I]I need exact description. I know it is annoying, some people take screenshots with a camera, you can do so if you do not want to type the error messages yourself.
[/I][B]
might it be due the fact that I use NFTS compresion?[/B]
[I]Yes, since you have only one drive and if i understand correctly the line for ubuntu was installed in vista bootloader with success.
[/I][B]
It did give an error about not being able to read some valua from registy
[/B]I need exact error message.
[I][B]
"VistaBootDrive"=" {f18780c7-03eb-11dc-ba1e-005056c00008"[/B]
is it 
[/I]* "VistaBootDrive"=" {f18780c7-03eb-11dc-ba1e-005056c00008}" ?*
If not the error is there.

I will edit this post with the exact error message in a few minutes (Can't reboot now).

As for the registry settings, I double checked and it is exactly as in my post. I have changed it now and I will reboot in a second to see if things are fixed.

edit :

After selecting the Ubuntu boot option I get (translated from Dutch to English) :

file : \grldr
status : 0x000007b
Information : Could not load the selected application because the application is damaged or missing

The installer gives me this error :

"Can't query regisrty value! (2)"

It contineus withouth problems after that. 

My grldr is 171 kB (175.109 bytes) in size.

I have disabled NFTS compresion on the following files :
grldr
menu.lst
grldr.mbr
boot.ini
c:\wubi

Anything I missed?

Thanks in advance!

---

### Post by Spegelius on 2007-05-19
Ok, i tried the latest 0.9 minefield on my Vista box. First a bug... ;):
 - Wubi doesn't detect alternat iso in some cases. I have the installer + the correct alternate iso on a network mount (\\mount\share\Not Backed Up\Apps) and running the installer from there, the iso is not found. However, moving the iso + installer to root \\mount\share works properly. Don't know if this that important, though...

Anyway, on my Vista box the installer fails and displays a messa: Error while trying to execute: bcdedit.exe.
Also i'm trying to build the installer in Vista but it fails: 

File: Returning to: "..\lupin-dist"
File: "..\lupin-dist\*.*" -> no files found.
Usage: File [/nonfatal] [/a] ([/r] [/x filespec [...]] filespec [...] |
   /oname=outfile one_file_only)
Error in script "H:\Roinaa\Omaa kodausta\wubi\devel\src\wubi.nsi" on line 156 -- aborting creation process

I guess i should have built lupin files before building Wubi?

Edit: got build scripts to work by copying the lupin dist folder contents to lupin-dist under wubi folder.

---

### Post by ecology2007 on 2007-05-19
[B] Edit: got build scripts to work by copying the lupin dist folder contents to lupin-dist under wubi folder.
[/B]
Yes. To build wubi you need :

-under linux, 
Get both lupin and wubi branches from bzr. Run make in lupin folder.
bzr co [http://code.launchpad.net/~lupin-team/lupin/devel](http://code.launchpad.net/~lupin-team/lupin/devel)
bzr co [http://code.launchpad.net/~lupin-team/wubi/devel](http://code.launchpad.net/~lupin-team/wubi/devel)
Run make in wubi folder and point to a valid lupin/dist folder when you are asked.

-under windows,
You need manually copy the content of an allready build lupin/dist folder to wubi/lupin-dist.

---

### Post by ecology2007 on 2007-05-19
[B] Anyway, on my Vista box the installer fails and displays a messa: Error while trying to execute: bcdedit.exe.
Also i'm trying to build the installer in Vista but it fails:

[/B]The error occurs there , in src/installer/make_menu_lst.nsh :
  ```
   nsExec::ExecToStack '"bcdedit" /create /d "Ubuntu" /application bootsector' 
      Pop $0 
      ${If} $0 != 0 
        StrCpy $0 bcdedit.exe 
        MessageBox MB_OK "$(error_exec) $0" 
        Quit
```You can do that to see the actual error
  ```
   nsExec::ExecToStack '"bcdedit" /create /d "Ubuntu" /application bootsector' 
      Pop $0 
      **MessageBox MB_OK "bcedit executed with return message : $0" **
      ${If} $0 != 0 
        StrCpy $0 bcdedit.exe 
        MessageBox MB_OK "$(error_exec) $0" 
        Quit
```

---

### Post by Spegelius on 2007-05-19
Yeah, i've been fiddling with that function. Added also line to execute only bcdedit.exe without any options. No go, only prints 'error' to $0 and $1 is empty (i added that to see if the real output was there) both with and without command parameters. Googling around makes me think that the nsExec function executes everything in non-elevated privileges. Running bcdedit.exe in non-admin command prompt causes following error:

The boot configuration data store could not be opened.
Access is denied.

Executing Wubi installer doesn't pop up the window that normally appears when elevated privileges are required. Only the window askin can this sw be trusted appears. I'll se if there's a way to elevate rights in command prompt.

BTW, my Vista is 64-bit version.

---

### Post by ecology2007 on 2007-05-19
On top of wubi.nsi, you can see :
```
RequestExecutionLevel admin.
```Documentation is here :
> **4.8.1.32 RequestExecutionLevel**

 **none**|user|highest|admin
 Specifies the requested execution level for Windows Vista. The value is embedded in the installer and uninstaller's XML manifest and tells Vista, and probably future versions of Windows, what privileges level the installer requires. *user* requests the a normal user's level with no administrative privileges. *highest* will request the highest execution level available for the current user and will cause Windows to prompt the user to verify privilege escalation. The prompt might request for the user's password. *admin* requests administrator level and will cause Windows to prompt the user as well. Specifying *none*, which is also the default, will keep the manifest empty and let Windows decide which execution level is required. Windows Vista automatically identifies NSIS installers and decides administrator privileges are required. Because of this, *none* and *admin* have virtually the same effect.
  It's recommended, at least by Microsoft, that every application will be marked with the required execution level. Unmarked installers are subject to compatibility mode. Workarounds of this mode include automatically moving any shortcuts created in the user's start menu to all users' start menu. Installers that need not install anything into system folders or write to the local machine registry (HKLM) should specify *user* execution level.
  More information about this topic can be found at MSDN. Keywords include "UAC", "requested execution level", "vista manifest" and "vista security".


[http://nsis.sourceforge.net/Docs/Chapter4.html](http://nsis.sourceforge.net/Docs/Chapter4.html)

---

### Post by Spegelius on 2007-05-19
Not good so far. I found one way to elevate from cmdline and it's an external program (needs Visual studio to compile?): [http://www.wintellect.com/cs/blogs/jrobbins/archive/2007/03/27/elevate-a-process-at-the-command-line-in-vista.aspx](http://www.wintellect.com/cs/blogs/jrobbins/archive/2007/03/27/elevate-a-process-at-the-command-line-in-vista.aspx)

I'm stuck untill i can get the nsExec to execute commands as admin. Running Wubi as Admin doesn't help.

Edit: 'RequestExecutionLevel admin' is allready defined on the latest bzr source. Doesn't do a thing...

---

### Post by ecology2007 on 2007-05-19
Ok, i see.After all, It is normal  that bcedit is prevented from being run by external software.
Can you run manually the bcedit commands in a dos box, and confirm the approach we use is valid ?

---

### Post by Spegelius on 2007-05-22
I built the latest bzr codes of Wubi and tried it on Vista; same error message is printed when trying to execute bcdedit.exe. I searched for a solution to execute bcdedit.exe with elevated rights but all i could find was a third party program and some references to runas, but didn't get them working (and wouldn't propably work with NSIS anyway). I'm curious why NSIS doesn't request elevated rights, as Vista never asks me to grant it those rights... i saw a post dating ~6 months back where a -apparently- NSIS developer was asking for M$ to fix some NSIS detection stuff. Dunno if that is related to current version anymore...

---

### Post by ago on 2007-05-22
Spegelius, I think this is now becoming a generic NSIS issue, you might want to get in touch with NSIS devs.

---

### Post by nreisan on 2007-05-24
i used the file from the first post and did the bcedit, however it loads the unbuntu installer
and it gets stuck on 33% preparing virtual disks, Formatting system.virtual.disk (this may take 1-15 minutes...)

hmmm

---

### Post by jimwmiller on 2007-05-24
Hi,

FYI, I just downloaded the [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.9.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.9.exe) file, and ran it.  It brought up several debugging type dialog boxes, and then finished successfully.  I then had the error 17 problem (that seems pretty common).  After getting the fix for grldr from the sticky tag [http://ubuntuforums.org/showthread.php?t=439965](http://ubuntuforums.org/showthread.php?t=439965), and replacing the file, all went well.  While my system does not have compression, the fix seemed to do the trick.  In fact, I'm writing this from my new wubi'ed Ubuntu Studio. :)  

System:
HP Pavilion 6120us (laptop) runing Vista (no XP)

Thanks to everyone for a fantastic job on this!  
-Jim

---

### Post by Computer Guru on 2007-05-27
I didn't read this thread through, but there is a workaround to force UAC on Vista for any app. I can forward you the (external, no modification needed to the original apps) code to whoever needs it if you drop me an email @ [email]ComputerGuru@NeoSmart.net[/email]

I'm using this code in EasyBCD, and it works a dream.

---

### Post by ASPCartman on 2007-05-27
Em i don't now what is wubi or another stuff that is on first post, but how i understand, you want to have on 1 pc Vista and Ubuntu? hmmm i have vista 32 bit and ubuntu 32 bit. Vista's partition primary, active. Ubuntu's ext3 logical. Grub starts first and he asks what to start, including vista. All is working perfectly. Or i misunderstood you?

---

### Post by ago on 2007-05-27
> **Computer Guru said:**
> I didn't read this thread through, but there is a workaround to force UAC on Vista for any app. I can forward you the (external, no modification needed to the original apps) code to whoever needs it if you drop me an email @ [email]ComputerGuru@NeoSmart.net[/email]

I'm using this code in EasyBCD, and it works a dream.

That would be extremely useful. Now ecology2007 and Spegelius are working on the Vista version, so feel free to send it to them.

Thanks in advance Computer Guru.

---

### Post by Computer Guru on 2007-05-27
Will do :)

---

### Post by Computer Guru on 2007-05-27
Just sent the code with the instructions, hope it helps.

---

### Post by 1337PSPer on 2007-05-27
Ok i tried 0.8 version with no luck i will give 0.9 a try tonight see how that goes i seem to be getting the common error on the Vista Boot loader. I also might try adding that line of code to boot.inf see if that works. also what are the chances of messing up my computer to a state that i would need to reformat my hardrive?
Thx, and if there are any other methods you would like me to try that there is a good guide for let me know I'll give it a go.

---

### Post by Spegelius on 2007-05-28
Computer Guru: i tried adding the .manifest to folder with the built executable. It didn't change anything. Also, i downloaded the thememe app and it showed that the Wubi NSIS executable allready has the manifest, with the <requestedExecutionLevel level="requireAdministrator" uiAccess="false" /> defined. So apparently no luck with that.

---

### Post by Computer Guru on 2007-05-28
OK, that means that the Wubi installer is already running with full admin privelages.

I'm into Windows Vista now to finally go through the code (it's finals week), so I'll be able to help you better once I'm familiar with how you're launching BCDedit.

If NSIS is launching BCDedit directly *using the Windows API* and as such bcdedit.exe is registered as a "child process" of NSIS, then it should work. I'll get back to you.

---

### Post by Computer Guru on 2007-05-28
Spegelius: I just went back and re-read the entire thread. You say that when running Wubi as a standard user you aren't prompted for a user/pass. I'm not sure what you mean.
 
Do you have UAC disabled? Did you maybe uncheck "Run all admins in admin approval mode"? Because if you did, MS made a mistake with that, it doesn't work as expected.
 
Because Wubi runs just fine here as both an admin and a standard user :)
When attempting to use it as a standard user, I'm prompted for the administrator credentials.
 
The code for bcdedit looks just great. the embedded manifest is perfect.

---

### Post by ecology2007 on 2007-05-28
To computer guru : Spegelius runs vista 64 bits, it might be a special case.

---

### Post by Computer Guru on 2007-05-28
That shouldn't matter. I use the same UAC code in EasyBCD, and it works fine on x86 and x64.

However, if you disable UAC for administrators, Vista actually disables UAC for EVERYONE, thanks to the bad grammer some of the programmers at MS have.

I suspect that is the problem, there is a workaround in the Local Security Policy if you really want to disable UAC for admin,s you just tell it to keep UAC on but hide the confirmation dialog.

---

### Post by Spegelius on 2007-05-29
> **Computer Guru said:**
> Spegelius: I just went back and re-read the entire thread. You say that when running Wubi as a standard user you aren't prompted for a user/pass. I'm not sure what you mean.


I meant the prompt which asks if program needs elevated right. But it seems that Wubi is running with elevated rights even without the prompt. I'm not very experienced with Vista's annoying UAC restrictions (actually i had that same mentality few years back with some Linux distro as everything reuired sudo or something... i guess i'm  expecting Windows to let me do everything... ;) ). 

> 
Do you have UAC disabled? Did you maybe uncheck "Run all admins in admin approval mode"? Because if you did, MS made a mistake with that, it doesn't work as expected.

I did have it disabled for annoyance minimizing reasons, but Wubi worked just the same. Now i have it on. I've never seen that Run all admins... button?

>  
Because Wubi runs just fine here as both an admin and a standard user :)
When attempting to use it as a standard user, I'm prompted for the administrator credentials.


Actually i just noticed that i'm the Admin of this PC (makes sence as i'm the only user of this machine.. ;) ). I haven't tried as normal user... 

> 
The code for bcdedit looks just great. the embedded manifest is perfect.

I think NSIS creates a manifest automatically. And the code regarding bcdedit does look ok, but just doesn't work on my machine. Executing the commands manually in command prompt one after another works with no probs, but not from Wubi... i've also tried ShellExecWait, Exec etc. Also tried an UAC plugin for NSIS, but same results. I do have two instances of Wubi running so it should be executing with elevated rights.

---

### Post by Computer Guru on 2007-05-30
Interesting.
Can you tell me if EasyBCD runs and displays the data on your machine?

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

It uses UAC and also executes bcdedit.exe - if it doesn't work that would indeed explain a lot.

If UAC is disabled, you won't be prompted for credentials, the manifest file doesn't have a meaning in that case.

What's interesting though is that with UAC disabled and as an Administrator bcdedit doesn't work. If you enable debugging, what's the output of bcdedit.exe from Wubi?

---

### Post by Spegelius on 2007-05-30
I DL'd EasyBCD and it does display entries of the boot manager and seems to be able to edit it without problems. Also VistaBootPro works ok (and i think it uses bcdedit also).

With added debugging, NSIS reports the output of bcdedit execution to be 'error'. Nothing else. In the code i have 4 different registers where output of executed programs should be, but they contain nothing or  stuff not related to bcdedit.

BTW, TweakVI Downloader produced Unhandled exception:

See the end of this message for details on invoking 
just-in-time (JIT) debugging instead of this dialog box.

************** Exception Text **************
System.ComponentModel.Win32Exception: The system cannot find the file specified
   at System.Diagnostics.Process.StartWithShellExecuteEx(ProcessStartInfo startInfo)
   at EPS.Libraries.ClientLibrary.HttpUtils.FileDownloaderForm.btnCancel_Click(Object sender, EventArgs e)
   at System.Windows.Forms.Control.OnClick(EventArgs e)
   at System.Windows.Forms.Button.WndProc(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.WndProc(Message& m)
   at System.Windows.Forms.NativeWindow.Callback(IntPtr hWnd, Int32 msg, IntPtr wparam, IntPtr lparam)


************** Loaded Assemblies **************
mscorlib
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/Microsoft.NET/Framework64/v2.0.50727/mscorlib.dll
----------------------------------------
FileDownloaderTester
    Assembly Version: 1.0.2550.16594
    Win32 Version: 1.0.2550.16594
    CodeBase: file:///C:/Program%20Files%20(x86)/NeoSmart%20Technologies/EasyBCD/bin/Get_TweakVI.exe
----------------------------------------
FileDownloader
    Assembly Version: 1.0.2550.16590
    Win32 Version: 1.0.2550.16590
    CodeBase: file:///C:/Program%20Files%20(x86)/NeoSmart%20Technologies/EasyBCD/bin/FileDownloader.DLL
----------------------------------------
System.Windows.Forms
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll
----------------------------------------
System
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System/2.0.0.0__b77a5c561934e089/System.dll
----------------------------------------
System.Drawing
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
----------------------------------------
System.Configuration
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
----------------------------------------
System.Xml
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll
----------------------------------------

************** JIT Debugging **************
To enable just-in-time (JIT) debugging, the .config file for this
application or computer (machine.config) must have the
jitDebugging value set in the system.windows.forms section.
The application must also be compiled with debugging
enabled.

For example:

<configuration>
    <system.windows.forms jitDebugging="true" />
</configuration>

When JIT debugging is enabled, any unhandled exception
will be sent to the JIT debugger registered on the computer
rather than be handled by this dialog box.

---

### Post by Spegelius on 2007-05-30
After fiddling around with EasyBCD, i lost all my bcd entries... ;). For kicks i tried the re-crete missing/deleted boot files in Diagnostic center and it first asked me for my Vista drive, gave it C: as that is my Vista drive. After that it asked for my boot drive and gave it E: as that is the active primary partition and houses XP. Got something about folder not being empty and no valid entries found. Nothing on the list... luckily i have some old backus made with VistaBootPro. I tried running Reset BCD storage in EasyBCD, but it crashed: Object reference not set to an instance of an object.

I wonder, could there be something on my setup that's causing some weird to happen? The Vista i'm running has been restored from disk image few times and bcd has been also restored multiple times. Bcdedit does work without problems.

---

### Post by Computer Guru on 2007-05-30
Thanks for the TweakVI Downloader bug - verified :/

In order for EasyBCD to recreate your BCD data, you'll need to delete the "Boot" folder from E: first.

I'm online if you want to IM, I'm sure we can fix it quickly: [email]NeoSmart@Gmail.com[/email] [msn protocol]

BTW, you can restore the VistaBootPRO image from EasyBCD -> Manage Bootloader

---

### Post by Computer Guru on 2007-05-30
So the output of bcdedit.exe during NSIS is `error`?

That's really suspicious, I've never seen that before. The errors I have EasyBCD coded to accept are in the form of ```
The boot configuration data store could not be opened.
xxxxxxxxxxxxxxxxxx
```

Where xxxxx is on a new line, and contains something like `Access Denied.` or `The system cannot find the file specified` or `The boot configuration data store could not be opened. The volume for a file has been externally altered so that the opened file is no longer valid.`

As a matter of fact, the word "error" doesn't occur in that output at all. You'd expect the `Access [is] Denied` message to appear if UAC was the problem.

Suggestion: replace calls to BCDedit with calls to ```
cmd.exe /k bcdedit /emum > c:\bcd.txt
``` which will simply dump all output of the bcdedit.exe command to c:\bcd.txt where you can view the entire log.

---

### Post by Spegelius on 2007-05-31
I'll get back to the Vista problem @ weekend, no time currently.

---

### Post by Computer Guru on 2007-05-31
OK, that's cool.
 
The TweakVI error isn't as bad as I thought - IdeaSoft (TweakVI Authors) server was down that day, everything is working now :)

---

### Post by myITrescue on 2007-05-31
Was able to set it up with the bcdedit commands that you gave me.  It worked fine after that.  My {ID} was a long long hexadecimal number so that didn't seem right, i tried to just put the number 1 and then it gave me a "bad command" error.  Then tried the really long id number and was able to complete all the commands.  Then on reboot it gave me the option of booting to Ubuntu and it finished the installation.   ( i did this at work and the next day someone took it off the computer already... LOL, but it worked. ) 

:p  thanks for the instructions guys.

---

### Post by nphoops on 2007-06-01
I just downloaded Wubi test3.exe on my Gateway Vista laptop, and I was surprised on how well things went.....the bootloader even worked! BUT, when Ubuntu Studio was starting up, I  got some kind of virtual disk error message, and then a graphics error message, and then all i get is the DOS looking screen w/ login and username. Any help? How can I get this to work?

---

### Post by Computer Guru on 2007-06-02
Do you have the error message that it gave you? Can you post it?

---

### Post by pezpen on 2007-06-02
hey im new to this... have just installed ubuntu using the wubi test 3 installer but it dosent work on vista... (knew that until i saw this forum and tryied it for my self :) )
when i reboot it find the ubuntu fine but when i select it is says that windows couldnt boot the files...
when i look in boot.ini i can see the ubuntu an all that and on c: is the files from the guide... what do i need to do to make it work ?

---

### Post by pwright2 on 2007-06-02
I've got a Gateway laptop with Vista Home Premium.  Before my old laptop died I had installed Kubuntu and was becoming kind of fond of it.  So I thought I would try with Wubi.  But I had been hesitating.

3 days ago I read some of the chatter in Linuxforum and decided to give it a try.  I have Wubi 7.04 test 3.  I read that I could save some time by downloading the Kubuntu alternate iso and putting it in the same folder with Wubi, so I did that.  I ran Wubi and it seemed to do fine.  It warned me that Vista support was experimental.  Installed and called for a reboot.  And up it came.  Except it was Ubuntu, not Kubuntu.  It seemed to work fine, though.  I thrashed around with it for a while and then went back to Vista.

Last night I tried to boot Ubuntu again.  Two instances show in the boot screen.  Neither would boot, just hung up with a few percent of the Ubuntu progress bar showing.

I used add/remove programs to remove Wubi.  I downloaded a Kubuntu iso from a different source.  I put it int the folder with Wubi.  This time I noticed the Settings button.  I told it to use Kubuntu this time.  The install has just finished.  It took several hours.  Obviously it was ignoring the ISO and downloading its own.

I'm about to reboot to see if it worked properly.  If I need to do this again, just how do I get it to use the local copy of the iso?

-----Paul-----

---

### Post by MikeM709 on 2007-06-03
Hello. 

I have Vista Ultimate with nothing else installed and I would like to know what I can do to help with making this work with Vista. So far after reading through the entire thread, the best idea I saw was to use a batch file to make the necessary changes. Oh well.

I have tried test2 and that was the one I had rpoblems with in getting back to Vista. So should I download test3 and try the instructions in the first post?

---

### Post by Spegelius on 2007-06-03
> **Computer Guru said:**
> So the output of bcdedit.exe during NSIS is `error`?

That's really suspicious, I've never seen that before. The errors I have EasyBCD coded to accept are in the form of ```
The boot configuration data store could not be opened.
xxxxxxxxxxxxxxxxxx
```

Where xxxxx is on a new line, and contains something like `Access Denied.` or `The system cannot find the file specified` or `The boot configuration data store could not be opened. The volume for a file has been externally altered so that the opened file is no longer valid.`

As a matter of fact, the word "error" doesn't occur in that output at all. You'd expect the `Access [is] Denied` message to appear if UAC was the problem.


Yeah, i actually thought that when originally encountering the problem with running bcdedit from NSIS, but dismissed it as 'error' just being a NSIS <-> external program interface thingy or something. True, if nsExec:ExecToStack should return the commands true output, it should something else than 'error'.

> 
Suggestion: replace calls to BCDedit with calls to ```
cmd.exe /k bcdedit /emum > c:\bcd.txt
``` which will simply dump all output of the bcdedit.exe command to c:\bcd.txt where you can view the entire log.

This didn't work... when executing command 
```

nsExec::ExecToStack '"cmd.exe" /k bcdedit /enum > c:\bcd.txt'

```
all i got was 'bcdedit is not recognized as external or internal program...' or something.

When i changed the string to:
```

nsExec::ExecToStack '"cmd.exe /k bcdedit /enum > c:\bcd.txt"'

```
the ooutput was the very familiar 'error'. I'm beginning to think that somehow the command execution fails or the syntax is wrong. BTW, none of the above causes c:\bcd.txt to be outputted.

Changing the code to:
```

ExecWait '"cmd.exe /k bcdedit /enum > c:\bcd.txt"'

```
causes to output to be 'ok'. But no output to c:\bcd.txt. And running the original bcd /create with ExecWait doesn't create anything to bcd, even if it outputs 'ok'.

Actually, Wubi does kinda work for me, as it creates the Ubuntu entry to boot.ini. Bcd sees this during boot and displays it as an option. It does not boot, giving some hex errorcode. But editing the boot.ini entry to 
```

c:\grldr.mbr="Ubuntu"

```
allows me to boot to Ubuntu, just as if i had the entry created with bcdedit. So where do we need bcdedit as we can accomplish it simply by editing or creating a boot.ini with the above entry? Lot neater, most of the Vista specific code could be removed(?) and no need to touch bcd itself. Granted, i'm not sure if bcd recognizes boot.ini if Vista is the only OS, but i'm waging it does. I'll see if i can get it tested during next week.

---

### Post by MikeM709 on 2007-06-03
I have looked many places and have found out that Vista does not recognize boot.ini. It is completely ignored unless there is something different than windows I think. I could be wrong but try googleing it.

---

### Post by clpo13 on 2007-06-03
> **pwright2 said:**
> I'm about to reboot to see if it worked properly.  If I need to do this again, just how do I get it to use the local copy of the iso?

Put the ISO in the same directory as your installation file, not the wubi folder. Then it should use the local copy.

---

### Post by Computer Guru on 2007-06-04
Spegelius, MikeM: Vista does not by default recognize boot.ini unless an older version of Windows is installed.
 
EasyBCD tricks Vista into recognizing and using boot.ini by creating a new BCD entry that chainloads ntldr placed in the same root folder as boot.ini, which then causes boot.ini to appear.
 
So if you want to ensure that it works, you'll have to package ntldr and ntdetect.com into the Wubi installer, copy them to C:\, add an NTLDR entry to the Vista bootloader, and modify boot.ini - a hell of a lot of work!
 
This is clearly a NSIS error now, the output is nothing like what should be outputted in that scenario.
 
What about creating a batch file and asking NSIS to run that? Is that any good?
 
Batch file contents:
```
%systemroot%\system32\bcdedit.exe /enum > \bcd.txt
```
 
And then running the .bat file from NSIS?
 
I mean, if even this doesn't work, then NSIS has some *major* problems! (unless this is just your machine??)
 
EasyBCD 1.61 will have Wubi support per ecology's request and should be available sometime next week. Would anyone here be willing to beta test the Wubi support?
 
(Even cooler, EasyBCD 1.61 can boot into a Linux installation without providing any details or even having GRUB installed to the bootsector. Just one button and EasyBCD will auto-locate Linux and run it :D)
 
Anyway, this is really weird!

---

### Post by ago on 2007-06-04
We can use the windows api directly and wrap the code as a dll plugin for nsis. We cannot ship ntldr for obvious reasons (but I do  not think it is required since the aim is to boot directly from bcd without using boot.ini).

---

### Post by ago on 2007-06-04
I have no Vista, my understanding was that there were permissions issues when editing BCD from nsis. Is that the case still? Computer Guru, Spegelius can you explain in lame terms what is the show stopper? Computer Guru, I assume you can edit BCD, can't we use the same technique to add an entry for grldr?

---

### Post by Computer Guru on 2007-06-04
Ago, the problem is that NSIS isn't properly executing the commands that Spegelius is passing to bcdedit.exe.
 
The permissions issue has been dealt with (on systems with UAC enabled, Wubi now correctly requests elevation and then uses this elevated status to run bcdedit), but for some odd reason NSIS refuses to carry out those commands.
 
So, yes, you can use the same exact technique I do to add GRLDR to the Vista bootloader. But it isn't working from NSIS.

---

### Post by ago on 2007-06-04
> **Computer Guru said:**
> Ago, the problem is that NSIS isn't properly executing the commands that Spegelius is passing to bcdedit.exe.

Can't we use C++ calls? As mentioned whenever we have limitations in NSIS what we have done in the past was using C++ WinAPI and wrapping up the code. Do you have a snipplet we can use?

---

### Post by Computer Guru on 2007-06-04
Yeah, that should work.
 
I'm afraid I stopped using C++ 5 years back when the .NET Framework first came out. Now it's just .NET and Java :)

Anyway, all you would need is to use the Windows API to run bcdedit.exe and pipe the standard output back to your code where you would parse it with the regex:
```
.*{([^}]+)}.*
``` for the ID, then re-run BCDedit with the commands on the first page of this thread.
 
If you like, I can write a helper program (not in C++) for you that you can run from Wubi setup, but that's of course assuming that NSIS can run it, but it should since you're not looking to redirect the output of this helper app, just to run it.
 
/me reboots now to test Wubi code.

---

### Post by ago on 2007-06-04
My only issue is that I do not have Vista and I do not like to write code blind, but we'll try to organize something.

---

### Post by Computer Guru on 2007-06-04
Yeah, I know what you mean.
 
Whatever you decide, I'm ready and willing to help in any way I can.

---

### Post by ago on 2007-06-04
For experimenting an exe is easier (a self contained executable that adds a wubi entry to bcd) , since the exe should obviously work independently of nsis/wubi, and chances are that an exe is all that is needed, we might convert that to an nsis dll, but that is probably unnecessary. C/C++ would be better since we do not want dependencies.

You are more than welcome to help us out whenever/however you want, if you apply to the lupin team I'll approve so that you'll be able to edit the devel branch directly.

---

### Post by Spegelius on 2007-06-04
Ok, the boot.ini did sound too easy to be true... (M$ making something easily usable... :P ).

I did try executing a batch file containing the bcdedit command, but as i recall, it didn't work. I did create a batch file that does the whole entry adding in one call; i use a fixed {id} field (all characters are '1'), it works when executed from cmd prompt with admin rights but haven't tested that from NSIS. I'll check it tonight.

I'm thinking about making a testinstall of Vista on a virtual machine, to see if these errors are on there, too.

---

### Post by ago on 2007-06-04
Spegelius do not test the bcd code inside wubi, make a stand-alone app first (dos/c/whatever) and make sure it works. Then just use wubi to call that app. Hardcode everything, there are no parameters to be passed and the only relevant output is success|failure.

---

### Post by Computer Guru on 2007-06-04
Here's the application. It'll create an entry with the name "Wubi Ubuntu" that points to `BOOT:\grldr.mbr`
 
If this works, I'll email or commit the source code (whatever license).
 
Spegelius, just run the exe from NSIS and/or out of it.
 
On error it will print 
 
```
Error: ERROR_DETAILS
```
On success:
```
Operation completed successfully.
```
 
It does not take any parameters. It runs on Windows Vista without any additional components or frameworks or anything.
 
(Just to clarify: this is a command-line application)

---

### Post by ago on 2007-06-04
Excellent I think we are getting there... Please test the above if you have vista!

---

### Post by ago on 2007-06-04
Code Guru, you can add the code within the zip itself (GPL2). If it works well, we'll add that into wubi/src/plugins. Call the file "editbcd.exe". 

NOTE: We will soon rename grldr.mbr to wubildr.mbr (that is to avoid potential conflicts with other apps)

---

### Post by Computer Guru on 2007-06-04
Here you go.

---

### Post by ago on 2007-06-04
Thanks a lot! Spegelius can you please test the above with/without nsis?

---

### Post by ago on 2007-06-04
Must grldr.mbr be under C:\ or can it be in a folder? We know grldr must be at root level but I assume that BCD does not necessarily have the same limitations of boot.ini & co.

---

### Post by Computer Guru on 2007-06-04
You can put it anywhere.
 
In EasyBCD I have NeoGrub.mbr in C:\NST\ along with menu.lst and a bunch of other "profiles"
Only GRLDR (in EasyBCD "NeoGrub") needs to be in C:\

---

### Post by ago on 2007-06-04
Then we might want to have 1 argument: the grldr.mbr full path.

---

### Post by Spegelius on 2007-06-04
Okay, executing WubiBCD.exe with ExecWait did add Ubuntu entry! Great work, Guru. ExecWait's output was simply 'ok'. With nsExec::ExecToStack, it was '0'.

---

### Post by Computer Guru on 2007-06-04
> 
Then we might want to have 1 argument: the grldr.mbr full path.
Sure, I can do that.
But if the name change is permanent, it's probably safer just to hard-code the new path in, no?

---

### Post by Computer Guru on 2007-06-04
Awesome news, Spegelius! Glad you got that to work!

---

### Post by ago on 2007-06-04
> **Computer Guru said:**
> Sure, I can do that.
But if the name change is permanent, it's probably safer just to hard-code the new path in, no?

The name and path is permanent but the installation drive is not, since we have to pass the drive we could just as well pass the full path. 
I also think it would be better to return the ID (0 for failure), thus we can use that in the uninstaller script.

---

### Post by Computer Guru on 2007-06-04
Why would you pass the drive?
 
When you say ```
bcdedit /set {ID} device boot
``` Vista automatically detects the boot drive and sets the "Wubi" BCD entry to point to there, where the Wubi GRLDR file should reside.
 
With regards to returning the ID, I think that is going to be a problem: NSIS isn't correctly reading anything that's "returned," only "OK" or "Error," at least as far as I can gather. This was a part of the original problem.
 
The best solution I can think of is to have WubiBCD add the info to the registry itself.....

---

### Post by ago on 2007-06-04
> **Computer Guru said:**
>  
When you say ```
bcdedit /set {ID} device boot
``` Vista automatically detects the boot drive and sets the "Wubi" BCD entry to point to there, where the Wubi GRLDR file should reside.

grld.mbr will go inside the /wubi/boot/winboot folder which is not necessarily in the boot drive (assuming that is feasible).  grldr will be under the boot drive, but grld.mbr will be somewhere else (possibly on a different partition). If that creates problems then we will keep also grld.mbr at root level of the boot drive.
 
> With regards to returning the ID, I think that is going to be a problem: NSIS isn't correctly reading anything that's "returned," only "OK" or "Error," at least as far as I can gather. This was a part of the original problem.
That's because the return value of an external call is an integer which is not to be confused with the standard output. I would not be surprised if bcedit returns an integer for success/failure but prints the ID to standard output. That does not mean that we cannot return the ID in our own script (we can certainly do so with a dll for instance [http://nsis.sourceforge.net/Calling_an_external_DLL_using_the_System.dll_plugin](http://nsis.sourceforge.net/Calling_an_external_DLL_using_the_System.dll_plugin)).
 
> The best solution I can think of is to have WubiBCD add the info to the registry itself.....
That can also work

---

### Post by Computer Guru on 2007-06-04
OK, no problem. I'll make it accept two parameters, the drive and the path (they're two separate calls in BCD)
 
So something like ```
WubiBCD /d=C: /p=\wubi\boot\winboot\grldr.mbr
```
 
There is no problem with having grldr.mbr out of the root, it's what I do with EasyBCD & NeoGrub.
 
I can have the main function return a complete string (because the ID is an alpha-numeric value) include the surrounding {}

---

### Post by Computer Guru on 2007-06-04
Well, I have all of it working.... except I can't return a string because it turns out that's not a valid return type under Windows - has to be integer or void. The BCD ID isn't a number, so I don't know what you would like for me to do. Should I have it add the info to the registry? If so, where to?

---

### Post by ago on 2007-06-04
> **Computer Guru said:**
> Well, I have all of it working.... except I can't return a string because it turns out that's not a valid return type under Windows - has to be integer or void. The BCD ID isn't a number, so I don't know what you would like for me to do. Should I have it add the info to the registry? If so, where to?

Can you copile it as a dll?

---

### Post by Computer Guru on 2007-06-04
Sure. Do you want the whole DLL to be static?

---

### Post by ecology2007 on 2007-06-04
If you want to store in registry, we store the drive id there 
WriteRegStr HKLM "Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi" "VistaBootDrive" "$vistaBootDriveCode".
You can overwite it or add you own entry if you want, but i don't know how hard it is to write to the registry from a dos exe, some antiviruses may block the process.

You can output it to the screen we can read stdin and stdout with ExecToStack.
Provided the output always follow the same scheme we can parse it.

Or you can put it in a txt file next to the exe, that's even better, 
for instance, wubibcd.ini
[WubiBCD]
driveid={........}
returncode=0/1
returnmessage="It worked !!!!"
[...]

Can you code its twin brother or add a parameter for uninstall purposes?

---

### Post by ago on 2007-06-04
I prefer to have a dll (no need for it to be static) and control storage from the main application. It's a cleaner design that way.

---

### Post by ecology2007 on 2007-06-04
> **Computer Guru said:**
> Sure. Do you want the whole DLL to be static?
What's good with an exe is that the user can uninstall the entry himself, but since he can allready do it with bcedit or EasyBCD.
A dll would be better to use on our side, but an exe is perfectly fine. I ll have Hampus contact you.

---

### Post by Computer Guru on 2007-06-04
OK, I'm confused now.
 
I have a DLL and an EXE. Which would you like to use?
 
With the EXE:
I can create a TXT file and store the stuff in it. Wub installer will have to parse the TXT file and do whatever it wants with the data.
OR
I can write the info to the registry myself. (perfectly safe, no fear of AV corruption)
 
With the DLL:
You get really tight integration with Wubi by making it into a plugin. You can install and remove Wubi by simply issuing a command in NSIS.
 
Either way, I will add both install and remove support.
 
I personally think DLL is the better way to go, especially since there is no fear of NSIS's buggy stdout support.

---

### Post by Computer Guru on 2007-06-04
> **ecology2007 said:**
> What's good with an exe is that the user can uninstall the entry himself, but since he can allready do it with bcedit or EasyBCD.
A dll would be better to use on our side, but an exe is perfectly fine. I ll have Hampus contact you.
Exactly.
 
Let wubi use a DLL, and if users want to change something, more user-friendly tools are available. I think people would rather use a GUI like EasyBCD than a command-line utility, esp. if they're Windows users ;)

---

### Post by ago on 2007-06-04
> **ecology2007 said:**
> You can output it to the screen we can read stdin and stdout with ExecToStack.

Did you guys try that to get the ID from a direct NSIS call to bcedit using ExecToStack?

---

### Post by Computer Guru on 2007-06-04
Here you go.
 
DLL Name: WubiBCD.dll
Namespace: WubiBCD
Class: WubiBCD
 
Function Prototypes:
```

[SIZE=2][COLOR=#0000ff]public [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]static [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][SIZE=2][COLOR=#000000] Install([/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][SIZE=2][COLOR=#000000] drive, [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][SIZE=2][COLOR=#000000] path);[/COLOR][/SIZE]
[SIZE=2][COLOR=#0000ff]public [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]static [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][SIZE=2][COLOR=#000000] Uninstall([/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][SIZE=2][COLOR=#000000] ID);[/COLOR][/SIZE]

```
 
[SIZE=2]WubiBCD.Install will return the ID as "{alphanumeric-string}" on success and "Error: ERROR_DETAILS" on failure. It expects input in form of "C:" and "\wubi\grldr.mbr"[/SIZE]
[SIZE=2]WubiBCD.Uninstall expects input in form of "{this-is-an-alphanumeric-bcd-id}"[/SIZE]

---

### Post by ecology2007 on 2007-06-04
> **ago said:**
> Did you guys try that to get the ID from a direct NSIS call to bcedit using ExecToStack?

Yes i did and it is the current way it is coded but i work blind, and did not have any feedback since two weeks.
There as been a couple of tweaks since test 1 or after, i don't know if they have been effective.
RequestExecutionLevel for Vista, RegistryMode 32 bits for Windows 64, full path of grldr.mbr given as parameter to bcdedit, reading of 4 lines of bcedit output...


Maybe it is allready working for 90 % of people and we don't know it.
(I seriously doubt it :D)

---

### Post by ago on 2007-06-04
> **Computer Guru said:**
> Here you go.

Excellent. Ecology it's all yours now. We'll have a preliminary build soon. Thanks a lot Computer Guru!

---

### Post by ecology2007 on 2007-06-04
> **Computer Guru said:**
> Here you go.
 
DLL Name: WubiBCD.dll
Namespace: WubiBCD
Class: WubiBCD
 
Function Prototypes:
```

[SIZE=2][COLOR=#0000ff]public [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]static [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][SIZE=2][COLOR=#000000] Install([/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][SIZE=2][COLOR=#000000] drive, [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][SIZE=2][COLOR=#000000] path);[/COLOR][/SIZE]
[SIZE=2][COLOR=#0000ff]public [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]static [/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][SIZE=2][COLOR=#000000] Uninstall([/COLOR][/SIZE][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][SIZE=2][COLOR=#000000] ID);[/COLOR][/SIZE]

```[SIZE=2]WubiBCD.Install will return the ID as "{alphanumeric-string}" on success and "Error: ERROR_DETAILS" on failure. It expects input in form of "C:" and "\wubi\grldr.mbr"[/SIZE]
[SIZE=2]WubiBCD.Uninstall expects input in form of "{this-is-an-alphanumeric-bcd-id}"[/SIZE]

:popcorn:

Now for the implementation details :
How do we know the value of "string drive" : is it Vista drive or wubi drive ?
Where do i copy grldr : to vista drive root or wubi drive root ? or wubibcd do it on his own ?
Is it still possible to make the exe version ( we could **** it in wubi/tools).
Would you be nice enough to ship the latest sources, the dll and the cs project in a zip ?

[SIZE=2][/SIZE]

---

### Post by Computer Guru on 2007-06-04
Come to think of it, I'm not so sure the dll will work.... I don't if NSIS can support .net DLLs or not.
 
The source and the dll are both in my last post in the zip file.
 
GRLDR (or whatever you rename it to) is placed on whatever drive you like, GRLDR.mbr (or whatever you end up calling it) will auto-locate it via the name embedded in it by means of `grubinst.exe`
 
I'll post the EXE version (and update it with uninstall support) soon as it's ready along with the source.
 
Do you want just the .cs file or the entire project? (.csproj, .sln, etc.)

---

### Post by ecology2007 on 2007-06-04
I want it all ! ;).

Your last zip is missing the source, it has the project configuration file, the first exe version has a .cs file but it has probably been updated since then...
.net exe will have no problem under Vista, i m pretty sure they allways have the framework, for NSIS it is another story.
Take your time.

---

### Post by Computer Guru on 2007-06-04
Oops.. I thought I had attached the source - must have zipped the wrong file.
 
Just googled it, doesn't look like NSIS has proper .NET support for DLLs, but EXEs should be fine (and Spegelius verified that it does indeed work with NSIS, so that's cool :))

---

### Post by Computer Guru on 2007-06-04
OK, hopefully this is it.
 
```
>wubibcd.exe
 
Call to WubiBCD is missing parameters. Expected input:
WubiBCD.exe [/d <drive> /p <path> | /uninstall <{id}>]
 

```
 
Basically,
wubi.exe /d C: /p \wubi\mygrldr.mbr
or
wubi.exe /uninstall {this-is-the-id}
 
If you run uninstall it will check if this is a valid, existing ID or not.
 
Anything else?
 
I've attached a Zip with the WubiBCD.exe and WubiBCD.cs - hope that covers it.

---

### Post by Computer Guru on 2007-06-04
btw, the code doesn't save the ID to the registry or a file yet - only stdout.

When you decide what method you'd rather I use, please let me know. I can do either as I said before.

Current output:
"Operation completed successfully. New ID is *{ID}*"

---

### Post by ecology2007 on 2007-06-04
Spegelius and i are working on it on IM, if you are around drop me a PM and i will tell you where we can meet.

---

### Post by Computer Guru on 2007-06-04
Added you to MSN.

---

### Post by Computer Guru on 2007-06-05
Really sorry about last night, Jabber was giving me hell.
Everything is fine now - see you online soon :)

---

### Post by Computer Guru on 2007-06-05
Here's an updated build of WubiBCD.exe that creates a .ini file with the needed data.
 
```
# wubibcd
The syntax of the command is incorrect.
Installs or removes Wubi from the Vista bootloader.
 
WubiBCD [[/d drive /p path | /uninstall]]
 
        /d              Identifies the drive to load the bootsector image from.
        /p              The path to the file relative to the root.
        /uninstall      Removes Wubi from the Vista BCD.
 

```
 
WubiBCD.ini on Success:
```
[wubibcd]
success=true
id={this-is-the-id}
```
 
WubiBCD.ini on Failure:
```
[wubibcd]
success=false
error=error_details
```

---

### Post by ecology2007 on 2007-06-05
Thanks i ll grab it !:o

---

### Post by MikeM709 on 2007-06-05
Hey should I give this a try? I'm still on ubuntu right now so if you say i can just delete the grldr file like i did last time and be back to vista.

---

### Post by Computer Guru on 2007-06-06
If you could that would be wonderful.
 
What's your Jabber ID btw?

---

### Post by ago on 2007-06-06
You can try the latest minefield, it includes latest vista code (untested so far)

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by Computer Guru on 2007-06-06
This is in bzr, right?

---

### Post by ago on 2007-06-06
Yes, but you will have to compile wubi (and lupin)

---

### Post by Computer Guru on 2007-06-06
Does lupin compile under Windows?
 
I haven't actually run Wubi, I just go follow the codeflow and run the applications by themselves...
 
BTW, I added you to Jabber, "awaiting authorization"

---

### Post by ago on 2007-06-06
> **Computer Guru said:**
> Does lupin compile under Windows?
 
I haven't actually run Wubi, I just go follow the codeflow and run the applications by themselves...
 
BTW, I added you to Jabber, "awaiting authorization"

You'll need to "compile" under linux. You can use cygwin/emulator/wubi
Computer Guru I can only authorize you tonight, I have no access during daytime.

---

### Post by Spegelius on 2007-06-07
My internet connection didn't work yesterday so i couldn't dl newest minefield or latest sources. Anyhoo, as i had rev 166 of Wubi on my comp, i played with it. Two problems: function editBCD was never executed and wubibcd causes error dialog during uninstall. First problem omitted adding the bcd item. The problem was caused the conditional structure that called editBCD only if $isNT was '0'. At least on my PC, $isNT is '1'. The second problem seemed to be because wubi folder was allready deleted when wubibcd was called from $INSTDIR\tools.

Dunno if t hese are still relevant, thought i'd report them anyways.

---

### Post by Computer Guru on 2007-06-07
Are you running Wubi in compatability mode?

There is really no other way that Windows Vista would be reported as not NT.

---

### Post by ago on 2007-06-07
If anything that is due to interaction between nsis and vista. There is no code that I am aware of that would trigger compatibility mode. Ecology might want to comment on that. Anyway if the only issue is vista detection we could use a different algorithm to detect vista.

---

### Post by ago on 2007-06-07
Spegelius, download the new minefield, try to set vista manually if necessary.

---

### Post by Spegelius on 2007-06-07
Computer Guru: i believe it is detected as NT, as the value was '1'. It's the Wubi code that doesn't execute Vista BCD edit when isNT is '1'.

I'll try the minefield sometime tonight, i believe installing Wubi on my work machine would be... bad karma... :) (don't want IM breathing on my neck).

---

### Post by Computer Guru on 2007-06-07
Oh, ok... 

Wow.. NSIS has some severe issues!

---

### Post by MikeM709 on 2007-06-07
Thats Microsoft for ya!

---

### Post by Spegelius on 2007-06-07
> **Computer Guru said:**
> Oh, ok... 

Wow.. NSIS has some severe issues!

Actually the OS detection is in the code and it works ok. Wubi code just handled NT and Vista exclusively, i.e. if NT, not Vista. Vista registry does have Windows NT key, wich is being searched.

I tested the latest minefield, found the bugs mentioned above and committed to bzr (talked about them with ecology in IM). There was also ideas about improving the boot drive detection, ecology took them in consideration.

BTW, Wubibcd did something odd; i ran it when testing changes the first time and it created item in BCD, but i was missing the partition. Also the item didn't show during boot. Second time i tested, it did it fine.

---

### Post by ago on 2007-06-07
I built a minefield (179-52) including latest spegelius bugfixes, test it out!

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by ago on 2007-06-09
We now have a new minefield still please keep testing. Same link above.

---

### Post by Computer Guru on 2007-06-11
Works great here!

Awesome work with this build, Ago.

---

### Post by Computer Guru on 2007-06-11
ecology, spegelius: are there any remaining changes to WubiBCD that you'd like made?

---

### Post by CrazyGuy123 on 2007-06-11
One thing on Wubibcd (or at least related), the path given to it should start with a "/", else it doesn't work.
so "/wubi/boot/winboot/wubildr.mbr" rather than "wubi/boot/winboot/wubildr.mbr"


Also, do you realise the BCD can be edited from the registry, either with the command line, a registry editor script, or the windows API, and that way you can just add the one key needed to add an entry to the boot menu without requiring a custom built app to do it.  Have a look in HKEY_LOCAL_MACHINE\BCD00000000\Object.

I thought the above would be helpful, although it's duplicated from my other post earlier today in a new thread.

---

### Post by ecology2007 on 2007-06-11
> **Computer Guru said:**
> ecology, spegelius: are there any remaining changes to WubiBCD that you'd like made?

For now we have everything we need, but the report from this crazy guy is interresting.
Can you confirm it ?
Note we have not switched yet to the Bcdedit version that writes its value to an ini.
If someone did, it happened under my radar.;)

---

### Post by Computer Guru on 2007-06-11
> **CrazyGuy123 said:**
> One thing on Wubibcd (or at least related), the path given to it should start with a "/", else it doesn't work.
so "/wubi/boot/winboot/wubildr.mbr" rather than "wubi/boot/winboot/wubildr.mbr"


Yeah, that's the way it should be - but I can of course hard code it to prepend the "/" if necessary, though seeing as wubibcd will only be used from the installer I don't think it's necessary.

> Also, do you realise the BCD can be edited from the registry, either with the command line, a registry editor script, or the windows API, and that way you can just add the one key needed to add an entry to the boot menu without requiring a custom built app to do it.  Have a look in HKEY_LOCAL_MACHINE\BCD00000000\Object.

Yes, it can be edited from the registry, but it's about the number 1 worst thing you can do on a Vista install.

Referring to the MSDN documentation and emailing the Windows Vista developers about this, they begged be not to do it this way, which was my first choice for ease of use, etc. - especially if you have two windosw vista installations, it won't be synchronized right. Plus, this data has to be propogated to the bcd store which isn't accessible before vista loads, so it's very susceptible to corruption if you make the changes from the registry.

I wasn't aware that there was a win32 api for accessing the BCD registry, though I do know it is possible via WMI, though it only runs from Vista or LHS and there is no documentation on *adding* data to the BCD via WMI, though I know it can be done.

IMO the most reliable and fail-proof way is to use bcdedit.exe, even if it requires a helper app the end users won't see.

---

### Post by CrazyGuy123 on 2007-06-11
> **Computer Guru said:**
> Yes, it can be edited from the registry, but it's about the number 1 worst thing you can do on a Vista install.

kk - I hadn't looked at any documentation, just used regedit to fix it when it wouldn't boot, and that fixed it so it seemd ok, and while I was there I looked around and it seemed like it was an easier route to add a new entry.  If I guess there was a reason for MS putting access control on them so even admins couldn't edit existing keys - I figured it was just so viri don't see it as an opertunity to load before windows.

The windows API I meant was just the RegOpenKeyA and the others like it which seemed to work.

If registry access isn't the way to do it, looking at how bcdedit works, it seems to use these API's:
NtAddBootEntry
NtEnumerateBootEntries
NtDeleteBootEntry
NtSetSystemEnvironmentValueEx
NtQuerySystemEnvironmentValueEx
NtModifyBootEntry
NtSetBootEntryOrder
NtSetBootOptions
NtTranslateFilePath
NtQueryBootEntryOrder
NtQueryBootOptions

Although I don't think it's worth changing to some (probably) undocumented API over just running a command line tool and parsing output.

EDIT:  Those API's seem to exist in XP as well, so they might not be the primary method bcdedit uses, or it could be MS nearly implemented the BCD store in XP, but then didn't use it at the last minute, and thats why it only arrived in vista.  As I'e no idea what parameters they take, it's not easy to test the api, short of debugging the bcdedit tool while it's using them.

---

### Post by Computer Guru on 2007-06-11
interesting.... Didn't see those functions before.

AFAICS, though the same function names exist in XP and Vista, they do different things. In XP they modify boot.ini and in Vista they modify bootmgr registry, at least that's what my light digging shows.

---

### Post by ago on 2007-06-15
Can you please try the latest minefield? Vista should hopefully work out of the box now.

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by whiteguysamurai on 2007-06-15
> hmm nobody with vista? Is it that bad?

Not at all, i enjoy it a great deal.

I'm considering trying this out, i'll let you know how it works later.

---

### Post by SirDaShadow on 2007-06-17
Well I tried the latest minefiled on 6/16/2007 on my brand new compaq presario v6000...well it did work, installed ubuntu, rebooted...got the ubuntu logo for 2 minutes then a blank screen for 3 minutes.

I looked at the HD activity light and it was off. I assumed it locked up. So I held down the button to turn off the laptop and turn it on.

Big Mistake.

I selected to boot Wubi, it said "could not find wubi.mbr". I was like huh? then selected to boot Vista. I saw a blue screen of death flash by and it did not boot. I selected the brand new "Repair Computer" option and ran a comannd prompt.

When I did a Dir C:\ it said "File Not found". The files were gone!!!

I then did a chkdsk C: /f...that restored the files

Then I did a chkdsk C: /R to check for bad sectors...it locked up at sector 10000

Rebooted into vista, ran the GUI chkdsk with the option to check for bad sectors. This time it went all the way through with no errors...I then promptly removed Wubi from my system...

---

### Post by leibowitz on 2007-06-17
holy cow

I remember someone telling a story about ntfs corruption after a while. He just booted Ubuntu once again, and then boom! no more files.

I wonder how this comes..

Anyway I'm happy you did recover your files.

---

### Post by Mizarus on 2007-06-18
i installed the tes3 3 version and i lost my vista boot, theres anyway i can get it back from inside unbutu? ive tryed to edit menu.lst and it did created a new entry on the boot list but all it does is to load unbutu,
i guess il uninstall it and give try to the new minefeild version.

---

### Post by tinybit on 2007-06-19
try this way to boot vista:

install grub4dos or call grub4dos from GNU GRUB by using "kernel (...)/grub.exe" followed by a "boot"

at the grub4dos console, type the following three commands:

find --set-root /bootmgr
chainloader /bootmgr
boot

This should boot to Windows boot manager and vista will get a chance to boot.

---

### Post by Computer Guru on 2007-06-19
Why are people losing their Vista boots by installing Wubi?

It didn't happen with me... but I don't understand why it would happen at all. Doesn't Wubi just add an entry to the Vista BCD store that, in turn, loads GRLDR? I was under the impression the MBR isn't touched by Wubi/GRLDR.....

---

### Post by ago on 2007-06-19
> **Computer Guru said:**
> Why are people losing their Vista boots by installing Wubi?

It didn't happen with me... but I don't understand why it would happen at all. Doesn't Wubi just add an entry to the Vista BCD store that, in turn, loads GRLDR? I was under the impression the MBR isn't touched by Wubi/GRLDR.....

Correct. I assume it's because of hard reboot, but it sounds quite strange.

---

### Post by CrazyGuy123 on 2007-06-19
I see why a hard reboot should cause that - linux shouldn't have been writing in that area anyway.  Could it be that they havn't lost the menu, but the timeouts been set to 0?  If say the preseed file went wrong or missing, could the installer have loaded grub to the mbr?  (since it normally installs grub by default)

Mizarus:  Could you try tapping F8 while starting the system up and see if that gets you to the vista bootloader?

---

### Post by ago on 2007-06-19
> **CrazyGuy123 said:**
> If say the preseed file went wrong or missing, could the installer have loaded grub to the mbr?  (since it normally installs grub by default)
Grub and partman are disabled in d-i, so I doubt that is the case even if preseed if missing or corrupted. In fact if preseed is missing the installation will stop immediately.

---

### Post by Mizarus on 2007-06-19
> **CrazyGuy123 said:**
> I see why a hard reboot should cause that - linux shouldn't have been writing in that area anyway.  Could it be that they havn't lost the menu, but the timeouts been set to 0?  If say the preseed file went wrong or missing, could the installer have loaded grub to the mbr?  (since it normally installs grub by default)

Mizarus:  Could you try tapping F8 while starting the system up and see if that gets you to the vista bootloader?
 i did tryed that before installing the new version, it got me to the boot screen but there was no vista entry there, i never had a chance to try guru advice tho, it would probly have worked

---

### Post by CrazyGuy123 on 2007-06-20
If you lost the vista bootloader, how did you uninstall and reinstall the new version?  Did you restore the bootloader using a windows CD? Or are we misunderstanding the problem and it's actually you can't see the vista bootloader to select ubuntu, and it always boots windows?

---

### Post by Armisael on 2007-06-20
i want put wubi, i read about that dont run in Vista :(, but i reaD another post that these program "EasyBCD" we choose the boot, we can add without change anything, work good? if it is ill try or ill w8 for a vista compatible

cause change files is too many trouble and not for all works

---

### Post by Mizarus on 2007-06-20
> **Armisael said:**
> i want put wubi, i read about that dont run in Vista :(, but i reaD another post that these program "EasyBCD" we choose the boot, we can add without change anything, work good? if it is ill try or ill w8 for a vista compatible

cause change files is too many trouble and not for all works
download the lastest minefield version it already suports vista

---

### Post by Mizarus on 2007-06-20
> **CrazyGuy123 said:**
> If you lost the vista bootloader, how did you uninstall and reinstall the new version?  Did you restore the bootloader using a windows CD? Or are we misunderstanding the problem and it's actually you can't see the vista bootloader to select ubuntu, and it always boots windows?
i mannualy unistalled wubi and i could boot to windows again, there was no need to restore the bootloader the first time i did that, on the second one tho the boot got damaged somehow(i think i deleted more files then i should have) and a system restore was needed.

---

### Post by Vadi on 2007-08-30
Is Wubi vista-stable now?

---

### Post by ago on 2007-09-13
> **Spegelius said:**
> Not good so far. I found one way to elevate from cmdline and it's an external program (needs Visual studio to compile?): [http://www.wintellect.com/cs/blogs/jrobbins/archive/2007/03/27/elevate-a-process-at-the-command-line-in-vista.aspx](http://www.wintellect.com/cs/blogs/jrobbins/archive/2007/03/27/elevate-a-process-at-the-command-line-in-vista.aspx)

I'm stuck untill i can get the nsExec to execute commands as admin. Running Wubi as Admin doesn't help.

Edit: 'RequestExecutionLevel admin' is allready defined on the latest bzr source. Doesn't do a thing...

Maybe: [http://nsis.sourceforge.net/UAC_plug-in](http://nsis.sourceforge.net/UAC_plug-in)

from the docs:

UAC::Exec '' '"$INSTDIR\${APPFILE}"' '' ''

That might be used to launch bcdedit...

---

### Post by anonymous j on 2007-09-16
Still not ready, booted it on vista and all I would get is a black screen after the ubuntu splash screen, I followed the instructions on the first page, and I even downloaded something called Wubi vista installer, still nothing. Please help

---

### Post by rruhge on 2007-09-16
Installed with wubi using Vista Ultimate, now using Ubuntu, absolutely no problems here.  Didn't have to go through any special steps either.

---

### Post by ago on 2007-09-17
> **anonymous j said:**
> Still not ready, booted it on vista and all I would get is a black screen after the ubuntu splash screen, I followed the instructions on the first page, and I even downloaded something called Wubi vista installer, still nothing. Please help

If you are booting into Ubuntu, it means that the vista-specific part is working. You may have a different issue. Open a new post and try to provide as much info as possible.

---

### Post by Thunderalex on 2007-09-17
Well i'm new on this of ubuntu, i'm find a video, about how to install ubuntu whit wubi on Vista, and there's go one tip, that it might be useful i think.
Here's the link: [http://www.youtube.com/watch?v=tjJl3p0-YMs]("http://www.youtube.com/watch?v=tjJl3p0-YMs")

I hope it will be usefull.

---

### Post by Thunderalex on 2007-09-18
It work's, yesterday i tried using the tip of the video, and it worked, in fact i'm posting on ubuntu. :)

---

### Post by sean_gilmore on 2007-11-20
Is there a set date for when the next Wubi is to be released? (hopefully with GG)

because I can't risk ******* up my computer by tooling around with it (again)

---

### Post by ago on 2007-11-20
There is a conflict with the kernel which makes it difficult for wubi to work with some hardware configurations, that is not easy to fix.

You can try wubi 7.10 it may or may not work in your case, but not much to loose.

[http://www.wubi-installer.org/devel/minefield/](http://www.wubi-installer.org/devel/minefield/)

---

### Post by sean_gilmore on 2007-12-11
where do you input the bcdedit stuff

like you give lines but what do i do with it??

---

### Post by ago on 2007-12-12
you can use easybcd for that: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by utester on 2007-12-19
I want to install Ubuntu on a Lenovo Thinkpad X61s with no CD drive, and so I'm interested in WUBI.  Tried WUBI previously on a XP machine and it worked great.  My Thinkpad is running Vista Business, however, and an attempt run WUBI yesterday was unsuccessful: the machine still boots into Vista automatically without any boot prompt.  I'm planning to follow the directions in this thread to try to get it working.  Do you recommend just walking through the steps in the first post and seeing what happens?  Or is there an updated/consolidated procedure posted somewhere else?  Just thought I should double check before giving it a go.

Also (and I may be getting ahead of myself here) does anyone have experience following the steps in this thread and then running LVPM on Vista to convert to a standard install?

---

### Post by ago on 2007-12-19
> **utester said:**
> I want to install Ubuntu on a Lenovo Thinkpad X61s with no CD drive, and so I'm interested in WUBI.  Tried WUBI previously on a XP machine and it worked great.  My Thinkpad is running Vista Business, however, and an attempt run WUBI yesterday was unsuccessful: the machine still boots into Vista automatically without any boot prompt.  I'm planning to follow the directions in this thread to try to get it working.  Do you recommend just walking through the steps in the first post and seeing what happens?  Or is there an updated/consolidated procedure posted somewhere else?  Just thought I should double check before giving it a go.

Also (and I may be getting ahead of myself here) does anyone have experience following the steps in this thread and then running LVPM on Vista to convert to a standard install?

This is an old thread, all the changes should be incorporated.
You can use easybcd to check the boot options.

---

### Post by kwiggit on 2007-12-19
yes, I have vista ultimate. it sux. I have been trying to get a working version of wubi going with the version I want, but that is not happening

[IMG]http://i19.photobucket.com/albums/b184/akak8ty/BadVista.png[/IMG]

---

### Post by utester on 2007-12-19
> **ago said:**
> This is an old thread, all the changes should be incorporated.
You can use easybcd to check the boot options.

My issue turned out to be that after running the WUBI installer, the bootloader timeout was still set to 0.  (FWIW I'm working with the latest beta download from wubi-installer.org as of today).  So upon rebooting, it appeared nothing had changed (the boot screen disappeared in a flash and I was in Vista again).  I used EasyBCD to set the timeout to 30, was then able to boot into Ubuntu, and the install finished without problems.

Alas, I'm still writing this from Vista since I've got an Intel 4965AGN wireless card and haven't gotten it to work in Ubuntu yet.

---

### Post by ago on 2007-12-19
> **utester said:**
> My issue turned out to be that after running the WUBI installer, the bootloader timeout was still set to 0.  (FWIW I'm working with the latest beta download from wubi-installer.org as of today).  So upon rebooting, it appeared nothing had changed (the boot screen disappeared in a flash and I was in Vista again).  I used EasyBCD to set the timeout to 30, was then able to boot into Ubuntu, and the install finished without problems.

That's a good point, we change the timeout for XP, but not for vista. I signed that down.

---

### Post by panaretos22 on 2007-12-27
hello currently i have worked with a 64 bit amd turition acer laptop with nvidia graphic crd...i wanted to install wubi ..... installation ok but something when wrong wit xenviromenet .....w

---

### Post by ago on 2007-12-27
alt+f2
sudo dpkg-reconfigure xserver-xorg

---

### Post by Kona Andrews on 2008-01-26
I found that (despite being an administrative user) I didn't have sufficient privilege to run bcdedit (this seems to be an issue that other  folk have had with vista).

However, there was a simpler solution to make wubi bootable (at least in my edition of Vista, which is Vista Business):

1. Open Control Panel

2. Choose "System and Maintenance"

3. Choose "System"

4. Choose "Advanced system settings"

5. Choose the "Advanced" tab

6. Choose "Settings" for the "Startup and Recovery" section

7. Look in the dropdown list "Default operating system" and check that there is some kind of entry for Wubi  (there was in my case - if not, then I guess the Wubi install didn't work)

8. *Enable* the "Time to display list of operating systems" and "Time to display recovery options when needed" checkboxes (they were both disabled by default, which is why I presume I never got to see a boot menu containing a choice of windows and wubi).  I set both options to be enabled with a time of 30 seconds.  

9.  Reboot - you should now get a choice of windows or wubi when you boot up.

(Sorry, this info may be in a previous page of this thread but I missed it if so).

---
[www.thingwright.com](www.thingwright.com)

---

### Post by Kona Andrews on 2008-01-28
The version of wubi I used was 7.04.04.

---

### Post by ACardboardRobot on 2008-02-12
I tried the sudo dpkg... but my monitor still isn't being detected. I get the error message:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20080212150622


I'm wondering if I should delete the file mentioned but don't want to mess up my computer. Any help?

---

### Post by ago on 2008-02-12
You may want to try wubi 8.04

---

### Post by ACardboardRobot on 2008-02-12
lokked in the thread and clicked the link but theres a problem:

1. Server: wubi-installer.org
2. URL path: /devel/minefield/Wubi-8.04-alpha-rev398.exe
3. Error notes: File does not exist: /home/groups/w/wu/wubi/htdocs/devel/minefield/Wubi-8.04-alpha-rev398.exe
4. Error type: 404
5. Request method: GET
6. Request query string:
7. Time: 2008-02-12 09:14:41 PST (1202836481)

---

### Post by ago on 2008-02-12
[http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)

Use rev410, 411+ do not work yet (require a new ISO) and if you a have trouble [http://ubuntuforums.org/showthread.php?t=685926](http://ubuntuforums.org/showthread.php?t=685926)

---

### Post by ACardboardRobot on 2008-02-12
thanks downloading now

---

### Post by ACardboardRobot on 2008-02-12
yup. that worked but i had to boot in safe mode and now it only maxes out at 800 X 600 but i suspect that that's a general problem. thanks

---

### Post by elmagique on 2008-08-19
I did it in a much easier way, I installed easybcd, pressed add/remove entries, pressed linux (in add an Entry) (chose ubuntu as name) and then copied the menu.1st from the e:\ubuntu\disk\boot\grub folder to the c:\NST folder (automatically added when adding the entry) replacing the existing menu

and then it booted into it

after install replace the c:\NST\menu.1st with E:\ubuntu\disks\boot\grub\menu.1st

so I did it from a seperate partition without difficult command line stuff

---

