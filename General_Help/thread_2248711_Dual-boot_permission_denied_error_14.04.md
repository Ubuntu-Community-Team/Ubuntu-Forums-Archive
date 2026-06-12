---
title: "Dual-boot permission denied error 14.04"
date: 2014-10-16
forum: General Help
---

### Post by richard643 on 2014-10-16
Hi all, 

I'm trying to install ubuntu 14.04 alongside a windows 7 installation but in using the wubi.exe installer I keep getting a permission denied error at the very end of the installation (and when rebooting I don't even get the option of choosing OS's, as I've read other posts where the error message simply didn't matter). When booting from the live cd I'm not even given the option to install alongside windows, and even if I manage to manually set the partitions I still seem to be unable to get a proper installation. Could it be a hardware problem? I've tried the wubi with automatic download, with cd and I've tried booting from both dvd and usb but still get an i/o error, similar with older versions of ubuntu...

My setup is:
Asus X99-S 
Intel i7-5820K
Crucial DDR4 32GB
Samsung SSD Evo 840 500GB
Toshiba 2GB secondary harddrive

Any help would be very much appreciated!

The full log-file for the permission error is below:
10-16 17:26 INFO   root: === wubi 14.04 rev286 ===
10-16 17:26 DEBUG  root: Logfile is c:\users\varun\appdata\local\temp\wubi-14.04-rev286.log
10-16 17:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Varun\\Downloads\\wubi.exe"']
10-16 17:26 DEBUG  CommonBackend: data_dir=C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\data
10-16 17:26 DEBUG  WindowsBackend: 7z=C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\bin\7z.exe
10-16 17:26 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 17:26 DEBUG  CommonBackend: Fetching basic info...
10-16 17:26 DEBUG  CommonBackend: original_exe=C:\Users\Varun\Downloads\wubi.exe
10-16 17:26 DEBUG  CommonBackend: platform=win32
10-16 17:26 DEBUG  CommonBackend: osname=nt
10-16 17:26 DEBUG  CommonBackend: language=en_GB
10-16 17:26 DEBUG  CommonBackend: encoding=cp1252
10-16 17:26 DEBUG  WindowsBackend: arch=amd64
10-16 17:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\data\isolist.ini
10-16 17:26 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-16 17:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 17:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 17:26 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-16 17:26 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-16 17:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 17:26 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-16 17:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 17:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 17:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 17:26 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-16 17:26 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-16 17:26 DEBUG  WindowsBackend: Fetching host info...
10-16 17:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 17:26 DEBUG  WindowsBackend: windows version=vista
10-16 17:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-16 17:26 DEBUG  WindowsBackend: windows_sp=None
10-16 17:26 DEBUG  WindowsBackend: windows_build=7601
10-16 17:26 DEBUG  WindowsBackend: gmt=0
10-16 17:26 DEBUG  WindowsBackend: country=GB
10-16 17:26 DEBUG  WindowsBackend: timezone=Europe/London
10-16 17:26 DEBUG  WindowsBackend: windows_username=Varun
10-16 17:26 DEBUG  WindowsBackend: user_full_name=Varun
10-16 17:26 DEBUG  WindowsBackend: user_directory=C:\Users\Varun
10-16 17:26 DEBUG  WindowsBackend: windows_language_code=1033
10-16 17:26 DEBUG  WindowsBackend: windows_language=English
10-16 17:26 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
10-16 17:26 DEBUG  WindowsBackend: bootloader=vista
10-16 17:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 397763.117188 mb free ntfs)
10-16 17:26 DEBUG  WindowsBackend: drive=Drive(C: hd 397763.117188 mb free ntfs)
10-16 17:26 DEBUG  WindowsBackend: drive=Drive(D: hd 1874906.3125 mb free ntfs)
10-16 17:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-16 17:26 DEBUG  WindowsBackend: uninstaller_path=None
10-16 17:26 DEBUG  WindowsBackend: previous_target_dir=None
10-16 17:26 DEBUG  WindowsBackend: previous_distro_name=None
10-16 17:26 DEBUG  WindowsBackend: keyboard_id=134809609
10-16 17:26 DEBUG  WindowsBackend: keyboard_layout=gb
10-16 17:26 DEBUG  WindowsBackend: keyboard_variant=
10-16 17:26 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-16 17:26 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-16 17:26 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-16 17:26 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 17:26 DEBUG  CommonBackend: Searching for local CDs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Ubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Ubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Kubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Kubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Mythbuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Mythbuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Edubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Edubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Lubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Lubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Ubuntu Studio CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Ubuntu Studio CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 17:26 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
10-16 17:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
10-16 17:26 INFO   Distro: Found a valid CD for Ubuntu: E:\
10-16 17:26 INFO   root: Running the installer...
10-16 17:26 DEBUG  WindowsFrontend: __init__...
10-16 17:26 DEBUG  WindowsFrontend: on_init...
10-16 17:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\translations, languages=['en_GB', 'en']
10-16 17:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\translations, languages=['en_GB', 'en']
10-16 17:26 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=varun
10-16 17:26 INFO   root: Received settings
10-16 17:26 DEBUG  CommonBackend: Searching for local CD
10-16 17:26 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp is a valid Ubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 17:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 17:26 INFO   Distro: Found a valid CD for Ubuntu: E:\
10-16 17:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\translations, languages=['en_GB', 'en']
10-16 17:26 DEBUG  TaskList: # Running tasklist...
10-16 17:26 DEBUG  TaskList: ## Running select_target_dir...
10-16 17:26 INFO   WindowsBackend: Installing into C:\ubuntu
10-16 17:26 DEBUG  TaskList: ## Finished select_target_dir
10-16 17:26 DEBUG  TaskList: ## Running create_dir_structure...
10-16 17:26 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-16 17:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-16 17:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-16 17:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-16 17:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-16 17:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-16 17:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-16 17:26 DEBUG  TaskList: ## Finished create_dir_structure
10-16 17:26 DEBUG  TaskList: ## Running uncompress_target_dir...
10-16 17:26 DEBUG  TaskList: ## Finished uncompress_target_dir
10-16 17:26 DEBUG  TaskList: ## Running create_uninstaller...
10-16 17:26 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Varun\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-16 17:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-16 17:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-16 17:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-16 17:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-16 17:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
10-16 17:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-16 17:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-16 17:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-16 17:26 DEBUG  TaskList: ## Finished create_uninstaller
10-16 17:26 DEBUG  TaskList: ## Running copy_installation_files...
10-16 17:26 DEBUG  WindowsBackend: Copying C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-16 17:26 DEBUG  WindowsBackend: Copying C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\winboot -> C:\ubuntu\winboot
10-16 17:26 DEBUG  WindowsBackend: Copying C:\Users\Varun\AppData\Local\Temp\pyl1B6C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-16 17:26 DEBUG  TaskList: ## Finished copy_installation_files
10-16 17:26 DEBUG  TaskList: ## Running get_iso...
10-16 17:26 DEBUG  TaskList: New task copy_file
10-16 17:26 DEBUG  TaskList: ### Running copy_file...
10-16 17:28 DEBUG  TaskList: ### Finished copy_file
10-16 17:28 DEBUG  TaskList: New task check_iso
10-16 17:28 DEBUG  TaskList: ### Running check_iso...
10-16 17:28 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
10-16 17:28 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
10-16 17:28 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
10-16 17:28 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
10-16 17:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
10-16 17:28 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
10-16 17:28 DEBUG  TaskList: New task get_metalink
10-16 17:28 DEBUG  TaskList: #### Running get_metalink...
10-16 17:28 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
10-16 17:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
10-16 17:28 DEBUG  downloader: download finished (read 45848 bytes)
10-16 17:28 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
10-16 17:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
10-16 17:28 DEBUG  downloader: download finished (read 560 bytes)
10-16 17:28 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
10-16 17:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-16 17:28 DEBUG  downloader: download finished (read 198 bytes)
10-16 17:28 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-16 17:28 INFO   saplog: Checking block bindings..
10-16 17:28 INFO   saplog: Key verified successfully.
10-16 17:28 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink


10-16 17:28 ERROR  CommonBackend: The md5 of the metalink does match
10-16 17:28 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
10-16 17:28 DEBUG  TaskList: #### Finished get_metalink
10-16 17:28 DEBUG  TaskList: New task get_file_md5
10-16 17:28 DEBUG  TaskList: #### Running get_file_md5...
10-16 17:28 DEBUG  TaskList: #### Finished get_file_md5
10-16 17:28 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dccff28314d9ae4ed262cfc6f35e5153 != 8d7cd0a69b7666926a8b4903b5855c59)
None
10-16 17:28 DEBUG  TaskList: ### Finished check_iso
10-16 17:28 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
10-16 17:28 DEBUG  TaskList: # Cancelling tasklist
10-16 17:28 DEBUG  TaskList: # Finished tasklist
10-16 17:28 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
10-16 17:30 INFO   root: === wubi 14.04 rev286 ===
10-16 17:30 DEBUG  root: Logfile is c:\users\varun\appdata\local\temp\wubi-14.04-rev286.log
10-16 17:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Varun\\Downloads\\wubi.exe"']
10-16 17:30 DEBUG  CommonBackend: data_dir=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\data
10-16 17:30 DEBUG  WindowsBackend: 7z=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\bin\7z.exe
10-16 17:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 17:30 DEBUG  CommonBackend: Fetching basic info...
10-16 17:30 DEBUG  CommonBackend: original_exe=C:\Users\Varun\Downloads\wubi.exe
10-16 17:30 DEBUG  CommonBackend: platform=win32
10-16 17:30 DEBUG  CommonBackend: osname=nt
10-16 17:30 DEBUG  CommonBackend: language=en_GB
10-16 17:30 DEBUG  CommonBackend: encoding=cp1252
10-16 17:30 DEBUG  WindowsBackend: arch=amd64
10-16 17:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\data\isolist.ini
10-16 17:30 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-16 17:30 DEBUG  WindowsBackend: Fetching host info...
10-16 17:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 17:30 DEBUG  WindowsBackend: windows version=vista
10-16 17:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-16 17:30 DEBUG  WindowsBackend: windows_sp=None
10-16 17:30 DEBUG  WindowsBackend: windows_build=7601
10-16 17:30 DEBUG  WindowsBackend: gmt=0
10-16 17:30 DEBUG  WindowsBackend: country=GB
10-16 17:30 DEBUG  WindowsBackend: timezone=Europe/London
10-16 17:30 DEBUG  WindowsBackend: windows_username=Varun
10-16 17:30 DEBUG  WindowsBackend: user_full_name=Varun
10-16 17:30 DEBUG  WindowsBackend: user_directory=C:\Users\Varun
10-16 17:30 DEBUG  WindowsBackend: windows_language_code=1033
10-16 17:30 DEBUG  WindowsBackend: windows_language=English
10-16 17:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
10-16 17:30 DEBUG  WindowsBackend: bootloader=vista
10-16 17:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 396778.21875 mb free ntfs)
10-16 17:30 DEBUG  WindowsBackend: drive=Drive(C: hd 396778.21875 mb free ntfs)
10-16 17:30 DEBUG  WindowsBackend: drive=Drive(D: hd 1874906.3125 mb free ntfs)
10-16 17:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-16 17:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-16 17:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-16 17:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-16 17:30 DEBUG  WindowsBackend: keyboard_id=134809609
10-16 17:30 DEBUG  WindowsBackend: keyboard_layout=gb
10-16 17:30 DEBUG  WindowsBackend: keyboard_variant=
10-16 17:30 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-16 17:30 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-16 17:30 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-16 17:30 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 17:30 DEBUG  CommonBackend: Searching for local CDs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 INFO   root: Already installed, running the uninstaller...
10-16 17:30 INFO   root: Running the uninstaller...
10-16 17:30 INFO   CommonBackend: This is the uninstaller running
10-16 17:30 DEBUG  WindowsFrontend: __init__...
10-16 17:30 DEBUG  WindowsFrontend: on_init...
10-16 17:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\translations, languages=['en_GB', 'en']
10-16 17:30 INFO   root: Received settings
10-16 17:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\translations, languages=['en_GB', 'en']
10-16 17:30 DEBUG  TaskList: # Running tasklist...
10-16 17:30 DEBUG  TaskList: ## Running Remove bootloader entry....
10-16 17:30 DEBUG  WindowsBackend: Could not find bcd id
10-16 17:30 DEBUG  WindowsBackend: undo_bootini C:
10-16 17:30 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 396778.21875 mb free ntfs)
10-16 17:30 DEBUG  WindowsBackend: undo_bootini D:
10-16 17:30 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1874906.3125 mb free ntfs)
10-16 17:30 DEBUG  TaskList: ## Finished Remove bootloader entry.
10-16 17:30 DEBUG  TaskList: ## Running Remove target dir....
10-16 17:30 DEBUG  CommonBackend: Deleting C:\ubuntu
10-16 17:30 DEBUG  TaskList: ## Finished Remove target dir.
10-16 17:30 DEBUG  TaskList: ## Running Remove registry key....
10-16 17:30 DEBUG  TaskList: ## Finished Remove registry key.
10-16 17:30 DEBUG  TaskList: # Finished tasklist
10-16 17:30 INFO   root: Almost finished uninstalling
10-16 17:30 INFO   root: Finished uninstallation
10-16 17:30 DEBUG  CommonBackend: Fetching basic info...
10-16 17:30 DEBUG  CommonBackend: original_exe=C:\Users\Varun\Downloads\wubi.exe
10-16 17:30 DEBUG  CommonBackend: platform=win32
10-16 17:30 DEBUG  CommonBackend: osname=nt
10-16 17:30 DEBUG  WindowsBackend: arch=amd64
10-16 17:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\data\isolist.ini
10-16 17:30 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 17:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-16 17:30 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-16 17:30 DEBUG  WindowsBackend: Fetching host info...
10-16 17:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 17:30 DEBUG  WindowsBackend: windows version=vista
10-16 17:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-16 17:30 DEBUG  WindowsBackend: windows_sp=None
10-16 17:30 DEBUG  WindowsBackend: windows_build=7601
10-16 17:30 DEBUG  WindowsBackend: gmt=0
10-16 17:30 DEBUG  WindowsBackend: country=GB
10-16 17:30 DEBUG  WindowsBackend: timezone=Europe/London
10-16 17:30 DEBUG  WindowsBackend: windows_username=Varun
10-16 17:30 DEBUG  WindowsBackend: user_full_name=Varun
10-16 17:30 DEBUG  WindowsBackend: user_directory=C:\Users\Varun
10-16 17:30 DEBUG  WindowsBackend: windows_language_code=1033
10-16 17:30 DEBUG  WindowsBackend: windows_language=English
10-16 17:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
10-16 17:30 DEBUG  WindowsBackend: bootloader=vista
10-16 17:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 397761.90625 mb free ntfs)
10-16 17:30 DEBUG  WindowsBackend: drive=Drive(C: hd 397761.90625 mb free ntfs)
10-16 17:30 DEBUG  WindowsBackend: drive=Drive(D: hd 1874906.3125 mb free ntfs)
10-16 17:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-16 17:30 DEBUG  WindowsBackend: uninstaller_path=None
10-16 17:30 DEBUG  WindowsBackend: previous_target_dir=None
10-16 17:30 DEBUG  WindowsBackend: previous_distro_name=None
10-16 17:30 DEBUG  WindowsBackend: keyboard_id=134809609
10-16 17:30 DEBUG  WindowsBackend: keyboard_layout=gb
10-16 17:30 DEBUG  WindowsBackend: keyboard_variant=
10-16 17:30 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-16 17:30 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 17:30 DEBUG  CommonBackend: Searching for local CDs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 INFO   root: Running the installer...
10-16 17:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\translations, languages=['en_GB', 'en']
10-16 17:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\translations, languages=['en_GB', 'en']
10-16 17:30 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=varun
10-16 17:30 INFO   root: Received settings
10-16 17:30 DEBUG  CommonBackend: Searching for local CD
10-16 17:30 DEBUG  Distro:   checking whether C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 17:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 17:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 17:30 DEBUG  CommonBackend: Searching for local ISO
10-16 17:30 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso
10-16 17:30 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso
10-16 17:30 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
10-16 17:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
10-16 17:30 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso
10-16 17:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\translations, languages=['en_GB', 'en']
10-16 17:30 DEBUG  TaskList: # Running tasklist...
10-16 17:30 DEBUG  TaskList: ## Running select_target_dir...
10-16 17:30 INFO   WindowsBackend: Installing into C:\ubuntu
10-16 17:30 DEBUG  TaskList: ## Finished select_target_dir
10-16 17:30 DEBUG  TaskList: ## Running create_dir_structure...
10-16 17:30 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-16 17:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-16 17:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-16 17:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-16 17:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-16 17:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-16 17:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-16 17:30 DEBUG  TaskList: ## Finished create_dir_structure
10-16 17:30 DEBUG  TaskList: ## Running uncompress_target_dir...
10-16 17:30 DEBUG  TaskList: ## Finished uncompress_target_dir
10-16 17:30 DEBUG  TaskList: ## Running create_uninstaller...
10-16 17:30 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Varun\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-16 17:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-16 17:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-16 17:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-16 17:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-16 17:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
10-16 17:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-16 17:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-16 17:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-16 17:30 DEBUG  TaskList: ## Finished create_uninstaller
10-16 17:30 DEBUG  TaskList: ## Running copy_installation_files...
10-16 17:30 DEBUG  WindowsBackend: Copying C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-16 17:30 DEBUG  WindowsBackend: Copying C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\winboot -> C:\ubuntu\winboot
10-16 17:30 DEBUG  WindowsBackend: Copying C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-16 17:30 DEBUG  TaskList: ## Finished copy_installation_files
10-16 17:30 DEBUG  TaskList: ## Running get_iso...
10-16 17:30 DEBUG  CommonBackend: Trying to use ISO C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso
10-16 17:30 DEBUG  TaskList: New task check_iso
10-16 17:30 DEBUG  TaskList: ### Running check_iso...
10-16 17:30 DEBUG  CommonBackend: Checking C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso
10-16 17:30 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso
10-16 17:30 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso
10-16 17:30 DEBUG  TaskList: New task get_metalink
10-16 17:30 DEBUG  TaskList: #### Running get_metalink...
10-16 17:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
10-16 17:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
10-16 17:30 DEBUG  downloader: download finished (read 45848 bytes)
10-16 17:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
10-16 17:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
10-16 17:30 DEBUG  downloader: download finished (read 560 bytes)
10-16 17:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
10-16 17:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-16 17:30 DEBUG  downloader: download finished (read 198 bytes)
10-16 17:30 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-16 17:30 INFO   saplog: Checking block bindings..
10-16 17:30 INFO   saplog: Key verified successfully.
10-16 17:30 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink


10-16 17:30 ERROR  CommonBackend: The md5 of the metalink does match
10-16 17:30 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
10-16 17:30 DEBUG  TaskList: #### Finished get_metalink
10-16 17:30 DEBUG  TaskList: New task get_file_md5
10-16 17:30 DEBUG  TaskList: #### Running get_file_md5...
10-16 17:30 DEBUG  TaskList: #### Finished get_file_md5
10-16 17:30 ERROR  CommonBackend: Invalid md5 for ISO C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso (dccff28314d9ae4ed262cfc6f35e5153 != 8d7cd0a69b7666926a8b4903b5855c59)
None
10-16 17:30 DEBUG  TaskList: ### Finished check_iso
10-16 17:30 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-16 17:30 DEBUG  TaskList: New task download
10-16 17:30 DEBUG  TaskList: ### Running download...
10-16 17:30 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
10-16 17:30 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.




10-16 17:30 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


 in task download
10-16 17:30 DEBUG  TaskList: ### Finished download
10-16 17:30 ERROR  root: Could not remove: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
10-16 17:30 DEBUG  TaskList: New task download
10-16 17:30 DEBUG  TaskList: ### Running download...
10-16 17:30 DEBUG  downloader: downloading [http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso](http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
10-16 17:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso, url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso, basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None
10-16 17:35 DEBUG  TaskList: ### Finished download
10-16 17:35 DEBUG  downloader: download finished (read 1010827264 bytes)
10-16 17:35 DEBUG  TaskList: New task check_iso
10-16 17:35 DEBUG  TaskList: ### Running check_iso...
10-16 17:35 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
10-16 17:35 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
10-16 17:35 ERROR  WindowsBackend: Error executing command
>>command=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
10-16 17:35 DEBUG  WindowsBackend: command >>C:\Users\Varun\AppData\Local\Temp\pylEBE4.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
10-16 17:35 DEBUG  Distro:     does not contain casper\filesystem.squashfs
10-16 17:35 DEBUG  TaskList: ### Finished check_iso
10-16 17:35 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
10-16 17:35 DEBUG  TaskList: # Cancelling tasklist
10-16 17:35 DEBUG  TaskList: # Finished tasklist
10-16 17:35 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'

---

### Post by O9aIevckc0 on 2014-10-16
Wubi was removed as an installation option from Ubuntu 13.04 onward

---

### Post by hakuna_matata on 2014-10-16
First of all, I recommend an Ubuntu install without Wubi.

But a part of your log is important for an install without Wubi, too.
> ```
10-16 17:30 ERROR  CommonBackend: Invalid md5 for ISO  C:\Users\Varun\Downloads\ubuntu-14.04.1-desktop-amd64.iso  (dccff28314d9ae4ed262cfc6f35e5153 != 8d7cd0a69b7666926a8b4903b5855c59)
None
```
8d7cd0a69b7666926a8b4903b5855c59 is not a valid MD5 sum of ubuntu-14.04.1-desktop-amd64.iso. It should be 119cb63b48c9a18f31f417f09655efbd. This means your ubuntu-14.04.1-desktop-amd64.iso is incomplete or corrupted. Maybe, you have to download a new one: [http://releases.ubuntu.com/trusty](http://releases.ubuntu.com/trusty)

Unfortunately, another problem is that your version of wubi.exe doesn't work for Ubuntu 14.04.1: [https://bugs.launchpad.net/wubi/+bug/1367071](https://bugs.launchpad.net/wubi/+bug/1367071)

So, as I wrote above: I recommend an Ubuntu install without Wubi.

If this is not what you want you can use a patched version wubi14041.exe from our project: [http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598](http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598)
The project is mainly for systems with UEFI but it works without UEFI, too.

---

