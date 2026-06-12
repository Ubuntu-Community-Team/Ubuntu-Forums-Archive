---
title: "Can't install Ubuntu with Wubi"
date: 2012-12-09
forum: General Help
---

### Post by Freezing Point on 2012-12-09
Hey everyone,

I'm new to these forums. And I'm trying to install Ubuntu on my Laptop, but I always get this annoying error when it's halfway through extracting, I have tried solutions, and I have assigned a letter to my hidden system drive, I have made my C: drive the online drive, but to no use, I still get the error, it's "error executing command"

I am running Windows 7 home Premium 64 Bit.

Log posted below, help is greatly appreciated. 

> 12-08 20:19 INFO   root: === wubi 12.10 rev273 ===
12-08 20:19 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 20:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Sam\'\\Downloads\\wubi.exe"']
12-08 20:19 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\data
12-08 20:19 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\bin\7z.exe
12-08 20:19 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 20:19 DEBUG  CommonBackend: Fetching basic info...
12-08 20:19 DEBUG  CommonBackend: original_exe=C:\Users\Sam'\Downloads\wubi.exe
12-08 20:19 DEBUG  CommonBackend: platform=win32
12-08 20:19 DEBUG  CommonBackend: osname=nt
12-08 20:19 DEBUG  CommonBackend: language=en_GB
12-08 20:19 DEBUG  CommonBackend: encoding=cp1252
12-08 20:19 DEBUG  WindowsBackend: arch=amd64
12-08 20:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\data\isolist.ini
12-08 20:19 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 20:19 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 20:19 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 20:19 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 20:19 DEBUG  WindowsBackend: Fetching host info...
12-08 20:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 20:19 DEBUG  WindowsBackend: windows version=vista
12-08 20:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 20:19 DEBUG  WindowsBackend: windows_sp=None
12-08 20:19 DEBUG  WindowsBackend: windows_build=7600
12-08 20:19 DEBUG  WindowsBackend: gmt=0
12-08 20:19 DEBUG  WindowsBackend: country=GB
12-08 20:19 DEBUG  WindowsBackend: timezone=Europe/London
12-08 20:19 DEBUG  WindowsBackend: windows_username=Sam'
12-08 20:19 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 20:19 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 20:19 DEBUG  WindowsBackend: windows_language_code=1033
12-08 20:19 DEBUG  WindowsBackend: windows_language=English
12-08 20:19 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 20:19 DEBUG  WindowsBackend: bootloader=vista
12-08 20:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 19713.9960938 mb free ntfs)
12-08 20:19 DEBUG  WindowsBackend: drive=Drive(C: hd 19713.9960938 mb free ntfs)
12-08 20:19 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 20:19 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
12-08 20:19 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 20:19 DEBUG  WindowsBackend: uninstaller_path=None
12-08 20:19 DEBUG  WindowsBackend: previous_target_dir=None
12-08 20:19 DEBUG  WindowsBackend: previous_distro_name=None
12-08 20:19 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 20:19 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 20:19 DEBUG  WindowsBackend: keyboard_variant=
12-08 20:19 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 20:19 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 20:19 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 20:19 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 20:19 DEBUG  CommonBackend: Searching for local CDs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Ubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Ubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Kubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Kubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Mythbuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Mythbuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Edubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Edubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Lubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp is a valid Lubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 20:19 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:19 INFO   root: Running the installer...
12-08 20:19 DEBUG  WindowsFrontend: __init__...
12-08 20:19 DEBUG  WindowsFrontend: on_init...
12-08 20:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\translations, languages=['en_GB', 'en']
12-08 20:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylD71.tmp\translations, languages=['en_GB', 'en']
12-08 20:20 INFO   WindowsFrontend: Operation cancelled
12-08 20:20 DEBUG  WindowsFrontend: frontend.quit
12-08 20:20 DEBUG  WindowsFrontend: frontend.on_quit
12-08 20:20 DEBUG  root: application.on_quit
12-08 20:20 INFO   root: sys.exit
12-08 20:27 INFO   root: === wubi 12.10 rev273 ===
12-08 20:27 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 20:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Sam\'\\Downloads\\wubi.exe"']
12-08 20:27 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\data
12-08 20:27 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\bin\7z.exe
12-08 20:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 20:27 DEBUG  CommonBackend: Fetching basic info...
12-08 20:27 DEBUG  CommonBackend: original_exe=C:\Users\Sam'\Downloads\wubi.exe
12-08 20:27 DEBUG  CommonBackend: platform=win32
12-08 20:27 DEBUG  CommonBackend: osname=nt
12-08 20:27 DEBUG  CommonBackend: language=en_GB
12-08 20:27 DEBUG  CommonBackend: encoding=cp1252
12-08 20:27 DEBUG  WindowsBackend: arch=amd64
12-08 20:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\data\isolist.ini
12-08 20:27 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 20:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 20:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 20:27 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 20:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 20:27 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 20:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 20:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 20:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 20:27 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 20:27 DEBUG  WindowsBackend: Fetching host info...
12-08 20:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 20:27 DEBUG  WindowsBackend: windows version=vista
12-08 20:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 20:27 DEBUG  WindowsBackend: windows_sp=None
12-08 20:27 DEBUG  WindowsBackend: windows_build=7600
12-08 20:27 DEBUG  WindowsBackend: gmt=0
12-08 20:27 DEBUG  WindowsBackend: country=GB
12-08 20:27 DEBUG  WindowsBackend: timezone=Europe/London
12-08 20:27 DEBUG  WindowsBackend: windows_username=Sam'
12-08 20:27 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 20:27 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 20:27 DEBUG  WindowsBackend: windows_language_code=1033
12-08 20:27 DEBUG  WindowsBackend: windows_language=English
12-08 20:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 20:27 DEBUG  WindowsBackend: bootloader=vista
12-08 20:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 19703.671875 mb free ntfs)
12-08 20:27 DEBUG  WindowsBackend: drive=Drive(C: hd 19703.671875 mb free ntfs)
12-08 20:27 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 20:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
12-08 20:27 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 20:27 DEBUG  WindowsBackend: uninstaller_path=None
12-08 20:27 DEBUG  WindowsBackend: previous_target_dir=None
12-08 20:27 DEBUG  WindowsBackend: previous_distro_name=None
12-08 20:27 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 20:27 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 20:27 DEBUG  WindowsBackend: keyboard_variant=
12-08 20:27 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 20:27 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 20:27 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 20:27 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 20:27 DEBUG  CommonBackend: Searching for local CDs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Ubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Ubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Kubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Kubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Mythbuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Mythbuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Edubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Edubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Lubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Lubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 20:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:27 INFO   root: Running the installer...
12-08 20:27 DEBUG  WindowsFrontend: __init__...
12-08 20:27 DEBUG  WindowsFrontend: on_init...
12-08 20:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\translations, languages=['en_GB', 'en']
12-08 20:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\translations, languages=['en_GB', 'en']
12-08 20:29 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=10000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=sam
12-08 20:29 INFO   root: Received settings
12-08 20:29 DEBUG  CommonBackend: Searching for local CD
12-08 20:29 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp is a valid Ubuntu CD
12-08 20:29 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\casper\filesystem.squashfs
12-08 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 20:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 20:29 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 20:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 20:29 DEBUG  CommonBackend: Searching for local ISO
12-08 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\translations, languages=['en_GB', 'en']
12-08 20:29 DEBUG  TaskList: # Running tasklist...
12-08 20:29 DEBUG  TaskList: ## Running select_target_dir...
12-08 20:29 INFO   WindowsBackend: Installing into D:\ubuntu
12-08 20:29 DEBUG  TaskList: ## Finished select_target_dir
12-08 20:29 DEBUG  TaskList: ## Running create_dir_structure...
12-08 20:29 DEBUG  CommonBackend: Creating dir D:\ubuntu
12-08 20:29 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
12-08 20:29 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
12-08 20:29 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
12-08 20:29 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
12-08 20:29 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
12-08 20:29 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
12-08 20:29 DEBUG  TaskList: ## Finished create_dir_structure
12-08 20:29 DEBUG  TaskList: ## Running create_uninstaller...
12-08 20:29 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Sam'\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
12-08 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
12-08 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
12-08 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-08 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
12-08 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
12-08 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-08 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-08 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-08 20:29 DEBUG  TaskList: ## Finished create_uninstaller
12-08 20:29 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-08 20:29 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-08 20:29 DEBUG  TaskList: ## Running get_diskimage...
12-08 20:29 DEBUG  TaskList: New task download
12-08 20:29 DEBUG  TaskList: ### Running download...
12-08 20:29 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
12-08 20:29 DEBUG  downloader: Download start filename=D:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
12-08 20:37 DEBUG  TaskList: ### Finished download
12-08 20:37 DEBUG  downloader: download finished (read 562061340 bytes)
12-08 20:37 DEBUG  TaskList: ## Finished get_diskimage
12-08 20:37 DEBUG  TaskList: ## Running extract_diskimage...
12-08 20:38 DEBUG  TaskList: ## Finished extract_diskimage
12-08 20:38 DEBUG  TaskList: ## Running choose_disk_sizes...
12-08 20:38 DEBUG  WindowsBackend: total size=10000
  root=9744
  swap=256
  home=0
  usr=0
12-08 20:38 DEBUG  TaskList: ## Finished choose_disk_sizes
12-08 20:38 DEBUG  TaskList: ## Running expand_diskimage...
12-08 20:38 ERROR  TaskList: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pyl69F2.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pyl69F2.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-08 20:38 DEBUG  TaskList: # Cancelling tasklist
12-08 20:38 DEBUG  TaskList: # Finished tasklist
12-08 20:38 ERROR  root: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pyl69F2.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pyl69F2.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pyl69F2.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-08 21:05 INFO   root: === wubi 12.10 rev273 ===
12-08 21:05 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 21:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Sam\'\\Downloads\\wubi.exe"']
12-08 21:05 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\data
12-08 21:05 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\bin\7z.exe
12-08 21:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 21:05 DEBUG  CommonBackend: Fetching basic info...
12-08 21:05 DEBUG  CommonBackend: original_exe=C:\Users\Sam'\Downloads\wubi.exe
12-08 21:05 DEBUG  CommonBackend: platform=win32
12-08 21:05 DEBUG  CommonBackend: osname=nt
12-08 21:05 DEBUG  CommonBackend: language=en_GB
12-08 21:05 DEBUG  CommonBackend: encoding=cp1252
12-08 21:05 DEBUG  WindowsBackend: arch=amd64
12-08 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\data\isolist.ini
12-08 21:05 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 21:05 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 21:05 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 21:05 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 21:05 DEBUG  WindowsBackend: Fetching host info...
12-08 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 21:05 DEBUG  WindowsBackend: windows version=vista
12-08 21:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 21:05 DEBUG  WindowsBackend: windows_sp=None
12-08 21:05 DEBUG  WindowsBackend: windows_build=7600
12-08 21:05 DEBUG  WindowsBackend: gmt=0
12-08 21:05 DEBUG  WindowsBackend: country=GB
12-08 21:05 DEBUG  WindowsBackend: timezone=Europe/London
12-08 21:05 DEBUG  WindowsBackend: windows_username=Sam'
12-08 21:05 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 21:05 DEBUG  WindowsBackend: windows_language_code=1033
12-08 21:05 DEBUG  WindowsBackend: windows_language=English
12-08 21:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 21:05 DEBUG  WindowsBackend: bootloader=vista
12-08 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 39793.21875 mb free ntfs)
12-08 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 39793.21875 mb free ntfs)
12-08 21:05 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 21:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
12-08 21:05 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 21:05 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-08 21:05 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-08 21:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-08 21:05 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 21:05 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 21:05 DEBUG  WindowsBackend: keyboard_variant=
12-08 21:05 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 21:05 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 21:05 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 21:05 DEBUG  CommonBackend: Searching for local CDs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Ubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Ubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Kubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Kubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Mythbuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Mythbuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Edubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Edubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Lubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Lubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:05 INFO   root: Running the installer...
12-08 21:05 DEBUG  WindowsFrontend: __init__...
12-08 21:05 DEBUG  WindowsFrontend: on_init...
12-08 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\translations, languages=['en_GB', 'en']
12-08 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\translations, languages=['en_GB', 'en']
12-08 21:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=sam
12-08 21:06 INFO   root: Received settings
12-08 21:06 DEBUG  CommonBackend: Searching for local CD
12-08 21:06 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp is a valid Ubuntu CD
12-08 21:06 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\casper\filesystem.squashfs
12-08 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:06 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:06 DEBUG  CommonBackend: Searching for local ISO
12-08 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\translations, languages=['en_GB', 'en']
12-08 21:06 DEBUG  TaskList: # Running tasklist...
12-08 21:06 DEBUG  TaskList: ## Running select_target_dir...
12-08 21:06 INFO   WindowsBackend: Installing into C:\ubuntu
12-08 21:06 DEBUG  TaskList: ## Finished select_target_dir
12-08 21:06 DEBUG  TaskList: ## Running create_dir_structure...
12-08 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-08 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-08 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-08 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-08 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-08 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-08 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-08 21:06 DEBUG  TaskList: ## Finished create_dir_structure
12-08 21:06 DEBUG  TaskList: ## Running create_uninstaller...
12-08 21:06 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Sam'\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-08 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-08 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-08 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-08 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-08 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
12-08 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-08 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-08 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-08 21:06 DEBUG  TaskList: ## Finished create_uninstaller
12-08 21:06 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-08 21:06 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-08 21:06 DEBUG  TaskList: ## Running get_diskimage...
12-08 21:06 DEBUG  TaskList: New task download
12-08 21:06 DEBUG  TaskList: ### Running download...
12-08 21:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
12-08 21:06 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
12-08 21:13 DEBUG  TaskList: ### Finished download
12-08 21:13 DEBUG  downloader: download finished (read 562061340 bytes)
12-08 21:13 DEBUG  TaskList: ## Finished get_diskimage
12-08 21:13 DEBUG  TaskList: ## Running extract_diskimage...
12-08 21:18 DEBUG  TaskList: ## Finished extract_diskimage
12-08 21:18 DEBUG  TaskList: ## Running choose_disk_sizes...
12-08 21:18 DEBUG  WindowsBackend: total size=15000
  root=14744
  swap=256
  home=0
  usr=0
12-08 21:18 DEBUG  TaskList: ## Finished choose_disk_sizes
12-08 21:18 DEBUG  TaskList: ## Running expand_diskimage...
12-08 21:18 ERROR  TaskList: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 14744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylCA1C.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 14744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 14744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylCA1C.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 14744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-08 21:18 DEBUG  TaskList: # Cancelling tasklist
12-08 21:18 DEBUG  TaskList: # Finished tasklist
12-08 21:18 ERROR  root: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 14744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylCA1C.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 14744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylCA1C.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 14744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylCA1C.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 14744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-08 21:31 INFO   root: === wubi 12.10 rev273 ===
12-08 21:31 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 21:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-08 21:31 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\data
12-08 21:31 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\bin\7z.exe
12-08 21:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 21:31 DEBUG  CommonBackend: Fetching basic info...
12-08 21:31 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-08 21:31 DEBUG  CommonBackend: platform=win32
12-08 21:31 DEBUG  CommonBackend: osname=nt
12-08 21:31 DEBUG  CommonBackend: language=en_GB
12-08 21:31 DEBUG  CommonBackend: encoding=cp1252
12-08 21:31 DEBUG  WindowsBackend: arch=amd64
12-08 21:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\data\isolist.ini
12-08 21:31 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 21:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 21:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 21:31 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 21:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 21:31 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 21:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 21:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 21:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 21:31 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 21:31 DEBUG  WindowsBackend: Fetching host info...
12-08 21:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 21:31 DEBUG  WindowsBackend: windows version=vista
12-08 21:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 21:31 DEBUG  WindowsBackend: windows_sp=None
12-08 21:31 DEBUG  WindowsBackend: windows_build=7600
12-08 21:31 DEBUG  WindowsBackend: gmt=0
12-08 21:31 DEBUG  WindowsBackend: country=GB
12-08 21:31 DEBUG  WindowsBackend: timezone=Europe/London
12-08 21:31 DEBUG  WindowsBackend: windows_username=Sam'
12-08 21:31 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 21:31 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 21:31 DEBUG  WindowsBackend: windows_language_code=1033
12-08 21:31 DEBUG  WindowsBackend: windows_language=English
12-08 21:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 21:31 DEBUG  WindowsBackend: bootloader=vista
12-08 21:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38838.9648438 mb free ntfs)
12-08 21:31 DEBUG  WindowsBackend: drive=Drive(C: hd 38838.9648438 mb free ntfs)
12-08 21:31 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 21:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
12-08 21:31 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 21:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-08 21:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-08 21:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-08 21:31 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 21:31 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 21:31 DEBUG  WindowsBackend: keyboard_variant=
12-08 21:31 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 21:31 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 21:31 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 21:31 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 21:31 DEBUG  CommonBackend: Searching for local CDs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Ubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Ubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Kubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Kubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Mythbuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Mythbuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Edubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Edubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Lubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp is a valid Lubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:31 INFO   root: Running the uninstaller...
12-08 21:31 INFO   CommonBackend: This is the uninstaller running
12-08 21:31 DEBUG  WindowsFrontend: __init__...
12-08 21:31 DEBUG  WindowsFrontend: on_init...
12-08 21:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\translations, languages=['en_GB', 'en']
12-08 21:32 INFO   root: Received settings
12-08 21:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\translations, languages=['en_GB', 'en']
12-08 21:32 DEBUG  TaskList: # Running tasklist...
12-08 21:32 DEBUG  TaskList: ## Running Remove bootloader entry....
12-08 21:32 DEBUG  WindowsBackend: Could not find bcd id
12-08 21:32 DEBUG  WindowsBackend: undo_bootini C:
12-08 21:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 38838.9648438 mb free ntfs)
12-08 21:32 DEBUG  WindowsBackend: undo_bootini D:
12-08 21:32 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 143884.40625 mb free ntfs)
12-08 21:32 DEBUG  WindowsBackend: undo_bootini Q:
12-08 21:32 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-08 21:32 DEBUG  TaskList: ## Finished Remove bootloader entry.
12-08 21:32 DEBUG  TaskList: ## Running Remove target dir....
12-08 21:32 DEBUG  CommonBackend: Deleting C:\ubuntu
12-08 21:32 DEBUG  TaskList: ## Finished Remove target dir.
12-08 21:32 DEBUG  TaskList: ## Running Remove registry key....
12-08 21:32 DEBUG  TaskList: ## Finished Remove registry key.
12-08 21:32 DEBUG  TaskList: # Finished tasklist
12-08 21:32 INFO   root: Almost finished uninstalling
12-08 21:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylD93E.tmp\translations, languages=['en_GB', 'en']
12-08 21:32 INFO   root: Finished uninstallation
12-08 21:32 DEBUG  root: application.quit
12-08 21:32 DEBUG  WindowsFrontend: frontend.quit
12-08 21:32 DEBUG  WindowsFrontend: frontend.on_quit
12-08 21:32 DEBUG  root: application.on_quit
12-08 21:32 INFO   root: sys.exit
12-08 21:40 INFO   root: === wubi 12.10 rev273 ===
12-08 21:40 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 21:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Sam\'\\Downloads\\wubi.exe"']
12-08 21:40 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\data
12-08 21:40 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\bin\7z.exe
12-08 21:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 21:40 DEBUG  CommonBackend: Fetching basic info...
12-08 21:40 DEBUG  CommonBackend: original_exe=C:\Users\Sam'\Downloads\wubi.exe
12-08 21:40 DEBUG  CommonBackend: platform=win32
12-08 21:40 DEBUG  CommonBackend: osname=nt
12-08 21:40 DEBUG  CommonBackend: language=en_GB
12-08 21:40 DEBUG  CommonBackend: encoding=cp1252
12-08 21:40 DEBUG  WindowsBackend: arch=amd64
12-08 21:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\data\isolist.ini
12-08 21:40 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 21:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 21:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 21:40 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 21:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 21:40 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 21:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 21:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 21:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 21:40 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 21:40 DEBUG  WindowsBackend: Fetching host info...
12-08 21:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 21:40 DEBUG  WindowsBackend: windows version=vista
12-08 21:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 21:40 DEBUG  WindowsBackend: windows_sp=None
12-08 21:40 DEBUG  WindowsBackend: windows_build=7600
12-08 21:40 DEBUG  WindowsBackend: gmt=0
12-08 21:40 DEBUG  WindowsBackend: country=GB
12-08 21:40 DEBUG  WindowsBackend: timezone=Europe/London
12-08 21:40 DEBUG  WindowsBackend: windows_username=Sam'
12-08 21:40 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 21:40 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 21:40 DEBUG  WindowsBackend: windows_language_code=1033
12-08 21:40 DEBUG  WindowsBackend: windows_language=English
12-08 21:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 21:40 DEBUG  WindowsBackend: bootloader=vista
12-08 21:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 41306.6132813 mb free ntfs)
12-08 21:40 DEBUG  WindowsBackend: drive=Drive(C: hd 41306.6132813 mb free ntfs)
12-08 21:40 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 21:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-08 21:40 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 21:40 DEBUG  WindowsBackend: uninstaller_path=None
12-08 21:40 DEBUG  WindowsBackend: previous_target_dir=None
12-08 21:40 DEBUG  WindowsBackend: previous_distro_name=None
12-08 21:40 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 21:40 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 21:40 DEBUG  WindowsBackend: keyboard_variant=
12-08 21:40 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 21:40 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 21:40 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 21:40 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 21:40 DEBUG  CommonBackend: Searching for local CDs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Kubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Kubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Mythbuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Mythbuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Edubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Edubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Lubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Lubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 INFO   root: Running the installer...
12-08 21:40 DEBUG  WindowsFrontend: __init__...
12-08 21:40 DEBUG  WindowsFrontend: on_init...
12-08 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\translations, languages=['en_GB', 'en']
12-08 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\translations, languages=['en_GB', 'en']
12-08 21:40 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=sam
12-08 21:40 INFO   root: Received settings
12-08 21:40 DEBUG  CommonBackend: Searching for local CD
12-08 21:40 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:40 DEBUG  CommonBackend: Searching for local ISO
12-08 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\translations, languages=['en_GB', 'en']
12-08 21:40 DEBUG  TaskList: # Running tasklist...
12-08 21:40 DEBUG  TaskList: ## Running select_target_dir...
12-08 21:40 INFO   WindowsBackend: Installing into C:\ubuntu
12-08 21:40 DEBUG  TaskList: ## Finished select_target_dir
12-08 21:40 DEBUG  TaskList: ## Running create_dir_structure...
12-08 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-08 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-08 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-08 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-08 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-08 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-08 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-08 21:40 DEBUG  TaskList: ## Finished create_dir_structure
12-08 21:40 DEBUG  TaskList: ## Running create_uninstaller...
12-08 21:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Sam'\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-08 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-08 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-08 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-08 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-08 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
12-08 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-08 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-08 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-08 21:40 DEBUG  TaskList: ## Finished create_uninstaller
12-08 21:40 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-08 21:40 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-08 21:40 DEBUG  TaskList: ## Running get_diskimage...
12-08 21:40 DEBUG  TaskList: New task download
12-08 21:40 DEBUG  TaskList: ### Running download...
12-08 21:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
12-08 21:40 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
12-08 21:44 DEBUG  TaskList: ### Finished download
12-08 21:44 DEBUG  downloader: download finished (read 562061340 bytes)
12-08 21:44 DEBUG  TaskList: ## Finished get_diskimage
12-08 21:44 DEBUG  TaskList: ## Running extract_diskimage...
12-08 21:48 DEBUG  TaskList: ## Finished extract_diskimage
12-08 21:48 DEBUG  TaskList: ## Running choose_disk_sizes...
12-08 21:48 DEBUG  WindowsBackend: total size=10000
  root=9744
  swap=256
  home=0
  usr=0
12-08 21:48 DEBUG  TaskList: ## Finished choose_disk_sizes
12-08 21:48 DEBUG  TaskList: ## Running expand_diskimage...
12-08 21:48 ERROR  TaskList: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pyl3C63.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pyl3C63.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-08 21:48 DEBUG  TaskList: # Cancelling tasklist
12-08 21:48 ERROR  root: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pyl3C63.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pyl3C63.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pyl3C63.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-08 21:48 DEBUG  TaskList: # Finished tasklist
12-08 21:49 INFO   root: === wubi 12.10 rev273 ===
12-08 21:49 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 21:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
12-08 21:49 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\data
12-08 21:49 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\bin\7z.exe
12-08 21:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 21:49 DEBUG  CommonBackend: Fetching basic info...
12-08 21:49 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-08 21:49 DEBUG  CommonBackend: platform=win32
12-08 21:49 DEBUG  CommonBackend: osname=nt
12-08 21:49 DEBUG  CommonBackend: language=en_GB
12-08 21:49 DEBUG  CommonBackend: encoding=cp1252
12-08 21:49 DEBUG  WindowsBackend: arch=amd64
12-08 21:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\data\isolist.ini
12-08 21:49 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 21:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 21:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 21:49 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 21:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 21:49 DEBUG  WindowsBackend: Fetching host info...
12-08 21:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 21:49 DEBUG  WindowsBackend: windows version=vista
12-08 21:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 21:49 DEBUG  WindowsBackend: windows_sp=None
12-08 21:49 DEBUG  WindowsBackend: windows_build=7600
12-08 21:49 DEBUG  WindowsBackend: gmt=0
12-08 21:49 DEBUG  WindowsBackend: country=GB
12-08 21:49 DEBUG  WindowsBackend: timezone=Europe/London
12-08 21:49 DEBUG  WindowsBackend: windows_username=Sam'
12-08 21:49 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 21:49 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 21:49 DEBUG  WindowsBackend: windows_language_code=1033
12-08 21:49 DEBUG  WindowsBackend: windows_language=English
12-08 21:49 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 21:49 DEBUG  WindowsBackend: bootloader=vista
12-08 21:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38566.4492188 mb free ntfs)
12-08 21:49 DEBUG  WindowsBackend: drive=Drive(C: hd 38566.4492188 mb free ntfs)
12-08 21:49 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 21:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-08 21:49 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 21:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-08 21:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-08 21:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-08 21:49 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 21:49 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 21:49 DEBUG  WindowsBackend: keyboard_variant=
12-08 21:49 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 21:49 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 21:49 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 21:49 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 21:49 DEBUG  CommonBackend: Searching for local CDs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 INFO   root: Running the uninstaller...
12-08 21:49 INFO   CommonBackend: This is the uninstaller running
12-08 21:49 DEBUG  WindowsFrontend: __init__...
12-08 21:49 DEBUG  WindowsFrontend: on_init...
12-08 21:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\translations, languages=['en_GB', 'en']
12-08 21:49 INFO   root: === wubi 12.10 rev273 ===
12-08 21:49 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 21:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
12-08 21:49 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\data
12-08 21:49 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\bin\7z.exe
12-08 21:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 21:49 DEBUG  CommonBackend: Fetching basic info...
12-08 21:49 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-08 21:49 DEBUG  CommonBackend: platform=win32
12-08 21:49 DEBUG  CommonBackend: osname=nt
12-08 21:49 DEBUG  CommonBackend: language=en_GB
12-08 21:49 DEBUG  CommonBackend: encoding=cp1252
12-08 21:49 DEBUG  WindowsBackend: arch=amd64
12-08 21:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\data\isolist.ini
12-08 21:49 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 21:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 21:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 21:49 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 21:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 21:49 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 21:49 DEBUG  WindowsBackend: Fetching host info...
12-08 21:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 21:49 DEBUG  WindowsBackend: windows version=vista
12-08 21:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 21:49 DEBUG  WindowsBackend: windows_sp=None
12-08 21:49 DEBUG  WindowsBackend: windows_build=7600
12-08 21:49 DEBUG  WindowsBackend: gmt=0
12-08 21:49 DEBUG  WindowsBackend: country=GB
12-08 21:49 DEBUG  WindowsBackend: timezone=Europe/London
12-08 21:49 DEBUG  WindowsBackend: windows_username=Sam'
12-08 21:49 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 21:49 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 21:49 DEBUG  WindowsBackend: windows_language_code=1033
12-08 21:49 DEBUG  WindowsBackend: windows_language=English
12-08 21:49 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 21:49 DEBUG  WindowsBackend: bootloader=vista
12-08 21:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38547.9101563 mb free ntfs)
12-08 21:49 DEBUG  WindowsBackend: drive=Drive(C: hd 38547.9101563 mb free ntfs)
12-08 21:49 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 21:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-08 21:49 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 21:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-08 21:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-08 21:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-08 21:49 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 21:49 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 21:49 DEBUG  WindowsBackend: keyboard_variant=
12-08 21:49 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 21:49 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 21:49 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 21:49 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 21:49 DEBUG  CommonBackend: Searching for local CDs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:49 INFO   root: Received settings
12-08 21:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\translations, languages=['en_GB', 'en']
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  TaskList: # Running tasklist...
12-08 21:49 DEBUG  TaskList: ## Running Remove bootloader entry....
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  WindowsBackend: Could not find bcd id
12-08 21:49 DEBUG  WindowsBackend: undo_bootini C:
12-08 21:49 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 38566.4492188 mb free ntfs)
12-08 21:49 DEBUG  WindowsBackend: undo_bootini D:
12-08 21:49 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 143884.40625 mb free ntfs)
12-08 21:49 DEBUG  WindowsBackend: undo_bootini Q:
12-08 21:49 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-08 21:49 DEBUG  TaskList: ## Finished Remove bootloader entry.
12-08 21:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  TaskList: ## Running Remove target dir....
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 21:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 21:49 INFO   root: Running the uninstaller...
12-08 21:49 DEBUG  CommonBackend: Deleting C:\ubuntu
12-08 21:49 INFO   CommonBackend: This is the uninstaller running
12-08 21:49 DEBUG  WindowsFrontend: __init__...
12-08 21:49 DEBUG  WindowsFrontend: on_init...
12-08 21:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl20B9.tmp\translations, languages=['en_GB', 'en']
12-08 21:50 DEBUG  TaskList: ## Finished Remove target dir.
12-08 21:50 DEBUG  TaskList: ## Running Remove registry key....
12-08 21:50 DEBUG  TaskList: ## Finished Remove registry key.
12-08 21:50 DEBUG  TaskList: # Finished tasklist
12-08 21:50 INFO   root: Almost finished uninstalling
12-08 21:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylBB91.tmp\translations, languages=['en_GB', 'en']
12-08 21:50 DEBUG  WindowsFrontend: frontend.on_quit
12-08 21:50 DEBUG  root: application.on_quit
12-08 21:50 INFO   root: sys.exit
12-08 21:50 INFO   root: Finished uninstallation
12-08 21:50 DEBUG  root: application.quit
12-08 21:50 DEBUG  WindowsFrontend: frontend.quit
12-08 21:50 DEBUG  WindowsFrontend: frontend.on_quit
12-08 21:50 DEBUG  root: application.on_quit
12-08 21:50 INFO   root: sys.exit
12-08 22:15 INFO   root: === wubi 12.10 rev273 ===
12-08 22:15 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 22:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Sam\'\\Downloads\\wubi.exe"']
12-08 22:15 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\data
12-08 22:15 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\bin\7z.exe
12-08 22:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 22:15 DEBUG  CommonBackend: Fetching basic info...
12-08 22:15 DEBUG  CommonBackend: original_exe=C:\Users\Sam'\Downloads\wubi.exe
12-08 22:15 DEBUG  CommonBackend: platform=win32
12-08 22:15 DEBUG  CommonBackend: osname=nt
12-08 22:15 DEBUG  CommonBackend: language=en_GB
12-08 22:15 DEBUG  CommonBackend: encoding=cp1252
12-08 22:15 DEBUG  WindowsBackend: arch=amd64
12-08 22:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\data\isolist.ini
12-08 22:15 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 22:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 22:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 22:15 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 22:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 22:15 DEBUG  WindowsBackend: Fetching host info...
12-08 22:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 22:15 DEBUG  WindowsBackend: windows version=vista
12-08 22:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 22:15 DEBUG  WindowsBackend: windows_sp=None
12-08 22:15 DEBUG  WindowsBackend: windows_build=7600
12-08 22:15 DEBUG  WindowsBackend: gmt=0
12-08 22:15 DEBUG  WindowsBackend: country=GB
12-08 22:15 DEBUG  WindowsBackend: timezone=Europe/London
12-08 22:15 DEBUG  WindowsBackend: windows_username=Sam'
12-08 22:15 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 22:15 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 22:15 DEBUG  WindowsBackend: windows_language_code=1033
12-08 22:15 DEBUG  WindowsBackend: windows_language=English
12-08 22:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 22:15 DEBUG  WindowsBackend: bootloader=vista
12-08 22:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 37393.3164063 mb free ntfs)
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(C: hd 37393.3164063 mb free ntfs)
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(F: hd 188.58203125 mb free ntfs)
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 22:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-08 22:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-08 22:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-08 22:15 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 22:15 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 22:15 DEBUG  WindowsBackend: keyboard_variant=
12-08 22:15 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 22:15 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 22:15 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 22:15 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 22:15 DEBUG  CommonBackend: Searching for local CDs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4CC9.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 INFO   root: Already installed, running the uninstaller...
12-08 22:15 INFO   root: Running the uninstaller...
12-08 22:15 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
12-08 22:15 DEBUG  root: application.quit
12-08 22:15 DEBUG  root: application.on_quit
12-08 22:15 INFO   root: sys.exit
12-08 22:15 INFO   root: Quitting application
12-08 22:15 INFO   root: === wubi 12.10 rev273 ===
12-08 22:15 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 22:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Sam\'\\Downloads\\wubi.exe"']
12-08 22:15 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\data
12-08 22:15 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\bin\7z.exe
12-08 22:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 22:15 DEBUG  CommonBackend: Fetching basic info...
12-08 22:15 DEBUG  CommonBackend: original_exe=C:\Users\Sam'\Downloads\wubi.exe
12-08 22:15 DEBUG  CommonBackend: platform=win32
12-08 22:15 DEBUG  CommonBackend: osname=nt
12-08 22:15 DEBUG  CommonBackend: language=en_GB
12-08 22:15 DEBUG  CommonBackend: encoding=cp1252
12-08 22:15 DEBUG  WindowsBackend: arch=amd64
12-08 22:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\data\isolist.ini
12-08 22:15 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 22:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 22:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 22:15 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 22:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 22:15 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 22:15 DEBUG  WindowsBackend: Fetching host info...
12-08 22:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 22:15 DEBUG  WindowsBackend: windows version=vista
12-08 22:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 22:15 DEBUG  WindowsBackend: windows_sp=None
12-08 22:15 DEBUG  WindowsBackend: windows_build=7600
12-08 22:15 DEBUG  WindowsBackend: gmt=0
12-08 22:15 DEBUG  WindowsBackend: country=GB
12-08 22:15 DEBUG  WindowsBackend: timezone=Europe/London
12-08 22:15 DEBUG  WindowsBackend: windows_username=Sam'
12-08 22:15 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 22:15 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 22:15 DEBUG  WindowsBackend: windows_language_code=1033
12-08 22:15 DEBUG  WindowsBackend: windows_language=English
12-08 22:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 22:15 DEBUG  WindowsBackend: bootloader=vista
12-08 22:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 39630.2851563 mb free ntfs)
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(C: hd 39630.2851563 mb free ntfs)
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(F: hd 188.58203125 mb free ntfs)
12-08 22:15 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 22:15 DEBUG  WindowsBackend: uninstaller_path=None
12-08 22:15 DEBUG  WindowsBackend: previous_target_dir=None
12-08 22:15 DEBUG  WindowsBackend: previous_distro_name=None
12-08 22:15 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 22:15 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 22:15 DEBUG  WindowsBackend: keyboard_variant=
12-08 22:15 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 22:15 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 22:15 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 22:15 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 22:15 DEBUG  CommonBackend: Searching for local CDs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 22:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:15 INFO   root: Running the installer...
12-08 22:15 DEBUG  WindowsFrontend: __init__...
12-08 22:15 DEBUG  WindowsFrontend: on_init...
12-08 22:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\translations, languages=['en_GB', 'en']
12-08 22:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\translations, languages=['en_GB', 'en']
12-08 22:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=sam
12-08 22:16 INFO   root: Received settings
12-08 22:16 DEBUG  CommonBackend: Searching for local CD
12-08 22:16 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp is a valid Ubuntu CD
12-08 22:16 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\casper\filesystem.squashfs
12-08 22:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-08 22:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:16 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 22:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:16 DEBUG  CommonBackend: Searching for local ISO
12-08 22:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\translations, languages=['en_GB', 'en']
12-08 22:16 DEBUG  TaskList: # Running tasklist...
12-08 22:16 DEBUG  TaskList: ## Running select_target_dir...
12-08 22:16 INFO   WindowsBackend: Installing into C:\ubuntu
12-08 22:16 DEBUG  TaskList: ## Finished select_target_dir
12-08 22:16 DEBUG  TaskList: ## Running create_dir_structure...
12-08 22:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-08 22:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-08 22:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-08 22:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-08 22:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-08 22:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-08 22:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-08 22:16 DEBUG  TaskList: ## Finished create_dir_structure
12-08 22:16 DEBUG  TaskList: ## Running create_uninstaller...
12-08 22:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Sam'\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-08 22:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-08 22:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-08 22:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-08 22:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-08 22:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
12-08 22:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-08 22:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-08 22:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-08 22:16 DEBUG  TaskList: ## Finished create_uninstaller
12-08 22:16 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-08 22:16 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-08 22:16 DEBUG  TaskList: ## Running get_diskimage...
12-08 22:16 DEBUG  TaskList: New task download
12-08 22:16 DEBUG  TaskList: ### Running download...
12-08 22:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
12-08 22:16 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
12-08 22:21 DEBUG  TaskList: ### Finished download
12-08 22:21 DEBUG  downloader: download finished (read 562061340 bytes)
12-08 22:21 DEBUG  TaskList: ## Finished get_diskimage
12-08 22:21 DEBUG  TaskList: ## Running extract_diskimage...
12-08 22:24 DEBUG  TaskList: ## Finished extract_diskimage
12-08 22:24 DEBUG  TaskList: ## Running choose_disk_sizes...
12-08 22:24 DEBUG  WindowsBackend: total size=10000
  root=9744
  swap=256
  home=0
  usr=0
12-08 22:24 DEBUG  TaskList: ## Finished choose_disk_sizes
12-08 22:24 DEBUG  TaskList: ## Running expand_diskimage...
12-08 22:24 ERROR  TaskList: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylD50A.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylD50A.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-08 22:24 DEBUG  TaskList: # Cancelling tasklist
12-08 22:24 DEBUG  TaskList: # Finished tasklist
12-08 22:24 ERROR  root: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylD50A.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylD50A.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 9744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylD50A.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 9744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-08 22:28 INFO   root: === wubi 12.10 rev273 ===
12-08 22:28 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-08 22:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-08 22:28 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\data
12-08 22:28 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\bin\7z.exe
12-08 22:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-08 22:28 DEBUG  CommonBackend: Fetching basic info...
12-08 22:28 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-08 22:28 DEBUG  CommonBackend: platform=win32
12-08 22:28 DEBUG  CommonBackend: osname=nt
12-08 22:28 DEBUG  CommonBackend: language=en_GB
12-08 22:28 DEBUG  CommonBackend: encoding=cp1252
12-08 22:28 DEBUG  WindowsBackend: arch=amd64
12-08 22:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\data\isolist.ini
12-08 22:28 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-08 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-08 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-08 22:28 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-08 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-08 22:28 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-08 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-08 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-08 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-08 22:28 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-08 22:28 DEBUG  WindowsBackend: Fetching host info...
12-08 22:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-08 22:28 DEBUG  WindowsBackend: windows version=vista
12-08 22:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-08 22:28 DEBUG  WindowsBackend: windows_sp=None
12-08 22:28 DEBUG  WindowsBackend: windows_build=7600
12-08 22:28 DEBUG  WindowsBackend: gmt=0
12-08 22:28 DEBUG  WindowsBackend: country=GB
12-08 22:28 DEBUG  WindowsBackend: timezone=Europe/London
12-08 22:28 DEBUG  WindowsBackend: windows_username=Sam'
12-08 22:28 DEBUG  WindowsBackend: user_full_name=Sam'
12-08 22:28 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-08 22:28 DEBUG  WindowsBackend: windows_language_code=1033
12-08 22:28 DEBUG  WindowsBackend: windows_language=English
12-08 22:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-08 22:28 DEBUG  WindowsBackend: bootloader=vista
12-08 22:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 36875.21875 mb free ntfs)
12-08 22:28 DEBUG  WindowsBackend: drive=Drive(C: hd 36875.21875 mb free ntfs)
12-08 22:28 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-08 22:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-08 22:28 DEBUG  WindowsBackend: drive=Drive(F: hd 188.58203125 mb free ntfs)
12-08 22:28 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-08 22:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-08 22:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-08 22:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-08 22:28 DEBUG  WindowsBackend: keyboard_id=134809609
12-08 22:28 DEBUG  WindowsBackend: keyboard_layout=gb
12-08 22:28 DEBUG  WindowsBackend: keyboard_variant=
12-08 22:28 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-08 22:28 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-08 22:28 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-08 22:28 DEBUG  CommonBackend: Searching ISOs on USB devices
12-08 22:28 DEBUG  CommonBackend: Searching for local CDs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-08 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-08 22:28 INFO   root: Running the uninstaller...
12-08 22:28 INFO   CommonBackend: This is the uninstaller running
12-08 22:28 DEBUG  WindowsFrontend: __init__...
12-08 22:28 DEBUG  WindowsFrontend: on_init...
12-08 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\translations, languages=['en_GB', 'en']
12-08 22:28 INFO   root: Received settings
12-08 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\translations, languages=['en_GB', 'en']
12-08 22:28 DEBUG  TaskList: # Running tasklist...
12-08 22:28 DEBUG  TaskList: ## Running Remove bootloader entry....
12-08 22:28 DEBUG  WindowsBackend: Could not find bcd id
12-08 22:28 DEBUG  WindowsBackend: undo_bootini C:
12-08 22:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 36875.21875 mb free ntfs)
12-08 22:28 DEBUG  WindowsBackend: undo_bootini D:
12-08 22:28 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 143884.40625 mb free ntfs)
12-08 22:28 DEBUG  WindowsBackend: undo_bootini F:
12-08 22:28 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 188.58203125 mb free ntfs)
12-08 22:28 DEBUG  WindowsBackend: undo_bootini Q:
12-08 22:28 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-08 22:28 DEBUG  TaskList: ## Finished Remove bootloader entry.
12-08 22:28 DEBUG  TaskList: ## Running Remove target dir....
12-08 22:28 DEBUG  CommonBackend: Deleting C:\ubuntu
12-08 22:28 DEBUG  TaskList: ## Finished Remove target dir.
12-08 22:28 DEBUG  TaskList: ## Running Remove registry key....
12-08 22:28 DEBUG  TaskList: ## Finished Remove registry key.
12-08 22:28 DEBUG  TaskList: # Finished tasklist
12-08 22:28 INFO   root: Almost finished uninstalling
12-08 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pyl4328.tmp\translations, languages=['en_GB', 'en']
12-08 22:28 INFO   root: Finished uninstallation
12-08 22:28 DEBUG  root: application.quit
12-08 22:28 DEBUG  WindowsFrontend: frontend.quit
12-08 22:28 DEBUG  WindowsFrontend: frontend.on_quit
12-08 22:28 DEBUG  root: application.on_quit
12-08 22:28 INFO   root: sys.exit
12-09 17:07 INFO   root: === wubi 12.10 rev273 ===
12-09 17:07 DEBUG  root: Logfile is c:\users\sam'\appdata\local\temp\wubi-12.10-rev273.log
12-09 17:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Sam\'\\Downloads\\wubi.exe"']
12-09 17:07 DEBUG  CommonBackend: data_dir=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\data
12-09 17:07 DEBUG  WindowsBackend: 7z=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\bin\7z.exe
12-09 17:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 17:07 DEBUG  CommonBackend: Fetching basic info...
12-09 17:07 DEBUG  CommonBackend: original_exe=C:\Users\Sam'\Downloads\wubi.exe
12-09 17:07 DEBUG  CommonBackend: platform=win32
12-09 17:07 DEBUG  CommonBackend: osname=nt
12-09 17:07 DEBUG  CommonBackend: language=en_GB
12-09 17:07 DEBUG  CommonBackend: encoding=cp1252
12-09 17:07 DEBUG  WindowsBackend: arch=amd64
12-09 17:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\data\isolist.ini
12-09 17:07 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-09 17:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 17:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 17:07 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-09 17:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 17:07 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-09 17:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 17:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 17:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 17:07 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-09 17:07 DEBUG  WindowsBackend: Fetching host info...
12-09 17:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 17:07 DEBUG  WindowsBackend: windows version=vista
12-09 17:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 17:07 DEBUG  WindowsBackend: windows_sp=None
12-09 17:07 DEBUG  WindowsBackend: windows_build=7600
12-09 17:07 DEBUG  WindowsBackend: gmt=0
12-09 17:07 DEBUG  WindowsBackend: country=GB
12-09 17:07 DEBUG  WindowsBackend: timezone=Europe/London
12-09 17:07 DEBUG  WindowsBackend: windows_username=Sam'
12-09 17:07 DEBUG  WindowsBackend: user_full_name=Sam'
12-09 17:07 DEBUG  WindowsBackend: user_directory=C:\Users\Sam'
12-09 17:07 DEBUG  WindowsBackend: windows_language_code=1033
12-09 17:07 DEBUG  WindowsBackend: windows_language=English
12-09 17:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
12-09 17:07 DEBUG  WindowsBackend: bootloader=vista
12-09 17:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43147.1054688 mb free ntfs)
12-09 17:07 DEBUG  WindowsBackend: drive=Drive(C: hd 43147.1054688 mb free ntfs)
12-09 17:07 DEBUG  WindowsBackend: drive=Drive(D: hd 143884.40625 mb free ntfs)
12-09 17:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
12-09 17:07 DEBUG  WindowsBackend: drive=Drive(F: hd 188.58203125 mb free ntfs)
12-09 17:07 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 17:07 DEBUG  WindowsBackend: uninstaller_path=None
12-09 17:07 DEBUG  WindowsBackend: previous_target_dir=None
12-09 17:07 DEBUG  WindowsBackend: previous_distro_name=None
12-09 17:07 DEBUG  WindowsBackend: keyboard_id=134809609
12-09 17:07 DEBUG  WindowsBackend: keyboard_layout=gb
12-09 17:07 DEBUG  WindowsBackend: keyboard_variant=
12-09 17:07 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-09 17:07 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-09 17:07 DEBUG  WindowsBackend: total_memory_mb=1906.671875
12-09 17:07 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 17:07 DEBUG  CommonBackend: Searching for local CDs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Edubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 DEBUG  Distro:   checking whether Q:\ is a valid Lubuntu CD
12-09 17:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:07 INFO   root: Running the installer...
12-09 17:07 DEBUG  WindowsFrontend: __init__...
12-09 17:07 DEBUG  WindowsFrontend: on_init...
12-09 17:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\translations, languages=['en_GB', 'en']
12-09 17:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\translations, languages=['en_GB', 'en']
12-09 17:09 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=sam
12-09 17:09 INFO   root: Received settings
12-09 17:09 DEBUG  CommonBackend: Searching for local CD
12-09 17:09 DEBUG  Distro:   checking whether C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp is a valid Ubuntu CD
12-09 17:09 DEBUG  Distro:     does not contain C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\casper\filesystem.squashfs
12-09 17:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 17:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 17:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 17:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 17:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-09 17:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-09 17:09 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 17:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 17:09 DEBUG  CommonBackend: Searching for local ISO
12-09 17:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\translations, languages=['en_GB', 'en']
12-09 17:09 DEBUG  TaskList: # Running tasklist...
12-09 17:09 DEBUG  TaskList: ## Running select_target_dir...
12-09 17:09 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 17:09 DEBUG  TaskList: ## Finished select_target_dir
12-09 17:09 DEBUG  TaskList: ## Running create_dir_structure...
12-09 17:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 17:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 17:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 17:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 17:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 17:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 17:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 17:09 DEBUG  TaskList: ## Finished create_dir_structure
12-09 17:09 DEBUG  TaskList: ## Running create_uninstaller...
12-09 17:09 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Sam'\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 17:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 17:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 17:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 17:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 17:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
12-09 17:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 17:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 17:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 17:09 DEBUG  TaskList: ## Finished create_uninstaller
12-09 17:09 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 17:09 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 17:09 DEBUG  TaskList: ## Running get_diskimage...
12-09 17:09 DEBUG  TaskList: New task download
12-09 17:09 DEBUG  TaskList: ### Running download...
12-09 17:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
12-09 17:09 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
12-09 17:13 DEBUG  TaskList: ### Finished download
12-09 17:13 DEBUG  downloader: download finished (read 562061340 bytes)
12-09 17:13 DEBUG  TaskList: ## Finished get_diskimage
12-09 17:13 DEBUG  TaskList: ## Running extract_diskimage...
12-09 17:16 DEBUG  TaskList: ## Finished extract_diskimage
12-09 17:16 DEBUG  TaskList: ## Running choose_disk_sizes...
12-09 17:16 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-09 17:16 DEBUG  TaskList: ## Finished choose_disk_sizes
12-09 17:16 DEBUG  TaskList: ## Running expand_diskimage...
12-09 17:16 ERROR  TaskList: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylA50B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylA50B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


12-09 17:16 DEBUG  TaskList: # Cancelling tasklist
12-09 17:16 DEBUG  TaskList: # Finished tasklist
12-09 17:16 ERROR  root: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylA50B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Sam'\AppData\Local\Temp\pylA50B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Sam/AppData/Local/Temp/pylA50B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

---

### Post by Freezing Point on 2012-12-09
Might of posted this in the wrong place, I have unblocked the file and run it as a administrator. Trying that.

---

### Post by Freezing Point on 2012-12-09
I tried another solution by downloading the xz file and using dimagepath with the wubi.exe file, it still didn't work, someone please help me :(

---

### Post by westie457 on 2012-12-09
Hello and welcome to the forum.
This > >>command=C:\Users\Sam'\AppData\Local\Temp\pylA50B .tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M and this > 12-09 17:07 DEBUG WindowsBackend: drive=Drive(C: hd 43147.1054688 mb free ntfs) suggest to me that you do not have enough contiguous free space on the hard drive to create the root.disk file.

Some house-cleaning is required to free up some space or reduce the size of the root.disk file.

Some quick acting tools to use are 'ccleaner' from [www.piriform.com](www.piriform.com) to clean out most of the junk.

To defrag the hard drive use Auslogics disk-defragmenter. They have a free one and is very quick.

Once you have done this,try again.

---

### Post by Freezing Point on 2012-12-09
> **westie457 said:**
> Hello and welcome to the forum.
This  and this  suggest to me that you do not have enough contiguous free space on the hard drive to create the root.disk file.

Some house-cleaning is required to free up some space or reduce the size of the root.disk file.

Some quick acting tools to use are 'ccleaner' from [www.piriform.com](www.piriform.com) to clean out most of the junk.

To defrag the hard drive use Auslogics disk-defragmenter. They have a free one and is very quick.

Once you have done this,try again.

Hi there,

Thanks for the advice, I have 41GB free on my HDD. I will use Ccleaner and auslogics disk defrag and I will keep you posted, thank you.

---

### Post by Freezing Point on 2012-12-09
just tried it, still doesn't work, same error.

---

### Post by Freezing Point on 2012-12-09
Running ubuntu in a virtual machine for now :) untill the problem is fixed.

---

