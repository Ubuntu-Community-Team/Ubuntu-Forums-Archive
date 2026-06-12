---
title: "Need help installing ubuntu"
date: 2013-01-13
forum: General Help
---

### Post by iseeu1001 on 2013-01-13
I can't install ubuntu no matter what I do :-( Here is what I tired. 
[http://www.youtube.com/watch?v=O7Bcc7b3OuM](http://www.youtube.com/watch?v=O7Bcc7b3OuM)

This is what I get when I do windows installer.

[IMG]http://ubuntuforums.org/[IMG]http://i1020.photobucket.com/albums/af325/eminembeastfan25/Capture-59.png[/IMG]
[IMG]http://i1020.photobucket.com/albums/af325/eminembeastfan25/Capture-59.png[/IMG]

Please help me I really want to use ubuntu and windows so I am trying to install ubuntu but I can't. Sorry for the quality shot with my iphone 4s and I forgot to cut some parts.

---

### Post by mlentink on 2013-01-14
Are you sure you want to install Ubuntu through Wubi? Wubi is nice, but does seem to have its limitations. The amount of space you can use for Ubuntu is limited.

To read about your installation options please have a look here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by iseeu1001 on 2013-01-14
> **mlentink said:**
> Are you sure you want to install Ubuntu through Wubi? Wubi is nice, but does seem to have its limitations. The amount of space you can use for Ubuntu is limited.

To read about your installation options please have a look here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
  Yes I used wubi and  the error in the picture above is what is I get.

---

### Post by cottfcfan on 2013-01-14
What I think mlentink is saying, is that, wubi is not the best way to install Ubuntu.
It is way better to re-partition your hard drive & install it as a dual boot system.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> What I think mlentink is saying, is that, wubi is not the best way to install Ubuntu.
It is way better to re-partition your hard drive & install it as a dual boot system.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
This is a new os I reinstalled already that's why I wanted to dual boot with windows and did you see the a seperate parition disk in my computer for ubuntu in the video?

---

### Post by cottfcfan on 2013-01-14
> **iseeu1001 said:**
> This is a new os I reinstalled already that's why I wanted to dual boot with windows and did you see the a seperate parition disk in my computer for ubuntu in the video?

But in your last post you said you used Wubi??
If you wish to dual boot you need to download the iso from here:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> But in your last post you said you used Wubi??
If you wish to dual boot you need to download the iso from here:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Please watch the video I use the disc its inside my laptop and I used wubi so I tried mostly everything.

EDIT:

This is what I get in the log

```
01-13 22:32 INFO   root: === wubi 12.10 rev273 ===
01-13 22:32 DEBUG  root: Logfile is c:\users\david\appdata\local\temp\wubi-12.10-rev273.log
01-13 22:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
01-13 22:32 DEBUG  CommonBackend: data_dir=C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\data
01-13 22:32 DEBUG  WindowsBackend: 7z=C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\bin\7z.exe
01-13 22:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-13 22:32 DEBUG  CommonBackend: Fetching basic info...
01-13 22:32 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
01-13 22:32 DEBUG  CommonBackend: platform=win32
01-13 22:32 DEBUG  CommonBackend: osname=nt
01-13 22:32 DEBUG  CommonBackend: language=en_US
01-13 22:32 DEBUG  CommonBackend: encoding=cp1252
01-13 22:32 DEBUG  WindowsBackend: arch=amd64
01-13 22:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\data\isolist.ini
01-13 22:32 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-13 22:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 22:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 22:32 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-13 22:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 22:32 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-13 22:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 22:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 22:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 22:32 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-13 22:32 DEBUG  WindowsBackend: Fetching host info...
01-13 22:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 22:32 DEBUG  WindowsBackend: windows version=vista
01-13 22:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-13 22:32 DEBUG  WindowsBackend: windows_sp=None
01-13 22:32 DEBUG  WindowsBackend: windows_build=7600
01-13 22:32 DEBUG  WindowsBackend: gmt=-5
01-13 22:32 DEBUG  WindowsBackend: country=US
01-13 22:32 DEBUG  WindowsBackend: timezone=America/New_York
01-13 22:32 DEBUG  WindowsBackend: windows_username=David
01-13 22:32 DEBUG  WindowsBackend: user_full_name=David
01-13 22:32 DEBUG  WindowsBackend: user_directory=C:\Users\David
01-13 22:32 DEBUG  WindowsBackend: windows_language_code=1033
01-13 22:32 DEBUG  WindowsBackend: windows_language=English
01-13 22:32 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II P650 Dual-Core Processor
01-13 22:32 DEBUG  WindowsBackend: bootloader=vista
01-13 22:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 197883.742188 mb free ntfs)
01-13 22:32 DEBUG  WindowsBackend: drive=Drive(C: hd 197883.742188 mb free ntfs)
01-13 22:32 DEBUG  WindowsBackend: drive=Drive(D: hd 1928.03125 mb free ntfs)
01-13 22:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-13 22:32 DEBUG  WindowsBackend: drive=Drive(F: hd 226713.804688 mb free ntfs)
01-13 22:32 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-13 22:32 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-13 22:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-13 22:32 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 22:32 DEBUG  WindowsBackend: keyboard_layout=us
01-13 22:32 DEBUG  WindowsBackend: keyboard_variant=
01-13 22:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-13 22:32 DEBUG  CommonBackend: locale=en_US.UTF-8
01-13 22:32 DEBUG  WindowsBackend: total_memory_mb=3834.90234375
01-13 22:32 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 22:32 DEBUG  CommonBackend: Searching for local CDs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Ubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Ubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Kubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Kubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Mythbuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Mythbuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Edubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Edubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Lubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl91A4.tmp is a valid Lubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-13 22:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:32 INFO   root: Running the uninstaller...
01-13 22:32 INFO   CommonBackend: This is the uninstaller running
01-13 22:32 DEBUG  WindowsFrontend: __init__...
01-13 22:32 DEBUG  WindowsFrontend: on_init...
01-13 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\translations, languages=['en_US', 'en']
01-13 22:32 INFO   root: Received settings
01-13 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\translations, languages=['en_US', 'en']
01-13 22:32 DEBUG  TaskList: # Running tasklist...
01-13 22:32 DEBUG  TaskList: ## Running Remove bootloader entry...
01-13 22:32 DEBUG  WindowsBackend: Could not find bcd id
01-13 22:32 DEBUG  WindowsBackend: undo_bootini C:
01-13 22:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 197883.742188 mb free ntfs)
01-13 22:32 DEBUG  WindowsBackend: undo_bootini D:
01-13 22:32 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1928.03125 mb free ntfs)
01-13 22:32 DEBUG  WindowsBackend: undo_bootini F:
01-13 22:32 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 226713.804688 mb free ntfs)
01-13 22:32 DEBUG  TaskList: ## Finished Remove bootloader entry
01-13 22:32 DEBUG  TaskList: ## Running Remove target dir...
01-13 22:32 DEBUG  CommonBackend: Deleting C:\ubuntu
01-13 22:32 DEBUG  TaskList: ## Finished Remove target dir
01-13 22:32 DEBUG  TaskList: ## Running Remove registry key...
01-13 22:32 DEBUG  TaskList: ## Finished Remove registry key
01-13 22:32 DEBUG  TaskList: # Finished tasklist
01-13 22:32 INFO   root: Almost finished uninstalling
01-13 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl91A4.tmp\translations, languages=['en_US', 'en']
01-13 22:32 INFO   root: Finished uninstallation
01-13 22:32 DEBUG  root: application.quit
01-13 22:32 DEBUG  WindowsFrontend: frontend.quit
01-13 22:32 DEBUG  WindowsFrontend: frontend.on_quit
01-13 22:32 DEBUG  root: application.on_quit
01-13 22:32 INFO   root: sys.exit
01-13 22:46 INFO   root: === wubi 12.10 rev273 ===
01-13 22:46 DEBUG  root: Logfile is c:\users\david\appdata\local\temp\wubi-12.10-rev273.log
01-13 22:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\David\\Downloads\\wubi(1).exe"']
01-13 22:46 DEBUG  root: Logfile is c:\users\david\appdata\local\temp\wubi-12.10-rev273.log
01-13 22:46 DEBUG  CommonBackend: data_dir=C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\data
01-13 22:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\David\\Downloads\\wubi(1).exe"']
01-13 22:46 DEBUG  WindowsBackend: 7z=C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\bin\7z.exe
01-13 22:46 DEBUG  CommonBackend: data_dir=C:\Users\David\AppData\Local\Temp\pyl9482.tmp\data
01-13 22:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-13 22:46 DEBUG  WindowsBackend: 7z=C:\Users\David\AppData\Local\Temp\pyl9482.tmp\bin\7z.exe
01-13 22:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-13 22:46 DEBUG  CommonBackend: Fetching basic info...
01-13 22:46 DEBUG  CommonBackend: original_exe=C:\Users\David\Downloads\wubi(1).exe
01-13 22:46 DEBUG  CommonBackend: platform=win32
01-13 22:46 DEBUG  CommonBackend: osname=nt
01-13 22:46 DEBUG  CommonBackend: language=en_US
01-13 22:46 DEBUG  CommonBackend: encoding=cp1252
01-13 22:46 DEBUG  CommonBackend: Fetching basic info...
01-13 22:46 DEBUG  CommonBackend: original_exe=C:\Users\David\Downloads\wubi(1).exe
01-13 22:46 DEBUG  CommonBackend: platform=win32
01-13 22:46 DEBUG  CommonBackend: osname=nt
01-13 22:46 DEBUG  CommonBackend: language=en_US
01-13 22:46 DEBUG  CommonBackend: encoding=cp1252
01-13 22:46 DEBUG  WindowsBackend: arch=amd64
01-13 22:46 DEBUG  WindowsBackend: arch=amd64
01-13 22:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\David\AppData\Local\Temp\pyl9482.tmp\data\isolist.ini
01-13 22:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\data\isolist.ini
01-13 22:46 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-13 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 22:46 DEBUG  WindowsBackend: Fetching host info...
01-13 22:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 22:46 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-13 22:46 DEBUG  WindowsBackend: windows version=vista
01-13 22:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-13 22:46 DEBUG  WindowsBackend: Fetching host info...
01-13 22:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 22:46 DEBUG  WindowsBackend: windows version=vista
01-13 22:46 DEBUG  WindowsBackend: windows_sp=None
01-13 22:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-13 22:46 DEBUG  WindowsBackend: windows_build=7600
01-13 22:46 DEBUG  WindowsBackend: gmt=-5
01-13 22:46 DEBUG  WindowsBackend: windows_sp=None
01-13 22:46 DEBUG  WindowsBackend: country=US
01-13 22:46 DEBUG  WindowsBackend: windows_build=7600
01-13 22:46 DEBUG  WindowsBackend: timezone=America/New_York
01-13 22:46 DEBUG  WindowsBackend: gmt=-5
01-13 22:46 DEBUG  WindowsBackend: country=US
01-13 22:46 DEBUG  WindowsBackend: timezone=America/New_York
01-13 22:46 DEBUG  WindowsBackend: windows_username=David
01-13 22:46 DEBUG  WindowsBackend: user_full_name=David
01-13 22:46 DEBUG  WindowsBackend: user_directory=C:\Users\David
01-13 22:46 DEBUG  WindowsBackend: windows_username=David
01-13 22:46 DEBUG  WindowsBackend: windows_language_code=1033
01-13 22:46 DEBUG  WindowsBackend: user_full_name=David
01-13 22:46 DEBUG  WindowsBackend: windows_language=English
01-13 22:46 DEBUG  WindowsBackend: user_directory=C:\Users\David
01-13 22:46 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II P650 Dual-Core Processor
01-13 22:46 DEBUG  WindowsBackend: windows_language_code=1033
01-13 22:46 DEBUG  WindowsBackend: bootloader=vista
01-13 22:46 DEBUG  WindowsBackend: windows_language=English
01-13 22:46 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II P650 Dual-Core Processor
01-13 22:46 DEBUG  WindowsBackend: bootloader=vista
01-13 22:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 197964.53125 mb free ntfs)
01-13 22:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 197964.53125 mb free ntfs)
01-13 22:46 DEBUG  WindowsBackend: drive=Drive(D: hd 1928.03125 mb free ntfs)
01-13 22:46 DEBUG  WindowsBackend: drive=Drive(C: hd 197964.53125 mb free ntfs)
01-13 22:46 DEBUG  WindowsBackend: drive=Drive(D: hd 1928.03125 mb free ntfs)
01-13 22:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-13 22:46 DEBUG  WindowsBackend: drive=Drive(F: hd 223143.089844 mb free ntfs)
01-13 22:46 DEBUG  WindowsBackend: uninstaller_path=F:\ubuntu\uninstall-wubi.exe
01-13 22:46 DEBUG  WindowsBackend: previous_target_dir=F:\ubuntu
01-13 22:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-13 22:46 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 22:46 DEBUG  WindowsBackend: keyboard_layout=us
01-13 22:46 DEBUG  WindowsBackend: keyboard_variant=
01-13 22:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-13 22:46 DEBUG  CommonBackend: locale=en_US.UTF-8
01-13 22:46 DEBUG  WindowsBackend: total_memory_mb=3834.90234375
01-13 22:46 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 22:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-13 22:46 DEBUG  WindowsBackend: drive=Drive(F: hd 223143.089844 mb free ntfs)
01-13 22:46 DEBUG  WindowsBackend: uninstaller_path=F:\ubuntu\uninstall-wubi.exe
01-13 22:46 DEBUG  WindowsBackend: previous_target_dir=F:\ubuntu
01-13 22:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-13 22:46 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 22:46 DEBUG  WindowsBackend: keyboard_layout=us
01-13 22:46 DEBUG  WindowsBackend: keyboard_variant=
01-13 22:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-13 22:46 DEBUG  CommonBackend: locale=en_US.UTF-8
01-13 22:46 DEBUG  WindowsBackend: total_memory_mb=3834.90234375
01-13 22:46 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 22:46 DEBUG  CommonBackend: Searching for local CDs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  CommonBackend: Searching for local CDs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl94B0.tmp is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl94B0.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
\pyl9482.tmp is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
mp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl9482.tmp is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl9482.tmp\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 INFO   root: Already installed, running the uninstaller...
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:46 INFO   root: Running the uninstaller...
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-13 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:46 INFO   root: Already installed, running the uninstaller...
01-13 22:46 INFO   root: Running the uninstaller...
01-13 22:46 INFO   CommonBackend: Launching previous uninestaller F:\ubuntu\uninstall-wubi.exe
01-13 22:46 INFO   CommonBackend: Launching previous uninestaller F:\ubuntu\uninstall-wubi.exe
01-13 22:46 DEBUG  root: application.quit
01-13 22:46 DEBUG  root: application.on_quit
01-13 22:46 INFO   root: sys.exit
01-13 22:46 INFO   root: Quitting application
01-13 22:46 DEBUG  root: application.quit
01-13 22:46 DEBUG  root: application.on_quit
01-13 22:46 INFO   root: sys.exit
01-13 22:46 INFO   root: Quitting application
01-13 22:47 INFO   root: === wubi 12.10 rev273 ===
01-13 22:47 DEBUG  root: Logfile is c:\users\david\appdata\local\temp\wubi-12.10-rev273.log
01-13 22:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\David\\Downloads\\wubi(2).exe"']
01-13 22:47 DEBUG  CommonBackend: data_dir=C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\data
01-13 22:47 DEBUG  WindowsBackend: 7z=C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\bin\7z.exe
01-13 22:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-13 22:47 DEBUG  CommonBackend: Fetching basic info...
01-13 22:47 DEBUG  CommonBackend: original_exe=C:\Users\David\Downloads\wubi(2).exe
01-13 22:47 DEBUG  CommonBackend: platform=win32
01-13 22:47 DEBUG  CommonBackend: osname=nt
01-13 22:47 DEBUG  CommonBackend: language=en_US
01-13 22:47 DEBUG  CommonBackend: encoding=cp1252
01-13 22:47 DEBUG  WindowsBackend: arch=amd64
01-13 22:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\data\isolist.ini
01-13 22:47 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-13 22:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 22:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 22:47 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-13 22:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 22:47 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-13 22:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 22:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 22:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 22:47 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-13 22:47 DEBUG  WindowsBackend: Fetching host info...
01-13 22:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 22:47 DEBUG  WindowsBackend: windows version=vista
01-13 22:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-13 22:47 DEBUG  WindowsBackend: windows_sp=None
01-13 22:47 DEBUG  WindowsBackend: windows_build=7600
01-13 22:47 DEBUG  WindowsBackend: gmt=-5
01-13 22:47 DEBUG  WindowsBackend: country=US
01-13 22:47 DEBUG  WindowsBackend: timezone=America/New_York
01-13 22:47 DEBUG  WindowsBackend: windows_username=David
01-13 22:47 DEBUG  WindowsBackend: user_full_name=David
01-13 22:47 DEBUG  WindowsBackend: user_directory=C:\Users\David
01-13 22:47 DEBUG  WindowsBackend: windows_language_code=1033
01-13 22:47 DEBUG  WindowsBackend: windows_language=English
01-13 22:47 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II P650 Dual-Core Processor
01-13 22:47 DEBUG  WindowsBackend: bootloader=vista
01-13 22:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 197971.21875 mb free ntfs)
01-13 22:47 DEBUG  WindowsBackend: drive=Drive(C: hd 197971.21875 mb free ntfs)
01-13 22:47 DEBUG  WindowsBackend: drive=Drive(D: hd 1928.03125 mb free ntfs)
01-13 22:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-13 22:47 DEBUG  WindowsBackend: drive=Drive(F: hd 226713.804688 mb free ntfs)
01-13 22:47 DEBUG  WindowsBackend: uninstaller_path=None
01-13 22:47 DEBUG  WindowsBackend: previous_target_dir=None
01-13 22:47 DEBUG  WindowsBackend: previous_distro_name=None
01-13 22:47 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 22:47 DEBUG  WindowsBackend: keyboard_layout=us
01-13 22:47 DEBUG  WindowsBackend: keyboard_variant=
01-13 22:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-13 22:47 DEBUG  CommonBackend: locale=en_US.UTF-8
01-13 22:47 DEBUG  WindowsBackend: total_memory_mb=3834.90234375
01-13 22:47 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 22:47 DEBUG  CommonBackend: Searching for local CDs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Kubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Kubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Mythbuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Mythbuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Edubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Edubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Lubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Lubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 INFO   root: Running the installer...
01-13 22:47 DEBUG  WindowsFrontend: __init__...
01-13 22:47 DEBUG  WindowsFrontend: on_init...
01-13 22:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\translations, languages=['en_US', 'en']
01-13 22:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\translations, languages=['en_US', 'en']
01-13 22:47 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=david
01-13 22:47 INFO   root: Received settings
01-13 22:47 DEBUG  CommonBackend: Searching for local CD
01-13 22:47 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl1C85.tmp is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 22:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 22:47 DEBUG  CommonBackend: Searching for local ISO
01-13 22:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl1C85.tmp\translations, languages=['en_US', 'en']
01-13 22:47 DEBUG  TaskList: # Running tasklist...
01-13 22:47 DEBUG  TaskList: ## Running select_target_dir...
01-13 22:47 INFO   WindowsBackend: Installing into F:\ubuntu
01-13 22:47 DEBUG  TaskList: ## Finished select_target_dir
01-13 22:47 DEBUG  TaskList: ## Running create_dir_structure...
01-13 22:47 DEBUG  CommonBackend: Creating dir F:\ubuntu
01-13 22:47 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks
01-13 22:47 DEBUG  CommonBackend: Creating dir F:\ubuntu\install
01-13 22:47 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot
01-13 22:47 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot
01-13 22:47 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot\grub
01-13 22:47 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot\grub
01-13 22:47 DEBUG  TaskList: ## Finished create_dir_structure
01-13 22:47 DEBUG  TaskList: ## Running create_uninstaller...
01-13 22:47 DEBUG  WindowsBackend: Copying uninstaller C:\Users\David\Downloads\wubi(2).exe -> F:\ubuntu\uninstall-wubi.exe
01-13 22:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString F:\ubuntu\uninstall-wubi.exe
01-13 22:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir F:\ubuntu
01-13 22:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-13 22:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon F:\ubuntu\Ubuntu.ico
01-13 22:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
01-13 22:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-13 22:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-13 22:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-13 22:47 DEBUG  TaskList: ## Finished create_uninstaller
01-13 22:47 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-13 22:47 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-13 22:47 DEBUG  TaskList: ## Running get_diskimage...
01-13 22:47 DEBUG  TaskList: New task download
01-13 22:47 DEBUG  TaskList: ### Running download...
01-13 22:47 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > F:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
01-13 22:47 DEBUG  downloader: Download start filename=F:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
01-13 22:52 DEBUG  TaskList: ### Finished download
01-13 22:52 DEBUG  downloader: download finished (read 562061340 bytes)
01-13 22:52 DEBUG  TaskList: ## Finished get_diskimage
01-13 22:52 DEBUG  TaskList: ## Running extract_diskimage...
01-13 22:53 DEBUG  TaskList: ## Finished extract_diskimage
01-13 22:53 DEBUG  TaskList: ## Running choose_disk_sizes...
01-13 22:53 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
01-13 22:53 DEBUG  TaskList: ## Finished choose_disk_sizes
01-13 22:53 DEBUG  TaskList: ## Running expand_diskimage...
01-13 22:55 DEBUG  TaskList: ## Finished expand_diskimage
01-13 22:55 DEBUG  TaskList: ## Running create_swap_diskimage...
01-13 22:55 DEBUG  TaskList: ## Finished create_swap_diskimage
01-13 22:55 DEBUG  TaskList: ## Running modify_bootloader...
01-13 22:55 DEBUG  TaskList: New task modify_bcd
01-13 22:55 DEBUG  TaskList: ### Running modify_bcd...
01-13 22:55 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 197971.21875 mb free ntfs)
01-13 22:55 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {e92bb6bd-5dc5-11e2-b6cf-dcd4dbe9c685} device partition=F:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {e92bb6bd-5dc5-11e2-b6cf-dcd4dbe9c685} device partition=F:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
01-13 22:55 DEBUG  TaskList: # Cancelling tasklist
01-13 22:55 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {e92bb6bd-5dc5-11e2-b6cf-dcd4dbe9c685} device partition=F:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {e92bb6bd-5dc5-11e2-b6cf-dcd4dbe9c685} device partition=F:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
01-13 22:55 DEBUG  TaskList: New task modify_bcd
01-13 22:55 DEBUG  TaskList: New task modify_bcd
01-13 22:55 DEBUG  TaskList: ## Finished modify_bootloader
01-13 22:55 DEBUG  TaskList: # Finished tasklist
01-14 09:41 INFO   root: === wubi 12.10 rev273 ===
01-14 09:41 DEBUG  root: Logfile is c:\users\david\appdata\local\temp\wubi-12.10-rev273.log
01-14 09:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\ubuntu\\uninstall-wubi.exe"']
01-14 09:41 DEBUG  CommonBackend: data_dir=C:\Users\David\AppData\Local\Temp\pyl6351.tmp\data
01-14 09:41 DEBUG  WindowsBackend: 7z=C:\Users\David\AppData\Local\Temp\pyl6351.tmp\bin\7z.exe
01-14 09:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-14 09:41 DEBUG  CommonBackend: Fetching basic info...
01-14 09:41 DEBUG  CommonBackend: original_exe=F:\ubuntu\uninstall-wubi.exe
01-14 09:41 DEBUG  CommonBackend: platform=win32
01-14 09:41 DEBUG  CommonBackend: osname=nt
01-14 09:41 DEBUG  CommonBackend: language=en_US
01-14 09:41 DEBUG  CommonBackend: encoding=cp1252
01-14 09:41 DEBUG  WindowsBackend: arch=amd64
01-14 09:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\David\AppData\Local\Temp\pyl6351.tmp\data\isolist.ini
01-14 09:41 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-14 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 09:41 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-14 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 09:41 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-14 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 09:41 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-14 09:41 DEBUG  WindowsBackend: Fetching host info...
01-14 09:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 09:41 DEBUG  WindowsBackend: windows version=vista
01-14 09:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-14 09:41 DEBUG  WindowsBackend: windows_sp=None
01-14 09:41 DEBUG  WindowsBackend: windows_build=7600
01-14 09:41 DEBUG  WindowsBackend: gmt=-5
01-14 09:41 DEBUG  WindowsBackend: country=US
01-14 09:41 DEBUG  WindowsBackend: timezone=America/New_York
01-14 09:41 DEBUG  WindowsBackend: windows_username=David
01-14 09:41 DEBUG  WindowsBackend: user_full_name=David
01-14 09:41 DEBUG  WindowsBackend: user_directory=C:\Users\David
01-14 09:41 DEBUG  WindowsBackend: windows_language_code=1033
01-14 09:41 DEBUG  WindowsBackend: windows_language=English
01-14 09:41 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II P650 Dual-Core Processor
01-14 09:41 DEBUG  WindowsBackend: bootloader=vista
01-14 09:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195964.257813 mb free ntfs)
01-14 09:41 DEBUG  WindowsBackend: drive=Drive(C: hd 195964.257813 mb free ntfs)
01-14 09:41 DEBUG  WindowsBackend: drive=Drive(D: hd 1928.03125 mb free ntfs)
01-14 09:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-14 09:41 DEBUG  WindowsBackend: drive=Drive(F: hd 222897.097656 mb free ntfs)
01-14 09:41 DEBUG  WindowsBackend: uninstaller_path=F:\ubuntu\uninstall-wubi.exe
01-14 09:41 DEBUG  WindowsBackend: previous_target_dir=F:\ubuntu
01-14 09:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-14 09:41 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 09:41 DEBUG  WindowsBackend: keyboard_layout=us
01-14 09:41 DEBUG  WindowsBackend: keyboard_variant=
01-14 09:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 09:41 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 09:41 DEBUG  WindowsBackend: total_memory_mb=3834.90234375
01-14 09:41 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 09:41 DEBUG  CommonBackend: Searching for local CDs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Ubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Ubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Kubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Kubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Mythbuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Mythbuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Edubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Edubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Lubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether C:\Users\David\AppData\Local\Temp\pyl6351.tmp is a valid Lubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain C:\Users\David\AppData\Local\Temp\pyl6351.tmp\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-14 09:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-14 09:41 INFO   root: Running the uninstaller...
01-14 09:41 INFO   CommonBackend: This is the uninstaller running
01-14 09:41 DEBUG  WindowsFrontend: __init__...
01-14 09:41 DEBUG  WindowsFrontend: on_init...
01-14 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl6351.tmp\translations, languages=['en_US', 'en']
01-14 09:41 INFO   root: Received settings
01-14 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl6351.tmp\translations, languages=['en_US', 'en']
01-14 09:41 DEBUG  TaskList: # Running tasklist...
01-14 09:41 DEBUG  TaskList: ## Running Remove bootloader entry...
01-14 09:41 DEBUG  WindowsBackend: Could not find bcd id
01-14 09:41 DEBUG  WindowsBackend: undo_bootini C:
01-14 09:41 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195964.257813 mb free ntfs)
01-14 09:41 DEBUG  WindowsBackend: undo_bootini D:
01-14 09:41 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1928.03125 mb free ntfs)
01-14 09:41 DEBUG  WindowsBackend: undo_bootini F:
01-14 09:41 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 222897.097656 mb free ntfs)
01-14 09:41 DEBUG  TaskList: ## Finished Remove bootloader entry
01-14 09:41 DEBUG  TaskList: ## Running Remove target dir...
01-14 09:41 DEBUG  CommonBackend: Deleting F:\ubuntu
01-14 09:41 DEBUG  TaskList: ## Finished Remove target dir
01-14 09:41 DEBUG  TaskList: ## Running Remove registry key...
01-14 09:41 DEBUG  TaskList: ## Finished Remove registry key
01-14 09:41 DEBUG  TaskList: # Finished tasklist
01-14 09:41 INFO   root: Almost finished uninstalling
01-14 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\David\AppData\Local\Temp\pyl6351.tmp\translations, languages=['en_US', 'en']
01-14 09:41 INFO   root: Finished uninstallation
01-14 09:41 DEBUG  root: application.quit
01-14 09:41 DEBUG  WindowsFrontend: frontend.quit
01-14 09:41 DEBUG  WindowsFrontend: frontend.on_quit
01-14 09:41 DEBUG  root: application.on_quit
01-14 09:41 INFO   root: sys.exit
```

---

### Post by cottfcfan on 2013-01-14
I've just watched your video.
What you are trying to do is install Ubuntu from inside Windows (wubi). This doesn't always work well for everyone.
What you may want to do is a proper install using an iso from the link in the above post. You can use this as a live cd/usb to make sure everything works, then install to your hard disc alongside Windows. You are more likely to have success that way.

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> I've just watched your video.
What you are trying to do is install Ubuntu from inside Windows (wubi). This doesn't always work well for everyone.
What you may want to do is a proper install using an iso from the link in the above post. You can use this as a live cd/usb to make sure everything works, then install to your hard disc alongside Windows. You are more likely to have success that way.
I don't get what your saying I used the other option to if you watched the whole video not just install inside of windows.

---

### Post by cottfcfan on 2013-01-14
I've watched the whole video, when it came to the installation option, you clicked to "install inside windows", & proceeded to boot back into windows again.
You need to pick the option to either "install alongside windows" or "something else", and place Ubuntu on your own created partition.

---

### Post by cottfcfan on 2013-01-14
iseeu1001. 

If you download the correct iso from the link I gave you and then follow the tutorial here, you will see how your wubi disc differs from the standard desktop iso, and it might make more sense what you need to do:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
Scroll down to the "install" part.

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> I've watched the whole video, when it came to the installation option, you clicked to "install inside windows", & proceeded to boot back into windows again.
You need to pick the option to either "install alongside windows" or "something else", and place Ubuntu on your own created partition.
I did do something else also but I don't get what you mean by placing ubuntu on your own created partition I picked the ubuntu partition on my hard drive but no difference I get that " no root file system is defined Please correct this from the partition menu".

---

### Post by cottfcfan on 2013-01-14
Ok go back to using the "something else" box, look at the link in the above post, and scroll down to the box that says "installation type".
What you need to do is highlight the partition you want Ubuntu to be installed on, (not windows obviously), click the "change" button, as in the next diagram. An "edit partition" box will open.
You need "use as" to be ext4, tick "format the partition" box, and the mouse point you want as "/". (that's defining your root file system) Click ok, and carry on with the installation.

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> Ok go back to using the "something else" box, look at the link in the above post, and scroll down to the box that says "installation type".
What you need to do is highlight the partition you want Ubuntu to be installed on, (not windows obviously), click the "change" button, as in the next diagram. An "edit partition" box will open.
You need "use as" to be ext4, tick "format the partition" box, and the mouse point you want as "/". (that's defining your root file system) Click ok, and carry on with the installation.
I get this 
[IMG]http://i1020.photobucket.com/albums/af325/eminembeastfan25/Snapbucket/9D68EC1B.jpg[/IMG]
Now my windows is f**K*D up and I gotta reinstall :(, now how do I fix that grub install error?

---

### Post by cottfcfan on 2013-01-14
Your windows is ok it's just the mbr that will have been partially overwritten by Ubuntu's grub.
 I've never had a disk that hasn't been able to install Grub before.
 Did you download the disk from the link I gave you or did you use the wubi disk that you had?

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> Your windows is ok it's just the mbr that will have been partially overwritten by Ubuntu's grub.
 I've never had a disk that hasn't been able to install Grub before.
 Did you download the disk from the link I gave you or did you use the wubi disk that you had?
Yes like I said I used the iso and tried wubi before. I used the ubuntu iso and got the error remember and you let me pass that error but now a new error from the cd and now I can't see my C or D drive or any other drive when trying to reinstall my windows so I can't reinstall windows at all.

---

### Post by cottfcfan on 2013-01-14
Sorry I don't understand your reply, did you use your wubi disc or a fresh disk from the link?

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> Sorry I don't understand your reply, did you use your wubi disc or a fresh disk from the link?
I use the disk from the list. I am using my other computer since I can't even reinstall windows on my laptop anymore.

---

### Post by cottfcfan on 2013-01-14
Windows is still there don't worry about that.
Lets start again.
1st, please boot into your live CD, open up gparted & take a screenshot of your partition table & post it here.

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> Windows is still there don't worry about that.
Lets start again.
1st, please boot into your live CD, open up gparted & take a screenshot of your partition table & post it here.
What do you mean by gparted? Here is my partition in ubuntu cd and from windows 7 cd 

[IMG]http://i1020.photobucket.com/albums/af325/eminembeastfan25/Snapbucket/79FFBCB1.jpg[/IMG]

[IMG]http://i1020.photobucket.com/albums/af325/eminembeastfan25/Snapbucket/C6FA53E7.jpg[/IMG]

---

### Post by cottfcfan on 2013-01-14
Gparted is a program on your Ubuntu live CD, but the information you have provided is what I was looking for.
The reason you can't re-install windows is because it won't like your sda4 ext4 partition.
What the 1mb sda1 is I have no idea, seems strange.
Before re-installing windows, try 1st fixing the MBR, using the tutorial here:
[http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)
If that fails try again to install the Ubuntu live CD as before, you might be luckier this time.
If you wanted to reinstall Windows boot back into the Ubuntu live CD, start the program gparted, delete all the partitions & re-format the whole disc as ntfs. (this will delete everything though). Then boot back into your windows cd & reinstall.

Before doing that you might want to wait & see if anyone else chimes in with any ideas.

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> Gparted is a program on your Ubuntu live CD, but the information you have provided is what I was looking for.
The reason you can't re-install windows is because it won't like your sda4 ext4 partition.
What the 1mb sda1 is I have no idea, seems strange.
Before re-installing windows, try 1st fixing the MBR, using the tutorial here:
[http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)
If that fails try again to install the Ubuntu live CD as before, you might be luckier this time.
If you wanted to reinstall Windows boot back into the Ubuntu live CD, start the program gparted, delete all the partitions & re-format the whole disc as ntfs. (this will delete everything though). Then boot back into your windows cd & reinstall.

Before doing that you might want to wait & see if anyone else chimes in with any ideas.
 
I will try to install back windows 7 but I can't delete the whole partition on my pc because 1 of the partition is for a HP partition because I don't know where to get srs premium sound driver that is why I am still using the HP partition and I can't use the hp partition yet so I am going to try the link you gave me.

---

### Post by iseeu1001 on 2013-01-14
I still can't install windows :( You messed up my computer I can't even reinstall windows or anything. Now I have to figure out how to make it work again even thought I have no idea what to do -.-

---

### Post by cottfcfan on 2013-01-14
Do you have a windows disc?
If so you must be able to re-install windows, all you need to do is make sure all your partitions are ntfs.
Change your sda4 partition from ext4 to ntfs, using gparted on your live CD.
Or make the whole hard drive one large ntfs partition, and let your Windows disc, sort out it's own partitioning when re-installing.

---

### Post by iseeu1001 on 2013-01-14
> **cottfcfan said:**
> Do you have a windows disc?
If so you must be able to re-install windows, all you need to do is make sure all your partitions are ntfs.
Change your sda4 partition from ext4 to ntfs, using gparted on your live CD.
Or make the whole hard drive one large ntfs partition, and let your Windows disc, sort out it's own partitioning when re-installing.
I couldn't even use the hp partition or the windows disk so I just used ubuntu and reformatted or whatever you call it for ubuntu and I just used the windows disk to reformat the ubuntu reformat and I just reinstalled windows but I lost my hp partition -.- now I will never have srs home premium sound driver no more but I did get windows 7 back and will try to install ubuntu after I get my pc back with all drivers and stuff.

---

### Post by speartip on 2013-01-14
I'm glad you got Windows back that's something.
Before you try installing Ubuntu or anything else for that matter in the future, post a screenshot of your partition table first, so we know how best to help you proceed.
As for your srs sound driver, could you not download it from here:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=0&prodSeriesId=4065889&prodNameId=4065890&swEnvOID=1093&swLang=13&mode=2&swItem=vc-86314-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=0&prodSeriesId=4065889&prodNameId=4065890&swEnvOID=1093&swLang=13&mode=2&swItem=vc-86314-1)

---

### Post by linuxcoffeelover on 2013-01-14
Hi if your going to try to install Ubuntu again something I like to do sometimes is boot into the ubuntu livecd or a gparted livecd. Partition everything first and set the partitions, mount points, and formats so all you have to do is click on the partition you want and install. you want to install windows first then ubuntu second so when grub is installed it will overwrite the windows mbr and then you can choose with OS you want to boot into. sometimes grub fails to install you can install try to install grub the livecd after your reboot.

---

### Post by iseeu1001 on 2013-01-14
> **speartip said:**
> I'm glad you got Windows back that's something.
Before you try installing Ubuntu or anything else for that matter in the future, post a screenshot of your partition table first, so we know how best to help you proceed.
As for your srs sound driver, could you not download it from here:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=0&prodSeriesId=4065889&prodNameId=4065890&swEnvOID=1093&swLang=13&mode=2&swItem=vc-86314-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=0&prodSeriesId=4065889&prodNameId=4065890&swEnvOID=1093&swLang=13&mode=2&swItem=vc-86314-1)

I don't think so because mine is a laptop and my laptop is not on the hardware product models list but yes I will try to install ubuntu after I do some stuff.

---

### Post by iseeu1001 on 2013-01-14
I got ubuntu to install but I got a question if I can get a virus for windows on some website can I get a website virus on ubuntu? Also since I am dual booting on the same hard drive can the virus spread from the windows to the ubuntu OS? Also how do i cuztomize my mouse scroll because it scrolls to big

---

### Post by linuxcoffeelover on 2013-01-14
My laptop wasn't on the hardware compatibly list either but but ubuntu is update with drivers and just works with most hardware that is out there the sd card reader didn't work maybe like 4 or 5 distro's ago but I found out it works fine on 12.04.
 and I haven't seen a virus that works on windows and on linux I haven't gotten anything malicious on linux. I don't think so but that doesn't mean its not imposable  just be careful and setup a firewall and antivirus software on windows and a firewall on linux and you should be fine.

---

### Post by iseeu1001 on 2013-01-14
> **linuxcoffeelover said:**
> My laptop wasn't on the hardware compatibly list either but but ubuntu is update with drivers and just works with most hardware that is out there the sd card reader didn't work maybe like 4 or 5 distro's ago but I found out it works fine on 12.04.
 and I haven't seen a virus that works on windows and on linux I haven't gotten anything malicious on linux. I don't think so but that doesn't mean its not imposable  just be careful and setup a firewall and antivirus software on windows and a firewall on linux and you should be fine.
Can I get a web site virus for linux like you can on windows? Do you know the website viruses I am talking bout that doesn't need install I think. and also how do I fix my mouse because when you scroll with the wheel up and down it scrolls to much and how do I install my ati radeon 4250 HD onboard and also how is there any way to play maplestory on ubuntu without some virtual machine running windows xp. I  google this and they said wine doesn't work because maplestory hackshield finds wine as a hack program.

---

### Post by iseeu1001 on 2013-01-15
I am starting to hate ubuntu its making my windows 7 slow I don't know why.

---

### Post by speartip on 2013-01-16
> **iseeu1001 said:**
> I am starting to hate ubuntu its making my windows 7 slow I don't know why.

If you have installed Ubuntu correctly, on its own partition, then there is no way it can make windows slow, unless you have cut the Windows partition down so small that it hasn't got room to operate.
I cut my hard disk with Windows 7 on it down to just 100 gig, to allow 900 gig for Linux, & it made no difference to the speed of Windows whatsoever.

As for your virus question. No Ubuntu cannot catch a Windows virus, that is why an Antivirus program is unnecessary.

---

### Post by iseeu1001 on 2013-01-16
> **speartip said:**
> If you have installed Ubuntu correctly, on its own partition, then there is no way it can make windows slow, unless you have cut the Windows partition down so small that it hasn't got room to operate.
I cut my hard disk with Windows 7 on it down to just 100 gig, to allow 900 gig for Linux, & it made no difference to the speed of Windows whatsoever.

As for your virus question. No Ubuntu cannot catch a Windows virus, that is why an Antivirus program is unnecessary.
I have 500GB HD and I made a partition for ubuntu for 200GB and the 233GB for windows 7 so its nothing to do with space I know how to partition a drive.

---

### Post by speartip on 2013-01-16
> **iseeu1001 said:**
> I have 500GB HD and I made a partition for ubuntu for 200GB and the 233GB for windows 7 so its nothing to do with space I know how to partition a drive.

Then your problem lies with your Windows installation.

---

