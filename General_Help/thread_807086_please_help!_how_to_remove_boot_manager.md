---
title: "please help! how to remove boot manager?"
date: 2008-05-25
forum: General Help
---

### Post by SeanEE89 on 2008-05-25
I am new to Linux and my friend gave me Wubi to install Ubuntu on my computer and I installed it on the wrong partition and I did delete it and now I am unable to remove the select OS boot manager option during my boot up in the Windows Manager.  

I was wondering if anyone would be able to help me remove it because I decided I want to install Linux on a different computer. 

Please any help would be greatly appreciated especially because I am such a newb with Linux.

---

### Post by 505 on 2008-05-25
If you want to remove the bootloader and only run Windows on that computer, boot into Windows and use the command "fixmbr". If the command is not available download that program. It is a Microsoft program and should be available for download. It will restore the Windows bootloader.

---

### Post by SeanEE89 on 2008-05-25
What program should I download? Would you be able to provide a link for me to go to?

Also does the fact that I use 64-bit Windows Vista Ultimate make and difference?

---

### Post by Dave2k6 on 2008-05-25
yes it does. use your windows vista dvd to restore vista's boot manager, or use [EasyBCD]("http://neosmart.net/downloads/software/EasyBCD/EasyBCD%201.7.2.exe") to restore vista's boot manager

---

### Post by ago on 2008-05-26
Use EasyBCD to edit your vista menu.

---

### Post by rossjamesparker on 2008-05-26
I had this same problem - playing around with WUBI and then even after I uninstalled it, the boot menu remained. Will try these fixes. It's a shame wubi's uninstall doesn't do what it says on the tin.

---

### Post by ago on 2008-05-26
It does remove the boot entries, unless you remove the ubuntu folder before running the uninstaller....

---

### Post by arinlares on 2008-05-27
i have the same problem, on XP.  i don't want to run a full recovery (my mom and brother will kill me).  I was trying to use the live cd, when wubi snuck in.  is there a fixmbr for XP?

---

### Post by ago on 2008-05-28
Wubi does not touch the mbr, the worse it can happen is that you hard reboot and the windows filesystem gets corrupted (which in most cases can be recovered via chkdsk /r). And wubi does not replace the boot manager (unless you did a full installation). So all there is to do is to remove the wubi line in C:\boot.ini (XP) or use EasyBCD (vista)

---

### Post by arinlares on 2008-05-28
> **ago said:**
> Wubi does not touch the mbr, the worse it can happen is that you hard reboot and the windows filesystem gets corrupted (which in most cases can be recovered via chkdsk /r). And wubi does not replace the boot manager (unless you did a full installation). So all there is to do is to remove the wubi line in C:\boot.ini (XP) or use EasyBCD (vista)

can you give or link to instructions? i'm good with computers, but i'm also kinda paranoid about settings.

---

### Post by ago on 2008-05-29
> **arinlares said:**
> can you give or link to instructions? i'm good with computers, but i'm also kinda paranoid about settings.

In XP open C:\boot.ini with notepad (it might be hidden so make sure you can see hidden files). There is one line about wubildr.mbr. Delete it and save the file

In vista, download and run EasyBCD

---

### Post by Dave2k6 on 2008-05-29
Download EasyBCD from [here](http://neosmart.net/downloads/software/EasyBCD/EasyBCD%201.7.2.exe) (if you run Vista) to edit Vista's boot menu and remove the Ubuntu option. Else, edit the c:\boot.ini file (use Notepad to edit it), and remove the Ubuntu line.

---

### Post by arinlares on 2008-05-30
it doesn't have a wubi line in it

this is the contents of the file

```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

```

---

### Post by 1154 on 2008-05-31
@arinlares: You dont have to do a complete recovery, just boot into recovery from the XP instalation CD & run da command "FIXMBR" which will re-write your MBR...

**EDIT:** Doing that will probably remove your "Microsoft Windows Recovery Console" option! So you would have to reinstall it or edit your boot.ini file i suppose...

---

### Post by ago on 2008-05-31
> **arinlares said:**
> it doesn't have a wubi line in it

this is the contents of the file

```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

```
Do you have the permission to edit boot.ini

---

### Post by Tomatz on 2008-05-31
> **505 said:**
> If you want to remove the bootloader and only run Windows on that computer, boot into Windows and use the command "fixmbr". If the command is not available download that program. It is a Microsoft program and should be available for download. It will restore the Windows bootloader.

Nope

If you used wubi, start xp then go to:

control panel, system, advanced (tab), **startup and recovery**

Then just edit the conf file (self explanitory once you get there). Deleting the ubuntu boot line.

;)

---

### Post by arinlares on 2008-05-31
@ ago: yes I have permission to edit the file, but the Wubi line doesn't exist (I used the uninstaller properly)

@tomatz: It opens "boot.ini", but I can't do anything because there is no line for Ubuntu.

the code in my earlier post is the WHOLE file, I opened, cut and pasted it to the forum.

---

### Post by Tomatz on 2008-05-31
That's weird???

If it were me i would just change the timeout to like 1 or 2 seconds (or even 0 if you are brave). That way it shouldn't really annoy you.


;)

---

### Post by ago on 2008-06-01
can you post the wubi log in your user temp folder?

---

### Post by arinlares on 2008-06-01
not sure what you are talking about

is it "C:\Temp" ?  there isn't a Wubi file there. I have "t4.log

```
2006-07-24 21:45:31:781 ->Open: LOG OPENED
2006-07-24 21:45:31:812 ->Creating a MonProc pointer...Creating a MonProc instance...Querying for a MonProc interface...MonProc interface exists!
2006-07-24 21:45:32:843 ->GetPaths: Current directory = E:\
2006-07-24 21:45:32:875 ->FindInstallerPath(): Using default installer
2006-07-24 21:45:32:875 ->FindInstallerPath(): Path = E:\AOL90S\setup90.exe -z ; Version = 9.7
2006-07-24 21:45:32:875 ->ReadRegistryValue(): Value: LastRegisteredAppPath; Data: ; Read? 0
2006-07-24 21:45:32:875 ->FindInstallerPath(): Path = E:\AOL90S\setup90.exe -z ; Version = 9.7
2006-07-24 21:45:32:875 ->IsCompatible:  OS, IE, RAM, HD, & Ports are compatible.
2006-07-24 21:45:32:875 ->OS = 5.1,Service Pack 2  IE = 62900.2180  RAM = 504  HD = 114364
2006-07-24 21:45:34:984 ->Enter CMonProc::get_DetectFirewall()
2006-07-24 21:45:37:750 ->ACS ExistingConnection(): Result = 1
2006-07-24 21:45:37:750 ->T4PostMsg(): AfxGetMainWnd; Msg: 1131, Ret: 1
2006-07-24 21:45:37:781 ->ExistingConnection: Looking for existing connection...Found an existing connection.
2006-07-24 21:45:37:812 ->ExistingConnection: Looking for existing connection...Found an existing connection.Connection exists!
2006-07-24 21:45:37:890 ->WindowProc():  WM_STARTWEBREG received...
2006-07-24 21:45:38:00 ->WindowProc():  WM_TIMER received...
2006-07-24 21:45:38:31 ->WindowProc():  StartWebReg timer received.
2006-07-24 21:45:38:31 ->StartWebReg():
2006-07-24 21:45:38:31 ->Start Post Metrics
2006-07-24 21:45:38:31 ->Using proxy for current POST? False
2006-07-24 21:45:38:31 ->CRBIACS::GetMachineID: MID = 0
2006-07-24 21:45:38:62 ->ProcessRequest: START_SESSION
2006-07-24 21:45:38:62 ->PostMetrics: START_SESSION Attempt 1
2006-07-24 21:45:38:62 ->MetricsTracker::Post()
2006-07-24 21:45:38:62 ->Post(): Setting connection & post timeout values to 15000 & 90000
2006-07-24 21:45:56:921 ->Post(): Request success
2006-07-24 21:45:56:937 ->Post(): Read 32 byte(s)
2006-07-24 21:45:56:937 ->StartWebReg(): START_SESSION complete
2006-07-24 21:45:56:937 ->Start Post Metrics
2006-07-24 21:45:56:937 ->Using proxy for current POST? False
2006-07-24 21:45:56:937 ->ProcessRequest: UI_REQUEST
2006-07-24 21:45:56:937 ->PostMetrics: UI_REQUEST Attempt 1
2006-07-24 21:45:56:937 ->MetricsTracker::Post()
2006-07-24 21:45:56:937 ->Post(): Setting connection & post timeout values to 15000 & 90000
2006-07-24 21:45:59:109 ->Post(): Request success
2006-07-24 21:45:59:859 ->Post(): Read 5033 byte(s)
2006-07-24 21:45:59:859 ->StartWebReg(): Loading web registration page
2006-07-24 21:45:59:859 ->LoadPage(): Loading page = http://free.aol.com/tryaolfree/t4UI?STATE=UI_REQUEST&BAT_ID=34717.1153802766.779538:REGISTER&service=T4&conn=t
2006-07-24 21:46:13:859 ->OnDocumentComplete(): Web Reg UI loaded!!!
2006-07-24 21:46:13:859 ->T4PostMsg(): AfxGetMainWnd; Msg: 1135, Ret: 1
2006-07-24 21:46:13:875 ->WindowProc():  WM_POSTWEBREGMETRICS received...
2006-07-24 21:46:13:875 ->Start Post Metrics
2006-07-24 21:46:13:875 ->Using proxy for current POST? False
2006-07-24 21:46:13:875 ->ProcessRequest: C2
2006-07-24 21:46:13:875 ->PostMetrics: C2 Attempt 1
2006-07-24 21:46:13:875 ->MetricsTracker::Post()
2006-07-24 21:46:13:875 ->Post(): Setting connection & post timeout values to 15000 & 90000
2006-07-24 21:46:14:406 ->Post(): Request success
2006-07-24 21:46:14:406 ->Post(): Read 1 byte(s)
2006-07-24 21:46:21:921 ->NewMember: Setting the new member variable to current
2006-07-24 21:47:18:625 ->T4PostMsg(): AfxGetMainWnd; Msg: 1127, Ret: 1
2006-07-24 21:47:18:625 ->LaunchInstaller(): Launching as 'current' member
2006-07-24 21:47:18:640 ->WindowProc():  WM_LAUNCHINSTALLER received...
2006-07-24 21:47:18:640 ->Start Post Metrics
2006-07-24 21:47:18:640 ->Using proxy for current POST? False
2006-07-24 21:47:18:640 ->ProcessRequest: C4a
2006-07-24 21:47:18:640 ->PostMetrics: C4a Attempt 1
2006-07-24 21:47:18:640 ->MetricsTracker::Post()
2006-07-24 21:47:18:640 ->Post(): Setting connection & post timeout values to 15000 & 90000
2006-07-24 21:47:19:531 ->Post(): Request success
2006-07-24 21:47:19:531 ->Post(): Read 1 byte(s)
2006-07-24 21:47:19:531 ->Start Post Metrics
2006-07-24 21:47:19:531 ->Using proxy for current POST? False
2006-07-24 21:47:19:531 ->ProcessRequest: C5
2006-07-24 21:47:19:531 ->PostMetrics: C5 Attempt 1
2006-07-24 21:47:19:531 ->MetricsTracker::Post()
2006-07-24 21:47:19:531 ->Post(): Setting connection & post timeout values to 15000 & 90000
2006-07-24 21:47:20:312 ->Post(): Request success
2006-07-24 21:47:20:312 ->Post(): Read 1 byte(s)
2006-07-24 21:47:20:312 ->Start Post Metrics
2006-07-24 21:47:20:312 ->Using proxy for current POST? False
2006-07-24 21:47:20:312 ->ProcessRequest: END_SESSION
2006-07-24 21:47:20:312 ->PostMetrics: END_SESSION Attempt 1
2006-07-24 21:47:20:312 ->MetricsTracker::Post()
2006-07-24 21:47:20:312 ->Post(): Setting connection & post timeout values to 15000 & 90000
2006-07-24 21:47:21:46 ->Post(): Request success
2006-07-24 21:47:21:46 ->Post(): Read 1 byte(s)
2006-07-24 21:47:21:46 ->LaunchInstallerInstaller launched as a existing member!
2006-07-24 21:47:21:46 ->StartInstallCD results: Command line is  -e
2006-07-24 21:47:21:46 ->Installer Path: E:\AOL90S\setup90.exe -z   -e
2006-07-24 21:47:21:46 ->StartInstallCD results: Creating new installer process...
2006-07-24 21:47:24:109 ->StartInstallCD results: Exiting install section.
2006-07-24 21:47:24:109 ->StartInstallCD results: Exiting install section.LaunchInstaller:  Process complete.  Quiting.
2006-07-24 21:47:24:109 ->T4PostMsg(): AfxGetMainWnd; Msg: 1128, Ret: 1
2006-07-24 21:47:24:109 ->WindowProc():  WM_CLOSEBROWSER received...
2006-07-24 21:47:24:109 ->CMainFrame::OnClose():  Closing the browser and exiting!
2006-07-24 21:47:24:109 ->CRBICtrl::CloseBrowser(): Disconnecting with install
2006-07-24 21:47:24:109 ->CRBICtrl::Disconnect(): FORCING ACS to disconnect
2006-07-24 21:47:24:390 ->AOLT4 shuting down!!! Bye!
2006-07-24 21:47:24:390 ->Close: LOG CLOSING

```

that is the only text file available in the TEMP folder.

---

### Post by ago on 2008-06-02
Each user in windows has a dedicated temp folder
Type %temp% in windows explorer URL bar

---

### Post by pete-the-meat on 2008-06-02
Editing the BOOT.INI file in Windows will let you remove the choose operating system option. Follow the steps here: [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by arinlares on 2008-06-04
couldn't find it.  Ago, i want to thank you for your help, but I don't think i should worry about this right now.  When I turn my computer on, the boot manager's 15 second countdown is done, so it isn't really an issue.  Yet again, thanks for all of your assistance.

---

### Post by Tomatz on 2008-06-04
> **arinlares said:**
> couldn't find it.  Ago, i want to thank you for your help, but I don't think i should worry about this right now.  When I turn my computer on, the boot manager's 15 second countdown is done, so it isn't really an issue.  Yet again, thanks for all of your assistance.

Lower the timeout ;)

---

### Post by stevenincleelum on 2008-06-05
In vista to remove an entry created by ubuntu that was installed in vista 

run CMD as administrator

Then type bcdedit

It will give a readout similiar to this

Windows Boot Manager
----------------------------
identifier {bootmgr}
device partition=C:
description Windows Boot Manager
locale en-US
inherit {globalsettings}
default {current}
resumeobject {3fcc4b92-260f-55ab-6a28-c3fd78c2f4ad}
displayorder {current}
{ntldr}
toolisdisplayorder {memdiag}
timeout {30}

Windows Boot Loader
--------------------------
identifier {current}
device partition=C:
path \Windows\system32\winload.exe
description Microsoft Windows Vista
locale en-US
inherit {bootloadersettings}
osdevice partition=C:
systemroot \Windows
resumeobject {3fcc4b92-260f-55ab-6a28-c3fd78c2f4ad}
nx OptIn

If ubuntu has a number like 

{3fcc4b92-260f-55ab-6a28-c3fd78c2f4ad}

then just type

bcdedit /delete {3fcc4b92-260f-55ab-6a28-c3fd78c2f4ad}

and it is gone

---

### Post by b@zou on 2008-06-05
In boot.ini, choose 0 for timeout (no risk in theory) or you have the other solution with editing the properties in the Windows system. In XP, choose "System properties"(to display the system properties dialog box)-> "Advanced" tab -> "Start up and recovery" Settings ->  choose 0 seconds for "time to display list of operating systems"

more details:
[http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)

---

