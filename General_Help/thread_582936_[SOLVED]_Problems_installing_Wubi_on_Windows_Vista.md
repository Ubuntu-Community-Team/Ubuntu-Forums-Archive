---
title: "[SOLVED] Problems installing Wubi on Windows Vista x64"
date: 2007-10-20
forum: General Help
---

### Post by arevilla on 2007-10-20
when will wubi (ubuntu 7.10 ) stay for windows vista?

---

### Post by ago on 2007-10-20
Vista is already supported but 7.10 is still work in progress. Stay tuned.

---

### Post by PGHammer on 2007-10-25
I got alpha-368 to install 7.10 on Vista Ultimate (in fact, I'm entering this reply from that install).  However, just to be on the safe side, here are the suggested installation steps:

1.  Download the 7.10 desktop ISO *separately* (I downloaded via torrent).

2.  If you have Wubi 7.04 installed, *uninstall it*.

3.  Run chkdsk /r (especially if you had a previous Wubi install) to clean up any *dirt* that may be in your NTFS filesystem.  (7.10's install system is pickier than that of 7.04; it refused to work until I did this; however, 7.04 would install fine.)

4.  Run the alpha-368 version of the installer.  (This installer worked flawlessly installing 7.10 on Vista Ultimate for me.)

Special note for owners of ATI X1K series graphics cards (this is especially true of the X1650/X1900 series): the restricted drivers that 7.10 will offer to install are the same drivers that were optional with 7.04 (Feisty Fawn).  They worked flawlessly wityh 7.04; they are just as flawless with 7.10.  For the first time, 7.10 actually offers to install the drivers for you (7.04 does not, though it had them as an option; if you wanted them, you had to install them either via apt-get or manually compile them yourself).  Advantage: 7.10.

---

### Post by penguin22 on 2007-10-25
Wow, I was so close with build 368, but now it says that bcdedit.exe not found although it is using the wubibcd from the temp directory.  I have copied bcdedit to the root of the C drive as well as that temp dir with the same results.  Once you click ok the install finishes and prompts to reboot, but I checked bcdedit and there is no entry for wubi :(

Any thoughts?

Here is the log:

UncompressFilesPriorInstall
C:\Users\PENGUI~1\AppData\Local\Temp\nsoF6AF.tmp\wubibcd.exe 
 1:1 
 2:Error: bcdedit.exe not found!
 
 3:HDD 
 4:3
Error while trying to execute: C:\Users\PENGUI~1\AppData\Local\Temp\nsoF6AF.tmp\wubibcd.exe : Error: bcdedit.exe not found!

vistaBootDriveCode = {} <=> 
vistaBootDriveCode {}
UncompressFilesAfterInstall
EjectCD

---

### Post by ago on 2007-10-25
where is your bcdedit.exe?

---

### Post by penguin22 on 2007-10-25
It is located in C:\Windows\System32 by default.

---

### Post by ago on 2007-10-25
> **penguin22 said:**
> It is located in C:\Windows\System32 by default.

Hmm strange because rev368 code checks for that:

[http://codebrowse.launchpad.net/~ubuntu-installer/wubi/gutsy/annotate/ago%40nb-ago-20071025023649-jfy8x1y9y8l0xjjf?file_id=wubibcd.cs-20071025011419-ch0wj8h6sla9af3w-4](http://codebrowse.launchpad.net/~ubuntu-installer/wubi/gutsy/annotate/ago%40nb-ago-20071025023649-jfy8x1y9y8l0xjjf?file_id=wubibcd.cs-20071025011419-ch0wj8h6sla9af3w-4)

line 27

---

### Post by penguin22 on 2007-10-25
The exact error message that pops up on the screen is:

Error while trying to execute:
C:\Users\PENGUI~1\AppData\Local\Temp\nsj72BA.tmp\wubibcd.exe : Error: bcdedit.exe not found!

I have copied the file at the beginning of the install to the active temp folder used as well.  Is there any way that a test build can assume and try to use the hardcoded path of C:\Windows\System32 as it is there?

I am not sure what you compile in, but am under the assumption that the environment variables are determined differently than how Windows uses set commands.  What does the Environment.SystemDirectory use exactly?  Could it be that it is not looking in the right location or that a %SystemDirectory% needs to be added?

Thanks,

David

---

### Post by ago on 2007-10-25
> **penguin22 said:**
> The exact error message that pops up on the screen is:

I am not sure what you compile in, but am under the assumption that the environment variables are determined differently than how Windows uses set commands.  What does the Environment.SystemDirectory use exactly?  Could it be that it is not looking in the right location or that a %SystemDirectory% needs to be added?



If you grap the mono compiler you can compile wubi.cs (link above) directly (mcs wubibcd.cs) and run the resulting executable with the arguments

wubibcd.exe /d "C:" /p "\ubuntu\winboot\wubildr.mbr" /t "Ubuntu Linux"

You can use Console.WriteLine in wubibcd.cs to output any message/variable value you want

---

### Post by penguin22 on 2007-10-25
Well I am not a great coder by any means and my testing was running the install, getting the error and opening a command prompt at the temp directory.  I ran what you posted verbatim as it applies to the install that I was performing and it is definitely no locating the bcdedit file.  If I wanted to manually run the bcdedit commands to create the proper boot options as the install finishes after the error, would you review the entries I should make?

I figure that it is two parts:

bcdedit /create /d "Ubuntu Linux" /application bootsector

and the second part would be to point it to the location:

C:\Ubuntu\winboot\wubildr.mbr

Is this a two command function or can it all be done in one bcdedit... They help for bcdedit didn't help too much.

Thanks,

David

---

### Post by ago on 2007-10-25
> **penguin22 said:**
> Well I am not a great coder by any means and my testing was running the install, getting the error and opening a command prompt at the temp directory.  I ran what you posted verbatim as it applies to the install that I was performing and it is definitely no locating the bcdedit file.  If I wanted to manually run the bcdedit commands to create the proper boot options as the install finishes after the error, would you review the entries I should make?

I figure that it is two parts:

bcdedit /create /d "Ubuntu Linux" /application bootsector

and the second part would be to point it to the location:

C:\Ubuntu\winboot\wubildr.mbr

Is this a two command function or can it all be done in one bcdedit... They help for bcdedit didn't help too much.

Thanks,

David

You can use EasyBcd for that. But I'd be really interested to know why it fails in your case. I will create a version tonight with more debugging messages.

---

### Post by penguin22 on 2007-10-25
In that case, I will wait for the updated debug build as I like the idea of having it properly uninstall and remove the bcd entries as well.  It is very odd indeed.

---

### Post by ago on 2007-10-25
Can you try rev370?

---

### Post by penguin22 on 2007-10-25
Vista was not happy with build 370.  It "encountered problems and had to close" at the bcd part, which was triggered by wubibcd.exe.  I can get event logs if that would help.

---

### Post by ago on 2007-10-25
> **penguin22 said:**
> Vista was not happy with build 370.  It "encountered problems and had to close" at the bcd part, which was triggered by wubibcd.exe.  I can get event logs if that would help.

yes please

---

### Post by penguin22 on 2007-10-25
The error was pretty much like any other Vista error, but the details that I was able to view with 372 at home said that the file could not be found.  Same error, only now Vista takes exception to it.

---

### Post by ago on 2007-10-25
374 will fail but at least the error should be a bit more informative

---

### Post by penguin22 on 2007-10-25
I can't explain it, but it now gives a meaningful error saying that the file that exists doesn't.

The file exists in C:\Windows\system32\bcdedit.exe, yet the error says that it is not found.  I am officially stumped.

---

### Post by Computer Guru on 2007-10-26
This sounds like it might be a BCD problem, instead of a Wubi one.

Can you install/run [EasyBCD]("http://neosmart.net/dl.php?id=1"), and paste the output of "Diagnostics | Copy Debug Data" here in a reply?

---

### Post by ago on 2007-10-26
Computer Guru, the line that fails is:

if (!File.Exists(Environment.SystemDirectory + "\\bcdedit.exe")) 

BCD is not even executed. It just cannot be found. Which is quite strange.

---

### Post by penguin22 on 2007-10-26
```
Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=D:
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {8342a97d-a18e-11db-a31d-c3f49148fdba}
resumeobject            {8342a97e-a18e-11db-a31d-c3f49148fdba}
displayorder            {466f5a88-0af2-4f76-9038-095b170dc21c}
                        {8342a97d-a18e-11db-a31d-c3f49148fdba}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 10

Windows Legacy OS Loader
------------------------
identifier              {466f5a88-0af2-4f76-9038-095b170dc21c}
device                  partition=D:
path                    \ntldr
description             Earlier Version of Windows

Windows Boot Loader
-------------------
identifier              {8342a97d-a18e-11db-a31d-c3f49148fdba}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {8342a97e-a18e-11db-a31d-c3f49148fdba}
nx                      OptIn

```

---

### Post by Computer Guru on 2007-10-26
> **ago said:**
> Computer Guru, the line that fails is:

if (!File.Exists(Environment.SystemDirectory + "\\bcdedit.exe")) 

BCD is not even executed. It just cannot be found. Which is quite strange.
Strange indeed - nothing wrong with the bcd output itself :/

Is this Windows 32-Bit or 64-Bit?

---

### Post by penguin22 on 2007-10-26
Two different Vista 64-bit machines, one Ultimate, the other Enterprise with the exact same results.  The Temp directory on both is different.  One the default under Users, the other in C:\Temp.  The file exists on both in C:\Windows\System32\bcdedit.exe.

If I am not mistaken, Ago even created a build that does not check and just assumes the file is there and that creates an exception in Vista as it even thinks the file isn't there.

Is any other Vista user experiencing this as if it were only one computer I'd say the problem is unique to it, but this is two separate machines?

---

### Post by Computer Guru on 2007-10-26
Can you run the attached file and paste the output here? (also from a CMD window)

I think it is checking \Windows\sysWOW64\ instead of \system32\
(contrary to what the names suggest, \system32\ contains the 64-bit executables and \syswow64\ contains the 32-bit ones.)

(the beauty of mono: I can compile programs for Windows users without leaving Linux!)

---

### Post by penguin22 on 2007-10-26
EnvTest.exe - NeoSmart Technologies

System Path: C:\Windows\system32

---

### Post by Computer Guru on 2007-10-26
OK, now I'm officially stumped!

It's saying that C:\Windows\System32\bcdedit.exe does **not** exist - but you verify that it does (and that's the default).

If you ran it (WubiBCD) as an Administrator, does it make any difference? (or is UAC already off)

To run as an ADministrator from cmd:
type in cmd.exe in the "search" box in the start menu and press ctrl+shift+enter
Then anything you run in that cmd.exe session will be run as admin.

---

### Post by penguin22 on 2007-10-26
Ah, good to have a blackberry that I can reply from.  I have UAC disabled on both, but have also run as admin for the wubi install.  Does easybcd wubi entry work with the current version?  I can add it with easybcd, but it gives no option for drive or path and it looks to be different than the ubuntu directory that the install creates.

---

### Post by Computer Guru on 2007-10-27
W/ EasyBCD you can add a Wubi entry - it'll search for Wubi's menu.lst and load it at boot.

---

### Post by doubleblack on 2007-10-27
Okay, I have it!

if (!File.Exists(Environment.SystemDirectory + "\\bcdedit.exe")) 

People have reported that this is where it fails, but they see system32/bcdedit.exe perfectly fine.  Well I was receiving another error before on x64 something to the effect BCD cannot be written, but it was documented before so I didn't register to bring it up.  Well now I don't get this error, I get the error saying bcdedit.exe cannot be found now using build 377.  But anyway, here is the problem:

Wubi is a x86 program, and thus the system directory it uses is SysWOW64 which emulates x86 stuff in x64 environments.  system32 is purely x64, while SysWOW64 is all x86.  Because bcdedit.exe on x64 machines is in system32, and Wubi is an x86 app looking in SysWOW64 that is causing problems.

Of course this is only a complete guess and I have no programming experience (networking background) and no proof or anything, but it seems very logical to me that this is the culprit.  I registered just for this, so hopefully this is some helpful feedback!

---

### Post by Computer Guru on 2007-10-27
Hi doubleblack, welcome to The Ubuntu Forums!

Actually, that's what the file I uploaded a couple of posts back is for - it's a quick program I wrote that will print the location of Environment.SystemDirectory - and unfortunately it returned \Windows\System32\.....

It is written in .NET/Mono, same as WubiBCD which is the app that is failing on his computer.

Wubi itself does not look for bcdedit.exe, rather it launches the command-line mono-powered WubiBCD, and WubiBCD does the looking.

---

### Post by doubleblack on 2007-10-27
Oh, alright then...well it seemed pretty logical to me.  Sorry I couldn't be of any more help though, not only am I not a programming person but I am not even a Linux person!  I was hoping to try to use Wubi on my laptop to help me fiddle around occasionally so I can at least get by.  I'm a Microsoft person always, MCSE and stuff...but I just like learning new things and I think I've learned about all you can in regards to Windows Administration and just looking for something else to tinker around with and am pretty sure Wubi is one of the best ways for me to accomplish that!

Keep up the good work everyone, and hopefully we can get this installed on some Vista x64 systems pretty soon!

---

### Post by anrichp on 2007-10-27
Hi everyone

I'm kinda new to ubuntu, and need some help I've got the latest version of wubi alpha rev 377 but after i install it and reboot my system , and boot up in ubuntu linux , it has the ubuntu starting screen and then goes to a black window saying something about busybox debian etc.
What do i need to do to get this working?

thnx

---

### Post by Computer Guru on 2007-10-27
> **doubleblack said:**
> Oh, alright then...well it seemed pretty logical to me.  Sorry I couldn't be of any more help though, not only am I not a programming person but I am not even a Linux person!  I was hoping to try to use Wubi on my laptop to help me fiddle around occasionally so I can at least get by.  I'm a Microsoft person always, MCSE and stuff...but I just like learning new things and I think I've learned about all you can in regards to Windows Administration and just looking for something else to tinker around with and am pretty sure Wubi is one of the best ways for me to accomplish that!

Keep up the good work everyone, and hopefully we can get this installed on some Vista x64 systems pretty soon!


You may yet be right... All I did was verify that system32 is indeed the path returned - however, it's possible that something about the way Vista is running NSIS or Wubi is causing it to return a different value under those circumstances.

penguin22, I've attached a different copy of WubiBCD. Can you replace the original WubiBCD.exe with this one and try again?
I've hardcoded the system32 path (not the recommended way of doing it, but since the recommended way is obviously failing...) and can't see any reason for this not to work now.

---

### Post by Computer Guru on 2007-10-27
Ago, would the NSIS package have to rebuilt with this test build of WubiBCD, or can penguin22 replace it on the fly? Do you have any idea where Wubi/NSIS extracts its contents to (maybe %temp%?) and if he can just replace it after Wubi starts but before it reaches the WubiBCD step?

---

### Post by penguin22 on 2007-10-27
I will try this in a little bit, I can pause the process as it begins and replace it on the fly.  Gotta love sysinternals :-). I am in the same boat with being a MS guy.  Wubi is yet another attempt to expand from windows CLI and basic scripting to unix/Linux.  I'll update shortly.

---

### Post by Cranchh on 2007-10-27
> **Computer Guru said:**
> You may yet be right... All I did was verify that system32 is indeed the path returned - however, it's possible that something about the way Vista is running NSIS or Wubi is causing it to return a different value under those circumstances.

penguin22, I've attached a different copy of WubiBCD. Can you replace the original WubiBCD.exe with this one and try again?
I've hardcoded the system32 path (not the recommended way of doing it, but since the recommended way is obviously failing...) and can't see any reason for this not to work now.

i have the same problem (working on vista ultimate 64), wubi rev377.

got this :

[wubibcd]
success=false
error=message

---

### Post by Computer Guru on 2007-10-27
> **penguin22 said:**
> I will try this in a little bit, I can pause the process as it begins and replace it on the fly.  Gotta love sysinternals :-). I am in the same boat with being a MS guy.  Wubi is yet another attempt to expand from windows CLI and basic scripting to unix/Linux.  I'll update shortly.
Good luck.

BTW, on the Windows Server 2003 servers I manage, I completely ditched Windows CLI and just installed Perl and Python - now all my server management, batch/cron jobs and everything else is either a pl or a py file... and it works great :)

Cranchh, it would seem that this is a global Vista x64-related problem. I'm afraid I don't have a 64-bit capable CPU (soon, soon!) and as such I can't test it myself which would probably have avoided this from happening in the first place. But if you guys are willing to try out the code, I'm willing to write it.

Go ahead and try what I recommended for penguin22 and replace WubiBCD with the one I uploaded if you like, it might do the trick.

---

### Post by penguin22 on 2007-10-27
C:\Users\PENGUI~1\AppData\Local\Temp\nssB373.tmp\wubibcd.exe 
 1:1 
 2: 
 3:HDD 
 4:3
Error while trying to execute: C:\Users\PENGUI~1\AppData\Local\Temp\nssB373.tmp\wubibcd.exe : 
vistaBootDriveCode = {} <=> 
vistaBootDriveCode {}
isFatFilesystem=false systemsize=17001 homesize=13000, swapsize=-1, usrsize=0
systemsize=17001 homesize=13000, swapsize=-1, usrsize=0
AllocFile filename=L:\ubuntu\disks\root.disk size=17001
AllocFile filename=L:\ubuntu\disks\home.disk size=13000
AllocFile filename=L:\ubuntu\disks\swap.disk size=-1
UncompressFilesAfterInstall
EjectCD

For some reason the post looks like there is a space in wubibcd.exe, but there is not.  I did not have to do anything special to overwrite as the file exists as soon as you start the program.  So I just overwrote it before clicking next.

Also, on my work laptop, I used EasyBCD to try and start wubi, but it doesn't seem to use the correct ubuntu\winboot\wubildr.mbr.  It uses a different one which loads some other shell.  Odd.

This is what EasyBCD adds:

Name:  Ubuntu Linux
BCD ID:  {5d8a4743-3fd4-11dc-93c1-0013d3605249}
Drive: Active Boot Partition
Bootloader Path:  \NST\NeoGrub.mbr

---

### Post by Cranchh on 2007-10-27
> **Computer Guru said:**
> 
Go ahead and try what I recommended for penguin22 and replace WubiBCD with the one I uploaded if you like, it might do the trick.

the last message was for the new file you uploaded.

i will try anything to make it work , and i have al the resources needed.
thanks :)

---

### Post by Computer Guru on 2007-10-27
hmph...

penguin: it's what's inside \NST\menu.lst that counts.

cranchh: didn't know that, but that's proof that there is something totally weird going on where Vista doesn't see bcdedit.exe when queried for it directly in WubiBCD - even with a hard-coded path.

--------------------

OK, I've attached another ZIP file. This time, it'll attempt to run bcdedit.exe from the local directory.

1) Overwrite existing WubiBCD with this one.
2) Copy \Windows\System32\bcdedit.exe to the same directory as WubiBCD.exe
3) Test.

Thanks.

---

### Post by Computer Guru on 2007-10-27
Here's another build (instead).

No need for bcdedit.exe anymore, just copy this WubiBCD over the the existing WubiBCD and test.

Also, updated the WubiBCD.ini to show an explicit error message instead of "error=message" (which is a bug!), so if it doesn't work, please post the full contents of WubiBCD.ini.

EDIT: If it doesn't work, copy bcdedit.exe to the same directory and try again.

---

### Post by doubleblack on 2007-10-27
I'm sorry if I'm a complete n00b here, but I can't find any WubiBCD.exe  to replace <_<

---

### Post by Computer Guru on 2007-10-27
It gets extracted to a folder in %temp%\ once you run Wubi.
Either search %temp% for WubiBCD.exe or sort by last modified and open the most recently created folder.

---

### Post by penguin22 on 2007-10-27
C:\Users\PENGUI~1\AppData\Local\Temp\nseB891.tmp\wubibcd.exe 
 1:1 
 2:The syntax of the command is incorrect.
Installs or removes Wubi from the Vista bootloader.

WubiBCD [[/d drive /p path | /uninstall]]

	/d		Identifies the drive to load the bootsector image from.
	/p		The path to the file relative to the root.
	/uninstall	Removes Wubi from the Vista BCD.
 
 3:HDD 
 4:3

EasyBCD confirms that it did not add.  bcdedit.exe was copied to the temp as well as the new wubibcd.exe.

---

### Post by Cranchh on 2007-10-27
with the last  wubibcd i got "the syntax of the command is incorect".


Computer guru: maybe you can connect via RDP or somthnig like that to my PC to check whats the problem.
Ill PM you with my messenger later.

---

### Post by Computer Guru on 2007-10-27
Are both of you running WubiBCD directly?
Wubi is supposed to run WubiBCD. It calls:
```
WubiBCD /d=C: /p=\wubi\boot\winboot\grldr.mbr
```
You can run that too if you want to run WubiBCD directly instead of having Wubi do it for you.

(I *think* that's the right path, but even if it's wrong the entry should still be added.
Ago, is that the right path to GRLDR?)

---

### Post by penguin22 on 2007-10-27
Just to confirm, it has been run in all cases with the install, replacing the wubibcd.exe at the first step when the temp dir is created.  With the latest wubibcd.exe, as instructed, I copied the windows\system32\bcdedit.exe file into the same temp directory.

To triple check, I ran the following (L drive at my home computer is where I want Wubi to run from):

C:\>cd\Users\Penguin22\AppData\Local\Temp\nspD050.tmp

C:\Users\Penguin22\AppData\Local\Temp\nspD050.tmp>wubibcd.exe /d "L:" /p "\ubunt
u\winboot\wubildr.mbr" /t "Ubuntu Linux"
The syntax of the command is incorrect.
Installs or removes Wubi from the Vista bootloader.

WubiBCD [[/d drive /p path | /uninstall]]

        /d              Identifies the drive to load the bootsector image from.
        /p              The path to the file relative to the root.
        /uninstall      Removes Wubi from the Vista BCD.

It seems that the new wubibcd.exe isn't seeing the args.

---

### Post by penguin22 on 2007-10-27
AND WE HAVE LIFTOFF!

After posting a second ago, I noticed that your command for wubibcd was different than Ago's posting at the beginning of this thread.  I tried to duplicate your commands with "=" and that had the same syntax error, but after deleting the spaces and removing the quotes wubibcd.exe finally worked.  Could the entire problem be the quotes?

C:\Users\Penguin22\AppData\Local\Temp\nspD050.tmp>wubibcd.exe /d L: /p \ubuntu\w
inboot\wubildr.mbr

And EadyBCD reports:

There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 5 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Wubi Ubuntu
BCD ID:  {5d8a4744-3fd4-11dc-93c1-0013d3605249}
Drive:  L:\
Bootloader Path:  \ubuntu\winboot\wubildr.mbr

In Ago's post he has /t "Ubuntu Linux", which I also removed as you can see.

---

### Post by Computer Guru on 2007-10-27
w00t!

the /t is not in my code, I see now that Ago's version was modified to add this feature - I'm adding it now to my new code.

Quotes were not the problem - a path without spaces doesn't have a problem with quotes or not. I'm still not sure WTF is wrong with Vista x64, but it still reports bcdedit.exe is not found in \Windows\System32\ so I just worked around that issue.

The attached version simply adds support for the /t flag.

Hopefully we'll get more verification that this works (and it had better still work on x86!!!) so we can put this issue to rest for once and for all.

(Ago, I don't have Bazaar set up so once all the kinks are sorted out I'll either upload or email you the code so you can commit it.)

---

### Post by Computer Guru on 2007-10-27
BTW, is this the correct path to Wubi's menu.lst?
```
\wubi\boot\grub\menu.lst
```

---

### Post by penguin22 on 2007-10-27
Well, I rebooted into Wubi Ubuntu and the installation began fine.  It gave a message about not configuring a swap partition and how the OS may run out of memory, but Go Back did not work and after rebooting into the installation a second time and clicking Continue, all seemed well.  After the installation (I didn't sit and watch it unfortunately as we are getting ready for a Halloween party tonight), it rebooted and I selected Wubi Ubuntu again and it gave and Error 17 file not found for all three boot options.  To this point, I was forced to the command line where I rebooted back into Vista.  Tonight I will uninstall and try again with your new wubibcd.exe and monitor the install.

Until then :-)

---

### Post by penguin22 on 2007-10-27
\ubuntu\winboot\menu.lst

although the bcd entry shows:

\ubuntu\winboot\wubildr.mbr

Likely two different things, eh?

---

### Post by Computer Guru on 2007-10-27
Thanks Penguin.

They are two different things, the .mbr one is the GRUB parser and the .lst is the config file.

EasyBCD 1.7 is still referencing \wubi\boot\grub\menu.lst so I'll have to update that for the upcoming 1.7.1 to point to \ubuntu\winboot\menu.lst

---

### Post by Cranchh on 2007-10-27
> **Computer Guru said:**
> BTW, is this the correct path to Wubi's menu.lst?
```
\wubi\boot\grub\menu.lst
```

```
\ubuntu\winboot\menu.lst
```

---

### Post by ago on 2007-10-27
> **Computer Guru said:**
> BTW, is this the correct path to Wubi's menu.lst?
```
\wubi\boot\grub\menu.lst
```

In 7.10 it is \ubuntu\winboot\menu.lst

---

### Post by Computer Guru on 2007-10-27
thanks guys.

penguin22: error 17 is a grub error - it means Vista's bootloader successfully loaded GRUB, and GRUB experienced a problem reading menu.lst. (either couldn't find menu.lst or a file that menu.lst lists)

It also means that WubiBCD works great :P

---

### Post by Cranchh on 2007-10-27
it is still not working for me:


```

C:\Users\Cranchh\AppData\Local\Temp\nsq2B6B.tmp>wubibcd.exe /d c: /p \ubuntu\winboot\
wubildr.mbr

Unhandled Exception: System.ComponentModel.Win32Exception: The system cannot fin
d the file specified
   at System.Diagnostics.Process.StartWithCreateProcess(ProcessStartInfo startIn
fo)
   at System.Diagnostics.Process.Start()
   at WubiBCD.WubiBCD.Install(String drive, String path, String title)
   at WubiBCD.WubiBCD.Main(String[] args)

C:\Users\Cranchh\AppData\Local\Temp\nsq2B6B.tmp>

```

don know what to do :(

---

### Post by Computer Guru on 2007-10-28
If you copy bcdedit.exe to the same directory, does it work?

---

### Post by Cranchh on 2007-10-28
now it is working. Great success :) 

with the wubibcd without the /t and copying the bcdedit to the same dir.

hope you can find the solution to the final ver now. 
good luck.

---

### Post by Computer Guru on 2007-10-28
I don't see much of a choice but to have the program copy bcdedit.exe to the same directory! :(

---

### Post by penguin22 on 2007-10-28
Well the method worked on both computers and on my desktop, the Error 17 was resolved by a post in another thread updating the from hd1,0 to hd2,0.  I am not sure if it is Wubi, Ubuntu or GRUB that misidentifies the hard drive, but it was an easy enough fix.  I do not mind blowing away this install and trying new Wubi builds to confirm compatibility with Vista x64.

The only thing now is finding out about drivers for my wireless network cards.  My home computer is the Atheros based D-link DWA-556 PCIExpress wireless N card and my laptop is the Broadcom based Dell 1505 N card.  Neither of them work with the drivers that Ubuntu has by default... same as with 7.04.  Doesn't bother me though as it gives me something to learn anyway ;-)

Thanks for all of your support and builds to help resolve this and I'm glad that I could be a testbed for you guys!

---

### Post by ago on 2007-10-28
> **penguin22 said:**
> Well the method worked on both computers and on my desktop, the Error 17 was resolved by a post in another thread updating the from hd1,0 to hd2,0.  I am not sure if it is Wubi, Ubuntu or GRUB that misidentifies the hard drive, but it was an easy enough fix. 

I'd need some help to figure it out, since I cannot reproduce that on my machine. You can join #wubi on freenode.net

---

### Post by Computer Guru on 2007-10-29
Can someone please verify that the attached WubiBCD.exe runs fine without BCDedit.exe in the same directory?

---

### Post by Computer Guru on 2007-10-29
Ago, could you please rename this thread to "Wubi Doesn't Install on Windows Vista x64" for SEO and legibility purposes?

---

### Post by ago on 2007-10-29
Sure, but it does install on Vista... Should check whether I have the 64 bit version, but it works well here...

---

### Post by ago on 2007-10-29
> **Computer Guru said:**
> Can someone please verify that the attached WubiBCD.exe runs fine without BCDedit.exe in the same directory?

I'll add it to new builds. But I am off for a few days starting tomorrow, so that might be delayed slightly, we'll have manual instructions for people in the meantime.

---

### Post by Computer Guru on 2007-10-29
> **ago said:**
> Sure, but it does install on Vista... Should check whether I have the 64 bit version, but it works well here...

Now I'm lost :)
I thought this was a global problem where WubiBCD wouldn't add the Wubi entry on all x64 environments? Or is it specific to certain x64-only users?

(better yet, is there a launchpad link for this bug?)

Thanks for changing the title though..

---

### Post by ago on 2007-10-29
> **Computer Guru said:**
> Now I'm lost :)
I thought this was a global problem where WubiBCD wouldn't add the Wubi entry on all x64 environments? Or is it specific to certain x64-only users?
I do have vista and a 64 bit laptop, but I have to check whether I have 64 or 32 bit vista. All I know it works here. But it might well be that I do have 32 bit vista and that the issue is confirmed for 64bit Vista. 

> (better yet, is there a launchpad link for this bug?)
I must admit I am a bit lazy with launchpad bugs, feel free to add one...

---

### Post by ago on 2007-10-29
Computer Guru, I'd need the source of that if possible

---

### Post by Computer Guru on 2007-10-30
Here you are.

---

### Post by ago on 2007-10-30
Computer Guru would it be possible to use the regstry as opposed to the ini file? I think it's safer when the user deletes manually the ubuntu folder and then wants to remove the rest.

You can see current wubibcd code in [http://codebrowse.launchpad.net/~ubuntu-installer/wubi/gutsy/annotate/ago%40nb-ago-20071029092825-4lobj8eb3s1qqg2q?file_id=wubibcd.cs-20071025011419-ch0wj8h6sla9af3w-4](http://codebrowse.launchpad.net/~ubuntu-installer/wubi/gutsy/annotate/ago%40nb-ago-20071029092825-4lobj8eb3s1qqg2q?file_id=wubibcd.cs-20071025011419-ch0wj8h6sla9af3w-4)

---

### Post by Computer Guru on 2007-10-30
Sure, that would work :) (I despise the registry as a matter of princple, but so long as its there, I guess we might as well use it ;))

I'll work on that as soon as I find out if this damn bug is fixed though - I think I'm going to have to talk to one of my MS contacts about that though, because it seems to be a bug in the .NET Framework :S

BTW, did you find out if your laptop is x64? Running winver.exe should do the trick.

---

### Post by ago on 2007-10-30
> **Computer Guru said:**
> Sure, that would work :) (I despise the registry as a matter of princple, but so long as its there, I guess we might as well use it ;))

I agree, but we have everything there for uninstallation settings, since you need a key to be in add/remove anyway... mix and matches are an even a worse idea then the registry.

> I'll work on that as soon as I find out if this damn bug is fixed though - I think I'm going to have to talk to one of my MS contacts about that though, because it seems to be a bug in the .NET Framework :S

BTW, did you find out if your laptop is x64? Running winver.exe should do the trick.
I can do that tonight, but I think it is 32 bit

---

### Post by Computer Guru on 2007-10-30
> **ago said:**
> I agree, but we have everything there for uninstallation settings, since you need a key to be in add/remove anyway... mix and matches are an even a worse idea then the registry.


I can do that tonight, but I think it is 32 bit
Definitely :)

Perhaps penguin or cranchh can verify that the latest version works without bcdedit.exe in the same directory? (I'm thankfully Vista-free at the moment)

---

### Post by penguin22 on 2007-10-30
I have no problems testing.  The latest version that you posted is the one you are referring to I guess?  Will this require me to manually run Wubibcd.exe with arguments or is that part fixed as well?  The quotes that are part of 377 caused wubibcd.exe to fail.  I am not sure if version 381 resolves this yet as I don't think any part of this thread has been addressed in that.  In fact, I believe that it is purely a fix for Error 17, which I was able to resolve manually.

Let me know what to test as I have no problems blowing away ubuntu for you guys and reinstalling.

---

### Post by Computer Guru on 2007-10-30
There is no need to blow away anything :)

If you just execute WubiBCD with the arguments above, it should just add an extra entry to the boot menu which you should be able to safely delete with EasyBCD.

I just want to know if this build (latest post w/ an attachment) works without BCDedit.exe in the same directory.

Thanks for your help so far, you've all been awesome! :)

---

### Post by Cranchh on 2007-10-30
rev 381 has the same problem.(bcedit not found)
i can check any version if you want.
do you have changes log for those alpha versions?

---

### Post by penguin22 on 2007-10-30
E:\Downloads\- Beta ->wubibcd.exe /d C: /p \ubuntu\winboot\wubildr.mbr

Unhandled Exception: System.IO.DirectoryNotFoundException: Could not find a part o
f the path 'System\bcdedit.exe'.
   at System.IO.__Error.WinIOError(Int32 errorCode, String maybeFullPath)
   at System.IO.File.InternalCopy(String sourceFileName, String destFileName, Bool
ean overwrite)
   at WubiBCD.WubiBCD.CopyBcd()
   at WubiBCD.WubiBCD.Install(String drive, String path, String title)
   at WubiBCD.WubiBCD.Main(String[] args)

---

### Post by Computer Guru on 2007-10-30
Sorry about that, that's a typo on my behalf!

Attached fixed version. Hopefully this fixes it.......

---

### Post by penguin22 on 2007-10-30
Why does it lie???

E:\Downloads\- Beta ->wubibcd.exe /d C: /p \ubuntu\winboot\wubildr.mbr

Unhandled Exception: System.IO.FileNotFoundException: Could not find file 'C:\Wind
ows\system32\bcdedit.exe'.
File name: 'C:\Windows\system32\bcdedit.exe'
   at System.IO.__Error.WinIOError(Int32 errorCode, String maybeFullPath)
   at System.IO.File.InternalCopy(String sourceFileName, String destFileName, Bool
ean overwrite)
   at WubiBCD.WubiBCD.CopyBcd()
   at WubiBCD.WubiBCD.Install(String drive, String path, String title)
   at WubiBCD.WubiBCD.Main(String[] args)

---

### Post by Computer Guru on 2007-10-30
I don't know!! :(

Vista can't do anything right... it even b0rked the lie-detector! :@

I've attached YAB (yet another build, might as well get used to that notation!) perhaps this time...

Thanks for bearing with me here :)

---

### Post by penguin22 on 2007-10-30
Requesting YAB:

Description:
  Stopped working

Problem signature:
  Problem Event Name:	CLR20r3
  Problem Signature 01:	wubibcd.exe
  Problem Signature 02:	1.1.0.42659
  Problem Signature 03:	4727a526
  Problem Signature 04:	System
  Problem Signature 05:	2.0.0.0
  Problem Signature 06:	4536f31b
  Problem Signature 07:	3915
  Problem Signature 08:	394
  Problem Signature 09:	System.ComponentModel.Win32
  OS Version:	6.0.6000.2.0.0.256.1
  Locale ID:	1033

and from CMD

E:\Downloads\- Beta ->wubibcd.exe /d C: /p \ubuntu\winboot\wubildr.mbr

Unhandled Exception: System.ComponentModel.Win32Exception: The system cannot fin
d the file specified
   at System.Diagnostics.Process.StartWithCreateProcess(ProcessStartInfo startIn
fo)
   at System.Diagnostics.Process.Start()
   at WubiBCD.WubiBCD.CopyBcd()
   at WubiBCD.WubiBCD.Install(String drive, String path, String title)
   at WubiBCD.WubiBCD.Main(String[] args)

---

### Post by ago on 2007-10-31
Wow didn't think was such a can of worms... Thanks Computer Guru and penguin22 for helping out.

---

### Post by Computer Guru on 2007-10-31
:??

[http://groups.google.com/group/microsoft.public.dotnet.languages.csharp/browse_thread/thread/fc12827392819285/1bd8322fa7beefb3#1bd8322fa7beefb3](http://groups.google.com/group/microsoft.public.dotnet.languages.csharp/browse_thread/thread/fc12827392819285/1bd8322fa7beefb3#1bd8322fa7beefb3)

I posted a request for a sane explanation in the .NET newsgroups..... perhaps something will come of it.

(I also couldn't resist taking a poke at them by making references to Python's duck typing..... Python is a good language that doesn't have this issue!)

---

### Post by Computer Guru on 2007-10-31
Penguin, can you check the event viewer and see if it logs any errors (particularly in the security section)

---

### Post by penguin22 on 2007-11-01
There was not much to mention in Security event logs.  Perhaps it doesn't log there.  Also, from CMD, I am able to cd to C:\Windows\System32 and run commands with bcdedit directly.  This is with UAC disabled.  They may have a point with .NET having a security restriction.  Is it possible to have .NET batch a command so that you are outside of the .NET security?

---

### Post by Computer Guru on 2007-11-07
OK, it looks like this a Vista bug that MS pretends is a feature - only they didn't even bother posting about it anywhere :x
 
Give this a shot guys?

---

### Post by penguin22 on 2007-11-07
Great news.  It worked completely using:

wubibcd.exe /d C: /p \ubuntu\winboot\wubildr.mbr

I did not play with the quotes or /t at all.  If you want me to test any additional cmd arguments, let me know (that is for Computer Guru or Ago so that this can make it into a general Wubi build).

There were no errors and bcdedit.exe remains in Windows\System32 where it belongs.

I saw that the .NET thread had been updated with some good information and was wondering where you had been and if you would update this thread :-)  It's been busy at work for me, so I figured I'd be patient waiting, especially since I have a working Ubuntu now.

Great job guys!:KS

---

### Post by ago on 2007-11-07
All the credit goes to Computer Guru! 
Good stuff! 
Just show me the code (with registry) and I'll push it in...

---

### Post by Computer Guru on 2007-11-07
No registry code yet, I wanted to get the x64 bug out first before I did the registy stuff.

All I need to store in the registry is a dword value with the ID of the WubiBCD entry in it.

Where shall I store it?

---

### Post by ago on 2007-11-07
> **Computer Guru said:**
> No registry code yet, I wanted to get the x64 bug out first before I did the registy stuff.

All I need to store in the registry is a dword value with the ID of the WubiBCD entry in it.

Where shall I store it?

In fact you do not have to store it at all, we take care of that from within nsis
You can reuse the current wubi code: 

[http://codebrowse.launchpad.net/~ubuntu-installer/wubi/gutsy/annotate/ago%40nbago-20071102122146-bu83bnmgvfion3ay?file_id=wubibcd.cs-20071025011419-ch0wj8h6sla9af3w-4](http://codebrowse.launchpad.net/~ubuntu-installer/wubi/gutsy/annotate/ago%40nbago-20071102122146-bu83bnmgvfion3ay?file_id=wubibcd.cs-20071025011419-ch0wj8h6sla9af3w-4)

---

### Post by Computer Guru on 2007-11-07
OK, this should do the trick:

```
WubiBCD [/d drive /p path [/t title] | /uninstall {id}]

        /d              Identifies the drive to load the bootsector image from.
        /p              The path to the file relative to the root.
        /t              The title of the new entry to be created.
        /uninstall      Removes the specified BCD id from the Vista BCD.

```

Install an entry:
```
WubiBCD /d c: /p \path\to\GRLDR /t "Ubuntu Linux"
```
Output:
```
Operation completed successfully. New ID is {id}
```

Remove an entry:
```
WubiBCD /uninstall {id}
```
Output:
```
Wubi successfully uninstalled from the Vista bootloader.
```

No INI files are created or used.

{id} is regex-checked to make sure it's in the proper form.

"/t title" is optional.


Returns int 0 on success, 1 on failure + writes a message to the console for debugging purposes when manually run (i.e. not via Wubi NSIS)

If bcdedit.exe error is encountered, it'll return 1 + print the error spit out by bcdedit.exe

On an x86 system, it'll run \Windows\System32\bcededit.exe
On an x64 system, it'll run \Windows\sysnative\bcdedit.exe

If not running Windows Vista, WubiBCD will gracefully exit:

```
Not running Windows Vista or Longhorn Server!
```

*phew*

:guitar:

Attached source + exe.

---

### Post by ago on 2007-11-07
Really great work!!! Thanks a bunch.
I will push it up tonight

---

### Post by ago on 2007-11-07
There you have it, rev 384

---

### Post by Computer Guru on 2007-11-07
Awesome, thanks.

(and congratulations on your "Iced Blended Vanilla Crème Ubuntu" it sounds yummy!!!)

---

### Post by doubleblack on 2007-11-07
I am taking responsibility of initial testing, downloading now!

---

### Post by Computer Guru on 2007-11-07
Good luck :)

---

### Post by doubleblack on 2007-11-08
Alright, works great!  No problems or error messages this time at all!

Now once I got into ubuntu, I was getting the NTFS + chkdsk /f problem (not to mention had to boot into installer using safe mode graphics) - but that's a whole other problem <_<

But the BCD thing is no longer an issue, congrats to all!

---

### Post by penguin22 on 2007-11-08
All works well now for me too.  Congrats on the great work!  Learn something new every day huh?

---

### Post by Computer Guru on 2007-11-08
That "[SOLVED]" tag looks *soooooooooooo* good! :D

---

### Post by ago on 2007-11-08
Yeah I wish I'd be able to use it more often... :D

---

### Post by System64 on 2008-01-20
I am running (i think) the final version of wubi from the 64bit Ubuntu Disc. The method does not seem to work, as after trying, i still keep getting error while trying to execute :bcdedit:. The setup phase is at Execshell:Compact and it's running on Vista 64. Yes it's 7.10

Do i need to do anything extra? such as copying the stuffs from the disc?

---

### Post by ago on 2008-01-21
Try easybcd

---

