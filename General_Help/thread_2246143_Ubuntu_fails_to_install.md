---
title: "Ubuntu fails to install"
date: 2014-09-28
forum: General Help
---

### Post by mbrown122098 on 2014-09-28
My CD/DVD Drive decided it wanted to live free, My computer does not recognize it anymore and when i put any disc into it... nothing happens. I tried to install ubuntu with a usb drive, but there was no success there. I tried to install through wubi but I always get an error stating 

"An error accourred:

'NoneType' object has no attribute 'get_info'

For more information, please see the log file:
c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log"

This is what the log said: 

```
09-28 13:50 INFO   root: === wubi 14.04 rev286 ===
09-28 13:50 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 13:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Matt\\AppData\\Local\\Temp\\Rar$EXa0.203\\wubi.exe"']
09-28 13:50 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\data
09-28 13:50 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\bin\7z.exe
09-28 13:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 13:50 DEBUG  CommonBackend: Fetching basic info...
09-28 13:50 DEBUG  CommonBackend: original_exe=C:\Users\Matt\AppData\Local\Temp\Rar$EXa0.203\wubi.exe
09-28 13:50 DEBUG  CommonBackend: platform=win32
09-28 13:50 DEBUG  CommonBackend: osname=nt
09-28 13:50 DEBUG  CommonBackend: language=en_US
09-28 13:50 DEBUG  CommonBackend: encoding=cp1252
09-28 13:50 DEBUG  WindowsBackend: arch=amd64
09-28 13:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\data\isolist.ini
09-28 13:50 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 13:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 13:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 13:50 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 13:50 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 13:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 13:50 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 13:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 13:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 13:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 13:50 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 13:50 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 13:50 DEBUG  WindowsBackend: Fetching host info...
09-28 13:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 13:50 DEBUG  WindowsBackend: windows version=vista
09-28 13:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 13:50 DEBUG  WindowsBackend: windows_sp=None
09-28 13:50 DEBUG  WindowsBackend: windows_build=7601
09-28 13:50 DEBUG  WindowsBackend: gmt=-6
09-28 13:50 DEBUG  WindowsBackend: country=US
09-28 13:50 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 13:50 DEBUG  WindowsBackend: windows_username=Matt
09-28 13:50 DEBUG  WindowsBackend: user_full_name=Matt
09-28 13:50 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 13:50 DEBUG  WindowsBackend: windows_language_code=1033
09-28 13:50 DEBUG  WindowsBackend: windows_language=English
09-28 13:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 13:50 DEBUG  WindowsBackend: bootloader=vista
09-28 13:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 90589.328125 mb free ntfs)
09-28 13:50 DEBUG  WindowsBackend: drive=Drive(C: hd 90589.328125 mb free ntfs)
09-28 13:50 DEBUG  WindowsBackend: drive=Drive(F: hd 337623.429688 mb free ntfs)
09-28 13:50 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 13:50 DEBUG  WindowsBackend: uninstaller_path=None
09-28 13:50 DEBUG  WindowsBackend: previous_target_dir=None
09-28 13:50 DEBUG  WindowsBackend: previous_distro_name=None
09-28 13:50 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 13:50 DEBUG  WindowsBackend: keyboard_layout=us
09-28 13:50 DEBUG  WindowsBackend: keyboard_variant=
09-28 13:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 13:50 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 13:50 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 13:50 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 13:50 DEBUG  CommonBackend: Searching for local CDs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Ubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Ubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Kubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Kubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Mythbuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Mythbuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Edubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Edubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Lubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Lubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Ubuntu Studio CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Ubuntu Studio CD
09-28 13:50 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
09-28 13:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
09-28 13:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:50 INFO   root: Running the installer...
09-28 13:50 DEBUG  WindowsFrontend: __init__...
09-28 13:50 DEBUG  WindowsFrontend: on_init...
09-28 13:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\translations, languages=['en_US', 'en']
09-28 13:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\translations, languages=['en_US', 'en']
09-28 13:51 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=matt
09-28 13:51 INFO   root: Received settings
09-28 13:51 DEBUG  CommonBackend: Searching for local CD
09-28 13:51 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp is a valid Ubuntu CD
09-28 13:51 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\casper\filesystem.squashfs
09-28 13:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 13:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 13:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 13:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 13:51 DEBUG  CommonBackend: Searching for local ISO
09-28 13:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\translations, languages=['en_US', 'en']
09-28 13:51 DEBUG  TaskList: # Running tasklist...
09-28 13:51 DEBUG  TaskList: ## Running select_target_dir...
09-28 13:51 INFO   WindowsBackend: Installing into C:\ubuntu
09-28 13:51 DEBUG  TaskList: ## Finished select_target_dir
09-28 13:51 DEBUG  TaskList: ## Running create_dir_structure...
09-28 13:51 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-28 13:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-28 13:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-28 13:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-28 13:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-28 13:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-28 13:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-28 13:51 DEBUG  TaskList: ## Finished create_dir_structure
09-28 13:51 DEBUG  TaskList: ## Running uncompress_target_dir...
09-28 13:51 DEBUG  TaskList: ## Finished uncompress_target_dir
09-28 13:51 DEBUG  TaskList: ## Running create_uninstaller...
09-28 13:51 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Matt\AppData\Local\Temp\Rar$EXa0.203\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-28 13:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-28 13:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-28 13:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-28 13:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-28 13:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
09-28 13:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-28 13:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-28 13:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-28 13:51 DEBUG  TaskList: ## Finished create_uninstaller
09-28 13:51 DEBUG  TaskList: ## Running copy_installation_files...
09-28 13:51 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-28 13:51 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\winboot -> C:\ubuntu\winboot
09-28 13:51 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-28 13:51 DEBUG  TaskList: ## Finished copy_installation_files
09-28 13:51 DEBUG  TaskList: ## Running get_iso...
09-28 13:51 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-28 13:51 DEBUG  TaskList: New task get_metalink
09-28 13:51 DEBUG  TaskList: ### Running get_metalink...
09-28 13:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
09-28 13:51 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-28 13:51 DEBUG  downloader: download finished (read 45848 bytes)
09-28 13:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-28 13:51 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
09-28 13:51 DEBUG  downloader: download finished (read 560 bytes)
09-28 13:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-28 13:51 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-28 13:51 DEBUG  downloader: download finished (read 198 bytes)
09-28 13:51 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-28 13:51 INFO   saplog: Checking block bindings..
09-28 13:51 INFO   saplog: Key verified successfully.
09-28 13:51 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink

09-28 13:51 ERROR  CommonBackend: The md5 of the metalink does match
09-28 13:51 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-28 13:51 DEBUG  TaskList: ### Finished get_metalink
09-28 13:51 DEBUG  TaskList: New task download
09-28 13:51 DEBUG  TaskList: ### Running download...
09-28 13:51 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-28 13:51 ERROR  TaskList: Traceback (most recent call last):
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


09-28 13:51 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.

 in task download
09-28 13:51 DEBUG  TaskList: ### Finished download
09-28 13:51 ERROR  root: Could not remove: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-28 13:51 DEBUG  TaskList: New task download
09-28 13:51 DEBUG  TaskList: ### Running download...
09-28 13:51 DEBUG  downloader: downloading [http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso](http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-28 13:51 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso, url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso, basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None
09-28 13:58 DEBUG  TaskList: ### Finished download
09-28 13:58 DEBUG  downloader: download finished (read 1010827264 bytes)
09-28 13:58 DEBUG  TaskList: New task check_iso
09-28 13:58 DEBUG  TaskList: ### Running check_iso...
09-28 13:58 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-28 13:58 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-28 13:58 ERROR  WindowsBackend: Error executing command
>>command=C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
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
>>command=C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=

7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18



Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.






Errors: 1
>>stdout=
09-28 13:58 DEBUG  WindowsBackend: command >>C:\Users\Matt\AppData\Local\Temp\pyl12A.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-28 13:58 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-28 13:58 DEBUG  TaskList: ### Finished check_iso
09-28 13:58 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-28 13:58 DEBUG  TaskList: # Cancelling tasklist
09-28 13:58 DEBUG  TaskList: # Finished tasklist
09-28 13:58 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-28 14:16 INFO   root: === wubi 14.04 rev286 ===
09-28 14:16 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 14:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
09-28 14:16 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\data
09-28 14:16 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\bin\7z.exe
09-28 14:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 14:16 DEBUG  CommonBackend: Fetching basic info...
09-28 14:16 DEBUG  CommonBackend: original_exe=E:\wubi.exe
09-28 14:16 DEBUG  CommonBackend: platform=win32
09-28 14:16 DEBUG  CommonBackend: osname=nt
09-28 14:16 DEBUG  CommonBackend: language=en_US
09-28 14:16 DEBUG  CommonBackend: encoding=cp1252
09-28 14:16 DEBUG  WindowsBackend: arch=amd64
09-28 14:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\data\isolist.ini
09-28 14:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 14:16 DEBUG  WindowsBackend: Fetching host info...
09-28 14:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 14:16 DEBUG  WindowsBackend: windows version=vista
09-28 14:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 14:16 DEBUG  WindowsBackend: windows_sp=None
09-28 14:16 DEBUG  WindowsBackend: windows_build=7601
09-28 14:16 DEBUG  WindowsBackend: gmt=-6
09-28 14:16 DEBUG  WindowsBackend: country=US
09-28 14:16 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 14:16 DEBUG  WindowsBackend: windows_username=Matt
09-28 14:16 DEBUG  WindowsBackend: user_full_name=Matt
09-28 14:16 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 14:16 DEBUG  WindowsBackend: windows_language_code=1033
09-28 14:16 DEBUG  WindowsBackend: windows_language=English
09-28 14:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 14:16 DEBUG  WindowsBackend: bootloader=vista
09-28 14:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95332.078125 mb free ntfs)
09-28 14:16 DEBUG  WindowsBackend: drive=Drive(C: hd 95332.078125 mb free ntfs)
09-28 14:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 14:16 DEBUG  WindowsBackend: drive=Drive(F: hd 337623.417969 mb free ntfs)
09-28 14:16 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 14:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 14:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 14:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 14:16 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 14:16 DEBUG  WindowsBackend: keyboard_layout=us
09-28 14:16 DEBUG  WindowsBackend: keyboard_variant=
09-28 14:16 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 14:16 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 14:16 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 14:16 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 14:16 DEBUG  CommonBackend: Searching for local CDs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Ubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Ubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Kubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Kubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Mythbuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Mythbuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Edubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Edubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Lubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Lubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Ubuntu Studio CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp is a valid Ubuntu Studio CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 14:16 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 14:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 14:16 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 14:16 INFO   root: Running the CD menu...
09-28 14:16 DEBUG  WindowsFrontend: __init__...
09-28 14:16 DEBUG  WindowsFrontend: on_init...
09-28 14:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\translations, languages=['en_US', 'en']
09-28 14:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylD6E0.tmp\translations, languages=['en_US', 'en']
09-28 14:16 DEBUG  root: application.quit
09-28 14:16 DEBUG  WindowsFrontend: frontend.quit
09-28 14:16 DEBUG  WindowsFrontend: frontend.on_quit
09-28 14:16 DEBUG  root: application.on_quit
09-28 14:16 INFO   root: sys.exit
09-28 14:16 INFO   root: === wubi 14.04 rev286 ===
09-28 14:16 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 14:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
09-28 14:16 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\data
09-28 14:16 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\bin\7z.exe
09-28 14:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 14:16 DEBUG  CommonBackend: Fetching basic info...
09-28 14:16 DEBUG  CommonBackend: original_exe=E:\wubi.exe
09-28 14:16 DEBUG  CommonBackend: platform=win32
09-28 14:16 DEBUG  CommonBackend: osname=nt
09-28 14:16 DEBUG  CommonBackend: language=en_US
09-28 14:16 DEBUG  CommonBackend: encoding=cp1252
09-28 14:16 DEBUG  WindowsBackend: arch=amd64
09-28 14:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\data\isolist.ini
09-28 14:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 14:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 14:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 14:16 DEBUG  WindowsBackend: Fetching host info...
09-28 14:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 14:16 DEBUG  WindowsBackend: windows version=vista
09-28 14:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 14:16 DEBUG  WindowsBackend: windows_sp=None
09-28 14:16 DEBUG  WindowsBackend: windows_build=7601
09-28 14:16 DEBUG  WindowsBackend: gmt=-6
09-28 14:16 DEBUG  WindowsBackend: country=US
09-28 14:16 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 14:16 DEBUG  WindowsBackend: windows_username=Matt
09-28 14:16 DEBUG  WindowsBackend: user_full_name=Matt
09-28 14:16 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 14:16 DEBUG  WindowsBackend: windows_language_code=1033
09-28 14:16 DEBUG  WindowsBackend: windows_language=English
09-28 14:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 14:16 DEBUG  WindowsBackend: bootloader=vista
09-28 14:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95331.5273438 mb free ntfs)
09-28 14:16 DEBUG  WindowsBackend: drive=Drive(C: hd 95331.5273438 mb free ntfs)
09-28 14:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 14:16 DEBUG  WindowsBackend: drive=Drive(F: hd 337623.417969 mb free ntfs)
09-28 14:16 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 14:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 14:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 14:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 14:16 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 14:16 DEBUG  WindowsBackend: keyboard_layout=us
09-28 14:16 DEBUG  WindowsBackend: keyboard_variant=
09-28 14:16 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 14:16 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 14:16 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 14:16 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 14:16 DEBUG  CommonBackend: Searching for local CDs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Ubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Ubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Kubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Kubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Mythbuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Mythbuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Edubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Edubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Lubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Lubuntu CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Ubuntu Studio CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp is a valid Ubuntu Studio CD
09-28 14:16 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\casper\filesystem.squashfs
09-28 14:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 14:16 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 14:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 14:16 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 14:16 INFO   root: Running the CD menu...
09-28 14:16 DEBUG  WindowsFrontend: __init__...
09-28 14:16 DEBUG  WindowsFrontend: on_init...
09-28 14:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\translations, languages=['en_US', 'en']
09-28 14:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl4664.tmp\translations, languages=['en_US', 'en']
09-28 14:16 INFO   root: CD menu finished
09-28 14:16 INFO   root: Rebooting
09-28 14:16 DEBUG  TaskList: # Running tasklist...
09-28 14:16 DEBUG  TaskList: ## Running reboot...
09-28 14:16 DEBUG  TaskList: ## Finished reboot
09-28 14:16 DEBUG  TaskList: # Finished tasklist
09-28 14:16 DEBUG  root: application.quit
09-28 14:16 DEBUG  WindowsFrontend: frontend.quit
09-28 14:16 DEBUG  WindowsFrontend: frontend.on_quit
09-28 14:16 DEBUG  root: application.on_quit
09-28 14:16 INFO   root: sys.exit
09-28 14:59 INFO   root: === wubi 14.04 rev286 ===
09-28 14:59 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 14:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
09-28 14:59 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\data
09-28 14:59 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\bin\7z.exe
09-28 14:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 14:59 DEBUG  CommonBackend: Fetching basic info...
09-28 14:59 DEBUG  CommonBackend: original_exe=E:\wubi.exe
09-28 14:59 DEBUG  CommonBackend: platform=win32
09-28 14:59 DEBUG  CommonBackend: osname=nt
09-28 14:59 DEBUG  CommonBackend: language=en_US
09-28 14:59 DEBUG  CommonBackend: encoding=cp1252
09-28 14:59 DEBUG  WindowsBackend: arch=amd64
09-28 14:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\data\isolist.ini
09-28 14:59 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 14:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 14:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 14:59 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 14:59 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 14:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 14:59 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 14:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 14:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 14:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 14:59 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 14:59 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 14:59 DEBUG  WindowsBackend: Fetching host info...
09-28 14:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 14:59 DEBUG  WindowsBackend: windows version=vista
09-28 14:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 14:59 DEBUG  WindowsBackend: windows_sp=None
09-28 14:59 DEBUG  WindowsBackend: windows_build=7601
09-28 14:59 DEBUG  WindowsBackend: gmt=-6
09-28 14:59 DEBUG  WindowsBackend: country=US
09-28 14:59 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 14:59 DEBUG  WindowsBackend: windows_username=Matt
09-28 14:59 DEBUG  WindowsBackend: user_full_name=Matt
09-28 14:59 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 14:59 DEBUG  WindowsBackend: windows_language_code=1033
09-28 14:59 DEBUG  WindowsBackend: windows_language=English
09-28 14:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 14:59 DEBUG  WindowsBackend: bootloader=vista
09-28 14:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 96148.6289063 mb free ntfs)
09-28 14:59 DEBUG  WindowsBackend: drive=Drive(C: hd 96148.6289063 mb free ntfs)
09-28 14:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 14:59 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 14:59 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 14:59 DEBUG  WindowsBackend: drive=Drive(J: removable 1845.76171875 mb free fat32)
09-28 14:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 14:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 14:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 14:59 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 14:59 DEBUG  WindowsBackend: keyboard_layout=us
09-28 14:59 DEBUG  WindowsBackend: keyboard_variant=
09-28 14:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 14:59 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 14:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 14:59 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 14:59 DEBUG  Distro:   checking Ubuntu ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 14:59 DEBUG  WindowsBackend:   extracting .disk\info from J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 14:59 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 14:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 14:59 INFO   Distro: Found a valid iso for Ubuntu: J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 14:59 DEBUG  CommonBackend: Searching for local CDs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Ubuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Ubuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Kubuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Kubuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Mythbuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Mythbuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Edubuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Edubuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Lubuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Lubuntu CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Ubuntu Studio CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp is a valid Ubuntu Studio CD
09-28 14:59 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\casper\filesystem.squashfs
09-28 14:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 14:59 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 14:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 14:59 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 14:59 INFO   root: Running the CD menu...
09-28 14:59 DEBUG  WindowsFrontend: __init__...
09-28 14:59 DEBUG  WindowsFrontend: on_init...
09-28 14:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\translations, languages=['en_US', 'en']
09-28 14:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylF9D8.tmp\translations, languages=['en_US', 'en']
09-28 15:00 INFO   root: CD menu finished
09-28 15:00 DEBUG  CommonBackend: Showing info
09-28 15:00 DEBUG  root: application.quit
09-28 15:00 DEBUG  WindowsFrontend: frontend.quit
09-28 15:00 DEBUG  WindowsFrontend: frontend.on_quit
09-28 15:00 DEBUG  root: application.on_quit
09-28 15:00 INFO   root: sys.exit
09-28 15:01 INFO   root: === wubi 14.04 rev286 ===
09-28 15:01 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 15:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
09-28 15:01 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\data
09-28 15:01 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\bin\7z.exe
09-28 15:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 15:01 DEBUG  CommonBackend: Fetching basic info...
09-28 15:01 DEBUG  CommonBackend: original_exe=E:\wubi.exe
09-28 15:01 DEBUG  CommonBackend: platform=win32
09-28 15:01 DEBUG  CommonBackend: osname=nt
09-28 15:01 DEBUG  CommonBackend: language=en_US
09-28 15:01 DEBUG  CommonBackend: encoding=cp1252
09-28 15:01 DEBUG  WindowsBackend: arch=amd64
09-28 15:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\data\isolist.ini
09-28 15:01 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:01 DEBUG  WindowsBackend: Fetching host info...
09-28 15:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:01 DEBUG  WindowsBackend: windows version=vista
09-28 15:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:01 DEBUG  WindowsBackend: windows_sp=None
09-28 15:01 DEBUG  WindowsBackend: windows_build=7601
09-28 15:01 DEBUG  WindowsBackend: gmt=-6
09-28 15:01 DEBUG  WindowsBackend: country=US
09-28 15:01 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:01 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:01 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:01 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:01 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:01 DEBUG  WindowsBackend: windows_language=English
09-28 15:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:01 DEBUG  WindowsBackend: bootloader=vista
09-28 15:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 96147.3359375 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(C: hd 96147.3359375 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(J: removable 1845.76171875 mb free fat32)
09-28 15:01 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 15:01 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 15:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 15:01 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:01 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:01 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 15:01 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 15:01 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:01 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:01 DEBUG  Distro:   checking Ubuntu ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  WindowsBackend:   extracting .disk\info from J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:01 INFO   Distro: Found a valid iso for Ubuntu: J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  CommonBackend: Searching for local CDs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Kubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Kubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Mythbuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Mythbuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Edubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Edubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Lubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Lubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Ubuntu Studio CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp is a valid Ubuntu Studio CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:01 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:01 INFO   root: Running the CD menu...
09-28 15:01 DEBUG  WindowsFrontend: __init__...
09-28 15:01 DEBUG  WindowsFrontend: on_init...
09-28 15:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\translations, languages=['en_US', 'en']
09-28 15:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl5530.tmp\translations, languages=['en_US', 'en']
09-28 15:01 INFO   WindowsFrontend: Operation cancelled
09-28 15:01 DEBUG  WindowsFrontend: frontend.quit
09-28 15:01 DEBUG  WindowsFrontend: frontend.on_quit
09-28 15:01 DEBUG  root: application.on_quit
09-28 15:01 INFO   root: sys.exit
09-28 15:01 INFO   root: === wubi 14.04 rev286 ===
09-28 15:01 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 15:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
09-28 15:01 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\data
09-28 15:01 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\bin\7z.exe
09-28 15:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 15:01 DEBUG  CommonBackend: Fetching basic info...
09-28 15:01 DEBUG  CommonBackend: original_exe=E:\wubi.exe
09-28 15:01 DEBUG  CommonBackend: platform=win32
09-28 15:01 DEBUG  CommonBackend: osname=nt
09-28 15:01 DEBUG  CommonBackend: language=en_US
09-28 15:01 DEBUG  CommonBackend: encoding=cp1252
09-28 15:01 DEBUG  WindowsBackend: arch=amd64
09-28 15:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\data\isolist.ini
09-28 15:01 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:01 DEBUG  WindowsBackend: Fetching host info...
09-28 15:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:01 DEBUG  WindowsBackend: windows version=vista
09-28 15:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:01 DEBUG  WindowsBackend: windows_sp=None
09-28 15:01 DEBUG  WindowsBackend: windows_build=7601
09-28 15:01 DEBUG  WindowsBackend: gmt=-6
09-28 15:01 DEBUG  WindowsBackend: country=US
09-28 15:01 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:01 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:01 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:01 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:01 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:01 DEBUG  WindowsBackend: windows_language=English
09-28 15:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:01 DEBUG  WindowsBackend: bootloader=vista
09-28 15:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 96147.28125 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(C: hd 96147.28125 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(J: removable 1845.76171875 mb free fat32)
09-28 15:01 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 15:01 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 15:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 15:01 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:01 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:01 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 15:01 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 15:01 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:01 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:01 DEBUG  Distro:   checking Ubuntu ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  WindowsBackend:   extracting .disk\info from J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:01 INFO   Distro: Found a valid iso for Ubuntu: J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  CommonBackend: Searching for local CDs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Kubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Kubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Mythbuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Mythbuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Edubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Edubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Lubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Lubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Ubuntu Studio CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylE291.tmp is a valid Ubuntu Studio CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:01 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:01 INFO   root: Running the CD menu...
09-28 15:01 DEBUG  WindowsFrontend: __init__...
09-28 15:01 DEBUG  WindowsFrontend: on_init...
09-28 15:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\translations, languages=['en_US', 'en']
09-28 15:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylE291.tmp\translations, languages=['en_US', 'en']
09-28 15:01 INFO   WindowsFrontend: Operation cancelled
09-28 15:01 DEBUG  WindowsFrontend: frontend.quit
09-28 15:01 DEBUG  WindowsFrontend: frontend.on_quit
09-28 15:01 DEBUG  root: application.on_quit
09-28 15:01 INFO   root: sys.exit
09-28 15:01 INFO   root: === wubi 14.04 rev286 ===
09-28 15:01 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 15:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Matt\\Downloads\\ubuntu-14.04.1-desktop-amd64\\wubi.exe"']
09-28 15:01 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\data
09-28 15:01 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\bin\7z.exe
09-28 15:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 15:01 DEBUG  CommonBackend: Fetching basic info...
09-28 15:01 DEBUG  CommonBackend: original_exe=C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe
09-28 15:01 DEBUG  CommonBackend: platform=win32
09-28 15:01 DEBUG  CommonBackend: osname=nt
09-28 15:01 DEBUG  CommonBackend: language=en_US
09-28 15:01 DEBUG  CommonBackend: encoding=cp1252
09-28 15:01 DEBUG  WindowsBackend: arch=amd64
09-28 15:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\data\isolist.ini
09-28 15:01 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:01 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:01 DEBUG  WindowsBackend: Fetching host info...
09-28 15:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:01 DEBUG  WindowsBackend: windows version=vista
09-28 15:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:01 DEBUG  WindowsBackend: windows_sp=None
09-28 15:01 DEBUG  WindowsBackend: windows_build=7601
09-28 15:01 DEBUG  WindowsBackend: gmt=-6
09-28 15:01 DEBUG  WindowsBackend: country=US
09-28 15:01 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:01 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:01 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:01 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:01 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:01 DEBUG  WindowsBackend: windows_language=English
09-28 15:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:01 DEBUG  WindowsBackend: bootloader=vista
09-28 15:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 96146.7265625 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(C: hd 96146.7265625 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: drive=Drive(J: removable 1845.76171875 mb free fat32)
09-28 15:01 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 15:01 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 15:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 15:01 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:01 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:01 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 15:01 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 15:01 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:01 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:01 DEBUG  Distro:   checking Ubuntu ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  WindowsBackend:   extracting .disk\info from J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:01 INFO   Distro: Found a valid iso for Ubuntu: J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:01 DEBUG  CommonBackend: Searching for local CDs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Kubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Kubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Mythbuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Mythbuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Edubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Edubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Lubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Lubuntu CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu Studio CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu Studio CD
09-28 15:01 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:01 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:01 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:01 INFO   root: Already installed, running the uninstaller...
09-28 15:01 INFO   root: Running the uninstaller...
09-28 15:01 INFO   CommonBackend: This is the uninstaller running
09-28 15:01 DEBUG  WindowsFrontend: __init__...
09-28 15:01 DEBUG  WindowsFrontend: on_init...
09-28 15:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\translations, languages=['en_US', 'en']
09-28 15:01 INFO   root: Received settings
09-28 15:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\translations, languages=['en_US', 'en']
09-28 15:01 DEBUG  TaskList: # Running tasklist...
09-28 15:01 DEBUG  TaskList: ## Running Remove bootloader entry...
09-28 15:01 DEBUG  WindowsBackend: Could not find bcd id
09-28 15:01 DEBUG  WindowsBackend: undo_bootini C:
09-28 15:01 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 96146.7265625 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: undo_bootini F:
09-28 15:01 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: undo_bootini I:
09-28 15:01 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:01 DEBUG  WindowsBackend: undo_bootini J:
09-28 15:01 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 1845.76171875 mb free fat32)
09-28 15:01 DEBUG  TaskList: ## Finished Remove bootloader entry
09-28 15:01 DEBUG  TaskList: ## Running Remove target dir...
09-28 15:01 DEBUG  CommonBackend: Deleting C:\ubuntu
09-28 15:02 DEBUG  TaskList: ## Finished Remove target dir
09-28 15:02 DEBUG  TaskList: ## Running Remove registry key...
09-28 15:02 DEBUG  TaskList: ## Finished Remove registry key
09-28 15:02 DEBUG  TaskList: # Finished tasklist
09-28 15:02 INFO   root: Almost finished uninstalling
09-28 15:02 INFO   root: Finished uninstallation
09-28 15:02 DEBUG  CommonBackend: Fetching basic info...
09-28 15:02 DEBUG  CommonBackend: original_exe=C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe
09-28 15:02 DEBUG  CommonBackend: platform=win32
09-28 15:02 DEBUG  CommonBackend: osname=nt
09-28 15:02 DEBUG  WindowsBackend: arch=amd64
09-28 15:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\data\isolist.ini
09-28 15:02 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:02 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:02 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:02 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:02 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:02 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:02 DEBUG  WindowsBackend: Fetching host info...
09-28 15:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:02 DEBUG  WindowsBackend: windows version=vista
09-28 15:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:02 DEBUG  WindowsBackend: windows_sp=None
09-28 15:02 DEBUG  WindowsBackend: windows_build=7601
09-28 15:02 DEBUG  WindowsBackend: gmt=-6
09-28 15:02 DEBUG  WindowsBackend: country=US
09-28 15:02 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:02 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:02 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:02 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:02 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:02 DEBUG  WindowsBackend: windows_language=English
09-28 15:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:02 DEBUG  WindowsBackend: bootloader=vista
09-28 15:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 97113.2226563 mb free ntfs)
09-28 15:02 DEBUG  WindowsBackend: drive=Drive(C: hd 97113.2226563 mb free ntfs)
09-28 15:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 15:02 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:02 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:02 DEBUG  WindowsBackend: drive=Drive(J: removable 1845.76171875 mb free fat32)
09-28 15:02 DEBUG  WindowsBackend: uninstaller_path=None
09-28 15:02 DEBUG  WindowsBackend: previous_target_dir=None
09-28 15:02 DEBUG  WindowsBackend: previous_distro_name=None
09-28 15:02 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:02 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:02 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:02 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:02 DEBUG  CommonBackend: Checking pre-specified ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 DEBUG  Distro:   checking Ubuntu ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 INFO   Distro: Found a valid iso for Ubuntu: J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 DEBUG  CommonBackend: Searching for local CDs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Kubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Kubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Mythbuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Mythbuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Edubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Edubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Lubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Lubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu Studio CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu Studio CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:02 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:02 INFO   root: Running the installer...
09-28 15:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\translations, languages=['en_US', 'en']
09-28 15:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\translations, languages=['en_US', 'en']
09-28 15:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=matt
09-28 15:02 INFO   root: Received settings
09-28 15:02 DEBUG  CommonBackend: Searching for local CD
09-28 15:02 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp is a valid Ubuntu CD
09-28 15:02 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\casper\filesystem.squashfs
09-28 15:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:02 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\translations, languages=['en_US', 'en']
09-28 15:02 DEBUG  TaskList: # Running tasklist...
09-28 15:02 DEBUG  TaskList: ## Running select_target_dir...
09-28 15:02 INFO   WindowsBackend: Installing into C:\ubuntu
09-28 15:02 DEBUG  TaskList: ## Finished select_target_dir
09-28 15:02 DEBUG  TaskList: ## Running create_dir_structure...
09-28 15:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-28 15:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-28 15:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-28 15:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-28 15:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-28 15:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-28 15:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-28 15:02 DEBUG  TaskList: ## Finished create_dir_structure
09-28 15:02 DEBUG  TaskList: ## Running uncompress_target_dir...
09-28 15:02 DEBUG  TaskList: ## Finished uncompress_target_dir
09-28 15:02 DEBUG  TaskList: ## Running create_uninstaller...
09-28 15:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-28 15:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-28 15:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-28 15:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-28 15:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-28 15:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
09-28 15:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-28 15:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-28 15:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-28 15:02 DEBUG  TaskList: ## Finished create_uninstaller
09-28 15:02 DEBUG  TaskList: ## Running copy_installation_files...
09-28 15:02 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-28 15:02 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\winboot -> C:\ubuntu\winboot
09-28 15:02 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pylCAC.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-28 15:02 DEBUG  TaskList: ## Finished copy_installation_files
09-28 15:02 DEBUG  TaskList: ## Running get_iso...
09-28 15:02 DEBUG  CommonBackend: Trying to use pre-specified ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 DEBUG  TaskList: New task is_valid_iso
09-28 15:02 DEBUG  TaskList: ### Running is_valid_iso...
09-28 15:02 DEBUG  Distro:   checking Ubuntu ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 INFO   Distro: Found a valid iso for Ubuntu: J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 DEBUG  TaskList: ### Finished is_valid_iso
09-28 15:02 DEBUG  TaskList: New task check_iso
09-28 15:02 DEBUG  TaskList: ### Running check_iso...
09-28 15:02 DEBUG  CommonBackend: Checking J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 DEBUG  Distro:   checking Ubuntu ISO J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 INFO   Distro: Found a valid iso for Ubuntu: J:\ubuntu-14.04.1-desktop-amd64.iso
09-28 15:02 DEBUG  TaskList: New task get_metalink
09-28 15:02 DEBUG  TaskList: #### Running get_metalink...
09-28 15:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
09-28 15:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-28 15:02 DEBUG  downloader: download finished (read 45848 bytes)
09-28 15:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-28 15:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
09-28 15:02 DEBUG  downloader: download finished (read 560 bytes)
09-28 15:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-28 15:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-28 15:02 DEBUG  downloader: download finished (read 198 bytes)
09-28 15:02 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-28 15:02 INFO   saplog: Checking block bindings..
09-28 15:02 INFO   saplog: Key verified successfully.
09-28 15:02 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink

09-28 15:02 ERROR  CommonBackend: The md5 of the metalink does match
09-28 15:02 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-28 15:02 DEBUG  TaskList: #### Finished get_metalink
09-28 15:02 DEBUG  TaskList: New task get_file_md5
09-28 15:02 DEBUG  TaskList: #### Running get_file_md5...
09-28 15:03 DEBUG  TaskList: #### Finished get_file_md5
09-28 15:03 ERROR  CommonBackend: Invalid md5 for ISO J:\ubuntu-14.04.1-desktop-amd64.iso (dccff28314d9ae4ed262cfc6f35e5153 != 119cb63b48c9a18f31f417f09655efbd)
None
09-28 15:03 DEBUG  TaskList: ### Finished check_iso
09-28 15:03 DEBUG  TaskList: New task copy_file
09-28 15:03 DEBUG  TaskList: ### Running copy_file...
09-28 15:04 DEBUG  TaskList: ### Finished copy_file
09-28 15:04 DEBUG  TaskList: New task check_iso
09-28 15:04 DEBUG  TaskList: ### Running check_iso...
09-28 15:04 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
09-28 15:04 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
09-28 15:04 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
09-28 15:04 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:04 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
09-28 15:04 DEBUG  TaskList: New task get_file_md5
09-28 15:04 DEBUG  TaskList: #### Running get_file_md5...
09-28 15:04 DEBUG  TaskList: #### Finished get_file_md5
09-28 15:04 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dccff28314d9ae4ed262cfc6f35e5153 != 119cb63b48c9a18f31f417f09655efbd)
None
09-28 15:04 DEBUG  TaskList: ### Finished check_iso
09-28 15:04 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
09-28 15:04 DEBUG  TaskList: # Cancelling tasklist
09-28 15:04 DEBUG  TaskList: # Finished tasklist
09-28 15:04 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
09-28 15:29 INFO   root: === wubi 14.04 rev286 ===
09-28 15:29 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 15:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Matt\\Downloads\\ubuntu-14.04.1-desktop-amd64\\wubi.exe"']
09-28 15:29 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\data
09-28 15:29 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\bin\7z.exe
09-28 15:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 15:29 DEBUG  CommonBackend: Fetching basic info...
09-28 15:29 DEBUG  CommonBackend: original_exe=C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe
09-28 15:29 DEBUG  CommonBackend: platform=win32
09-28 15:29 DEBUG  CommonBackend: osname=nt
09-28 15:29 DEBUG  CommonBackend: language=en_US
09-28 15:29 DEBUG  CommonBackend: encoding=cp1252
09-28 15:29 DEBUG  WindowsBackend: arch=amd64
09-28 15:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\data\isolist.ini
09-28 15:29 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:29 DEBUG  WindowsBackend: Fetching host info...
09-28 15:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:29 DEBUG  WindowsBackend: windows version=vista
09-28 15:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:29 DEBUG  WindowsBackend: windows_sp=None
09-28 15:29 DEBUG  WindowsBackend: windows_build=7601
09-28 15:29 DEBUG  WindowsBackend: gmt=-6
09-28 15:29 DEBUG  WindowsBackend: country=US
09-28 15:29 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:29 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:29 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:29 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:29 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:29 DEBUG  WindowsBackend: windows_language=English
09-28 15:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:29 DEBUG  WindowsBackend: bootloader=vista
09-28 15:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 96128.6757813 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(C: hd 96128.671875 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 15:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 15:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 15:29 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:29 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:29 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 15:29 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 15:29 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:29 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:29 DEBUG  CommonBackend: Searching for local CDs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Kubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Kubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Mythbuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Mythbuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Edubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Edubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Lubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Lubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu Studio CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu Studio CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:29 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:29 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:29 INFO   root: Already installed, running the uninstaller...
09-28 15:29 INFO   root: Running the uninstaller...
09-28 15:29 INFO   CommonBackend: This is the uninstaller running
09-28 15:29 DEBUG  WindowsFrontend: __init__...
09-28 15:29 DEBUG  WindowsFrontend: on_init...
09-28 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\translations, languages=['en_US', 'en']
09-28 15:29 INFO   root: Received settings
09-28 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\translations, languages=['en_US', 'en']
09-28 15:29 DEBUG  TaskList: # Running tasklist...
09-28 15:29 DEBUG  TaskList: ## Running Remove bootloader entry...
09-28 15:29 DEBUG  WindowsBackend: Could not find bcd id
09-28 15:29 DEBUG  WindowsBackend: undo_bootini C:
09-28 15:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 96128.671875 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: undo_bootini F:
09-28 15:29 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: undo_bootini I:
09-28 15:29 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: undo_bootini J:
09-28 15:29 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:29 DEBUG  TaskList: ## Finished Remove bootloader entry
09-28 15:29 DEBUG  TaskList: ## Running Remove target dir...
09-28 15:29 DEBUG  CommonBackend: Deleting C:\ubuntu
09-28 15:29 DEBUG  TaskList: ## Finished Remove target dir
09-28 15:29 DEBUG  TaskList: ## Running Remove registry key...
09-28 15:29 DEBUG  TaskList: ## Finished Remove registry key
09-28 15:29 DEBUG  TaskList: # Finished tasklist
09-28 15:29 INFO   root: Almost finished uninstalling
09-28 15:29 INFO   root: Finished uninstallation
09-28 15:29 DEBUG  CommonBackend: Fetching basic info...
09-28 15:29 DEBUG  CommonBackend: original_exe=C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe
09-28 15:29 DEBUG  CommonBackend: platform=win32
09-28 15:29 DEBUG  CommonBackend: osname=nt
09-28 15:29 DEBUG  WindowsBackend: arch=amd64
09-28 15:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\data\isolist.ini
09-28 15:29 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:29 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:29 DEBUG  WindowsBackend: Fetching host info...
09-28 15:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:29 DEBUG  WindowsBackend: windows version=vista
09-28 15:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:29 DEBUG  WindowsBackend: windows_sp=None
09-28 15:29 DEBUG  WindowsBackend: windows_build=7601
09-28 15:29 DEBUG  WindowsBackend: gmt=-6
09-28 15:29 DEBUG  WindowsBackend: country=US
09-28 15:29 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:29 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:29 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:29 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:29 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:29 DEBUG  WindowsBackend: windows_language=English
09-28 15:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:29 DEBUG  WindowsBackend: bootloader=vista
09-28 15:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 97112.359375 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(C: hd 97112.359375 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:29 DEBUG  WindowsBackend: drive=Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:29 DEBUG  WindowsBackend: uninstaller_path=None
09-28 15:29 DEBUG  WindowsBackend: previous_target_dir=None
09-28 15:29 DEBUG  WindowsBackend: previous_distro_name=None
09-28 15:29 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:29 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:29 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:29 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:29 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:29 DEBUG  CommonBackend: Searching for local CDs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Kubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Kubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Mythbuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Mythbuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Edubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Edubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Lubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Lubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu Studio CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu Studio CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:29 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:29 INFO   root: Running the installer...
09-28 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\translations, languages=['en_US', 'en']
09-28 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\translations, languages=['en_US', 'en']
09-28 15:29 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=25000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=matt
09-28 15:29 INFO   root: Received settings
09-28 15:29 DEBUG  CommonBackend: Searching for local CD
09-28 15:29 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp is a valid Ubuntu CD
09-28 15:29 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\casper\filesystem.squashfs
09-28 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:29 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\translations, languages=['en_US', 'en']
09-28 15:29 DEBUG  TaskList: # Running tasklist...
09-28 15:29 DEBUG  TaskList: ## Running select_target_dir...
09-28 15:29 INFO   WindowsBackend: Installing into C:\ubuntu
09-28 15:29 DEBUG  TaskList: ## Finished select_target_dir
09-28 15:29 DEBUG  TaskList: ## Running create_dir_structure...
09-28 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-28 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-28 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-28 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-28 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-28 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-28 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-28 15:29 DEBUG  TaskList: ## Finished create_dir_structure
09-28 15:29 DEBUG  TaskList: ## Running uncompress_target_dir...
09-28 15:29 DEBUG  TaskList: ## Finished uncompress_target_dir
09-28 15:29 DEBUG  TaskList: ## Running create_uninstaller...
09-28 15:29 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-28 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-28 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-28 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-28 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-28 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
09-28 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-28 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-28 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-28 15:29 DEBUG  TaskList: ## Finished create_uninstaller
09-28 15:29 DEBUG  TaskList: ## Running copy_installation_files...
09-28 15:29 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-28 15:29 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\winboot -> C:\ubuntu\winboot
09-28 15:29 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl1DEB.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-28 15:29 DEBUG  TaskList: ## Finished copy_installation_files
09-28 15:29 DEBUG  TaskList: ## Running get_iso...
09-28 15:29 DEBUG  TaskList: New task copy_file
09-28 15:29 DEBUG  TaskList: ### Running copy_file...
09-28 15:30 INFO   WindowsFrontend: Operation cancelled
09-28 15:30 DEBUG  WindowsFrontend: frontend.quit
09-28 15:30 DEBUG  WindowsFrontend: frontend.on_quit
09-28 15:30 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-28 15:30 DEBUG  TaskList: # Cancelling tasklist
09-28 15:30 DEBUG  TaskList: ### Finished copy_file
09-28 15:30 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-28 15:30 DEBUG  root: application.on_quit
09-28 15:30 DEBUG  root: Forceful exit
09-28 15:30 INFO   root: sys.exit
09-28 15:30 INFO   root: === wubi 14.04 rev286 ===
09-28 15:30 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 15:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Matt\\Downloads\\ubuntu-14.04.1-desktop-amd64\\wubi.exe"']
09-28 15:30 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\data
09-28 15:30 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\bin\7z.exe
09-28 15:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 15:30 DEBUG  CommonBackend: Fetching basic info...
09-28 15:30 DEBUG  CommonBackend: original_exe=C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe
09-28 15:30 DEBUG  CommonBackend: platform=win32
09-28 15:30 DEBUG  CommonBackend: osname=nt
09-28 15:30 DEBUG  CommonBackend: language=en_US
09-28 15:30 DEBUG  CommonBackend: encoding=cp1252
09-28 15:30 DEBUG  WindowsBackend: arch=amd64
09-28 15:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\data\isolist.ini
09-28 15:30 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:30 DEBUG  WindowsBackend: Fetching host info...
09-28 15:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:30 DEBUG  WindowsBackend: windows version=vista
09-28 15:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:30 DEBUG  WindowsBackend: windows_sp=None
09-28 15:30 DEBUG  WindowsBackend: windows_build=7601
09-28 15:30 DEBUG  WindowsBackend: gmt=-6
09-28 15:30 DEBUG  WindowsBackend: country=US
09-28 15:30 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:30 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:30 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:30 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:30 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:30 DEBUG  WindowsBackend: windows_language=English
09-28 15:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:30 DEBUG  WindowsBackend: bootloader=vista
09-28 15:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 96271.234375 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(C: hd 96271.234375 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 15:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 15:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 15:30 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:30 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:30 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 15:30 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 15:30 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:30 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:30 DEBUG  CommonBackend: Searching for local CDs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Kubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Kubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Mythbuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Mythbuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Edubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Edubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Lubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Lubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu Studio CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu Studio CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:30 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:30 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:30 INFO   root: Already installed, running the uninstaller...
09-28 15:30 INFO   root: Running the uninstaller...
09-28 15:30 INFO   CommonBackend: This is the uninstaller running
09-28 15:30 DEBUG  WindowsFrontend: __init__...
09-28 15:30 DEBUG  WindowsFrontend: on_init...
09-28 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\translations, languages=['en_US', 'en']
09-28 15:30 INFO   root: Received settings
09-28 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\translations, languages=['en_US', 'en']
09-28 15:30 DEBUG  TaskList: # Running tasklist...
09-28 15:30 DEBUG  TaskList: ## Running Remove bootloader entry...
09-28 15:30 DEBUG  WindowsBackend: Could not find bcd id
09-28 15:30 DEBUG  WindowsBackend: undo_bootini C:
09-28 15:30 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 96271.234375 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: undo_bootini F:
09-28 15:30 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: undo_bootini I:
09-28 15:30 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: undo_bootini J:
09-28 15:30 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:30 DEBUG  TaskList: ## Finished Remove bootloader entry
09-28 15:30 DEBUG  TaskList: ## Running Remove target dir...
09-28 15:30 DEBUG  CommonBackend: Deleting C:\ubuntu
09-28 15:30 DEBUG  TaskList: ## Finished Remove target dir
09-28 15:30 DEBUG  TaskList: ## Running Remove registry key...
09-28 15:30 DEBUG  TaskList: ## Finished Remove registry key
09-28 15:30 DEBUG  TaskList: # Finished tasklist
09-28 15:30 INFO   root: Almost finished uninstalling
09-28 15:30 INFO   root: Finished uninstallation
09-28 15:30 DEBUG  CommonBackend: Fetching basic info...
09-28 15:30 DEBUG  CommonBackend: original_exe=C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe
09-28 15:30 DEBUG  CommonBackend: platform=win32
09-28 15:30 DEBUG  CommonBackend: osname=nt
09-28 15:30 DEBUG  WindowsBackend: arch=amd64
09-28 15:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\data\isolist.ini
09-28 15:30 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:30 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:30 DEBUG  WindowsBackend: Fetching host info...
09-28 15:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:30 DEBUG  WindowsBackend: windows version=vista
09-28 15:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:30 DEBUG  WindowsBackend: windows_sp=None
09-28 15:30 DEBUG  WindowsBackend: windows_build=7601
09-28 15:30 DEBUG  WindowsBackend: gmt=-6
09-28 15:30 DEBUG  WindowsBackend: country=US
09-28 15:30 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:30 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:30 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:30 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:30 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:30 DEBUG  WindowsBackend: windows_language=English
09-28 15:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:30 DEBUG  WindowsBackend: bootloader=vista
09-28 15:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 96983.859375 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(C: hd 96983.859375 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:30 DEBUG  WindowsBackend: drive=Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:30 DEBUG  WindowsBackend: uninstaller_path=None
09-28 15:30 DEBUG  WindowsBackend: previous_target_dir=None
09-28 15:30 DEBUG  WindowsBackend: previous_distro_name=None
09-28 15:30 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:30 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:30 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:30 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:30 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:30 DEBUG  CommonBackend: Searching for local CDs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Kubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Kubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Mythbuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Mythbuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Edubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Edubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Lubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Lubuntu CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu Studio CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu Studio CD
09-28 15:30 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:30 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:30 INFO   root: Running the installer...
09-28 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\translations, languages=['en_US', 'en']
09-28 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\translations, languages=['en_US', 'en']
09-28 15:31 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=matt
09-28 15:31 INFO   root: Received settings
09-28 15:31 DEBUG  CommonBackend: Searching for local CD
09-28 15:31 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp is a valid Ubuntu CD
09-28 15:31 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\casper\filesystem.squashfs
09-28 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:31 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-28 15:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\translations, languages=['en_US', 'en']
09-28 15:31 DEBUG  TaskList: # Running tasklist...
09-28 15:31 DEBUG  TaskList: ## Running select_target_dir...
09-28 15:31 INFO   WindowsBackend: Installing into C:\ubuntu
09-28 15:31 DEBUG  TaskList: ## Finished select_target_dir
09-28 15:31 DEBUG  TaskList: ## Running create_dir_structure...
09-28 15:31 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-28 15:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-28 15:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-28 15:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-28 15:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-28 15:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-28 15:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-28 15:31 DEBUG  TaskList: ## Finished create_dir_structure
09-28 15:31 DEBUG  TaskList: ## Running uncompress_target_dir...
09-28 15:31 DEBUG  TaskList: ## Finished uncompress_target_dir
09-28 15:31 DEBUG  TaskList: ## Running create_uninstaller...
09-28 15:31 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-28 15:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-28 15:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-28 15:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-28 15:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-28 15:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
09-28 15:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-28 15:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-28 15:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-28 15:31 DEBUG  TaskList: ## Finished create_uninstaller
09-28 15:31 DEBUG  TaskList: ## Running copy_installation_files...
09-28 15:31 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-28 15:31 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\winboot -> C:\ubuntu\winboot
09-28 15:31 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl2F49.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-28 15:31 DEBUG  TaskList: ## Finished copy_installation_files
09-28 15:31 DEBUG  TaskList: ## Running get_iso...
09-28 15:31 DEBUG  TaskList: New task copy_file
09-28 15:31 DEBUG  TaskList: ### Running copy_file...
09-28 15:31 DEBUG  TaskList: ### Finished copy_file
09-28 15:31 DEBUG  TaskList: New task check_iso
09-28 15:31 DEBUG  TaskList: ### Running check_iso...
09-28 15:31 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
09-28 15:31 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
09-28 15:31 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
09-28 15:31 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:31 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
09-28 15:31 DEBUG  TaskList: New task get_metalink
09-28 15:31 DEBUG  TaskList: #### Running get_metalink...
09-28 15:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
09-28 15:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-28 15:31 DEBUG  downloader: download finished (read 45848 bytes)
09-28 15:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-28 15:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
09-28 15:31 DEBUG  downloader: download finished (read 560 bytes)
09-28 15:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-28 15:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-28 15:31 DEBUG  downloader: download finished (read 198 bytes)
09-28 15:31 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-28 15:31 INFO   saplog: Checking block bindings..
09-28 15:31 INFO   saplog: Key verified successfully.
09-28 15:31 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink

09-28 15:31 ERROR  CommonBackend: The md5 of the metalink does match
09-28 15:31 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-28 15:31 DEBUG  TaskList: #### Finished get_metalink
09-28 15:31 DEBUG  TaskList: New task get_file_md5
09-28 15:31 DEBUG  TaskList: #### Running get_file_md5...
09-28 15:32 DEBUG  TaskList: #### Finished get_file_md5
09-28 15:32 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dccff28314d9ae4ed262cfc6f35e5153 != 119cb63b48c9a18f31f417f09655efbd)
None
09-28 15:32 DEBUG  TaskList: ### Finished check_iso
09-28 15:32 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
09-28 15:32 DEBUG  TaskList: # Cancelling tasklist
09-28 15:32 DEBUG  TaskList: # Finished tasklist
09-28 15:32 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
09-28 15:35 INFO   root: === wubi 14.04 rev286 ===
09-28 15:35 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 15:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
09-28 15:35 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\data
09-28 15:35 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\bin\7z.exe
09-28 15:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 15:35 DEBUG  CommonBackend: Fetching basic info...
09-28 15:35 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
09-28 15:35 DEBUG  CommonBackend: platform=win32
09-28 15:35 DEBUG  CommonBackend: osname=nt
09-28 15:35 DEBUG  CommonBackend: language=en_US
09-28 15:35 DEBUG  CommonBackend: encoding=cp1252
09-28 15:35 DEBUG  WindowsBackend: arch=amd64
09-28 15:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\data\isolist.ini
09-28 15:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:35 DEBUG  WindowsBackend: Fetching host info...
09-28 15:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:35 DEBUG  WindowsBackend: windows version=vista
09-28 15:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:35 DEBUG  WindowsBackend: windows_sp=None
09-28 15:35 DEBUG  WindowsBackend: windows_build=7601
09-28 15:35 DEBUG  WindowsBackend: gmt=-6
09-28 15:35 DEBUG  WindowsBackend: country=US
09-28 15:35 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:35 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:35 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:35 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:35 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:35 DEBUG  WindowsBackend: windows_language=English
09-28 15:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:35 DEBUG  WindowsBackend: bootloader=vista
09-28 15:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95524.765625 mb free ntfs)
09-28 15:35 DEBUG  WindowsBackend: drive=Drive(C: hd 95524.765625 mb free ntfs)
09-28 15:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-28 15:35 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:35 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:35 DEBUG  WindowsBackend: drive=Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:35 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-28 15:35 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-28 15:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-28 15:35 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:35 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:35 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 15:35 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 15:35 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:35 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:35 DEBUG  CommonBackend: Searching for local CDs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Kubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Kubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Mythbuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Mythbuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Edubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Edubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Lubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Lubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Ubuntu Studio CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp is a valid Ubuntu Studio CD
09-28 15:35 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-28 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
09-28 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
09-28 15:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:35 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-28 15:35 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:35 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-28 15:35 INFO   root: Running the uninstaller...
09-28 15:35 INFO   CommonBackend: This is the uninstaller running
09-28 15:35 DEBUG  WindowsFrontend: __init__...
09-28 15:35 DEBUG  WindowsFrontend: on_init...
09-28 15:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\translations, languages=['en_US', 'en']
09-28 15:35 INFO   root: Received settings
09-28 15:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\translations, languages=['en_US', 'en']
09-28 15:35 DEBUG  TaskList: # Running tasklist...
09-28 15:35 DEBUG  TaskList: ## Running Remove bootloader entry...
09-28 15:35 DEBUG  WindowsBackend: Could not find bcd id
09-28 15:35 DEBUG  WindowsBackend: undo_bootini C:
09-28 15:35 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 95524.765625 mb free ntfs)
09-28 15:36 DEBUG  WindowsBackend: undo_bootini F:
09-28 15:36 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:36 DEBUG  WindowsBackend: undo_bootini I:
09-28 15:36 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:36 DEBUG  WindowsBackend: undo_bootini J:
09-28 15:36 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:36 DEBUG  TaskList: ## Finished Remove bootloader entry
09-28 15:36 DEBUG  TaskList: ## Running Remove target dir...
09-28 15:36 DEBUG  CommonBackend: Deleting C:\ubuntu
09-28 15:36 DEBUG  TaskList: ## Finished Remove target dir
09-28 15:36 DEBUG  TaskList: ## Running Remove registry key...
09-28 15:36 DEBUG  TaskList: ## Finished Remove registry key
09-28 15:36 DEBUG  TaskList: # Finished tasklist
09-28 15:36 INFO   root: Almost finished uninstalling
09-28 15:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl2348.tmp\translations, languages=['en_US', 'en']
09-28 15:36 INFO   root: Finished uninstallation
09-28 15:36 DEBUG  root: application.quit
09-28 15:36 DEBUG  WindowsFrontend: frontend.quit
09-28 15:36 DEBUG  WindowsFrontend: frontend.on_quit
09-28 15:36 DEBUG  root: application.on_quit
09-28 15:36 INFO   root: sys.exit
09-28 15:57 INFO   root: === wubi 14.04 rev286 ===
09-28 15:57 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 15:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Matt\\Downloads\\ubuntu-14.04.1-desktop-amd64\\wubi.exe"']
09-28 15:57 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\data
09-28 15:57 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\bin\7z.exe
09-28 15:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 15:57 DEBUG  CommonBackend: Fetching basic info...
09-28 15:57 DEBUG  CommonBackend: original_exe=C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe
09-28 15:57 DEBUG  CommonBackend: platform=win32
09-28 15:57 DEBUG  CommonBackend: osname=nt
09-28 15:57 DEBUG  CommonBackend: language=en_US
09-28 15:57 DEBUG  CommonBackend: encoding=cp1252
09-28 15:57 DEBUG  WindowsBackend: arch=amd64
09-28 15:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\data\isolist.ini
09-28 15:57 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:57 DEBUG  WindowsBackend: Fetching host info...
09-28 15:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:57 DEBUG  WindowsBackend: windows version=vista
09-28 15:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:57 DEBUG  WindowsBackend: windows_sp=None
09-28 15:57 DEBUG  WindowsBackend: windows_build=7601
09-28 15:57 DEBUG  WindowsBackend: gmt=-6
09-28 15:57 DEBUG  WindowsBackend: country=US
09-28 15:57 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:57 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:57 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:57 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:57 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:57 DEBUG  WindowsBackend: windows_language=English
09-28 15:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:57 DEBUG  WindowsBackend: bootloader=vista
09-28 15:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 93382.359375 mb free ntfs)
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(C: hd 93382.359375 mb free ntfs)
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:57 DEBUG  WindowsBackend: uninstaller_path=None
09-28 15:57 DEBUG  WindowsBackend: previous_target_dir=None
09-28 15:57 DEBUG  WindowsBackend: previous_distro_name=None
09-28 15:57 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:57 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:57 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 15:57 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 15:57 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:57 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:57 DEBUG  CommonBackend: Searching for local CDs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:57 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-28 15:57 INFO   root: Running the installer...
09-28 15:57 DEBUG  WindowsFrontend: __init__...
09-28 15:57 DEBUG  WindowsFrontend: on_init...
09-28 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\translations, languages=['en_US', 'en']
09-28 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pylEA4F.tmp\translations, languages=['en_US', 'en']
09-28 15:57 DEBUG  WindowsFrontend: frontend.on_quit
09-28 15:57 DEBUG  root: application.on_quit
09-28 15:57 INFO   root: sys.exit
09-28 15:57 INFO   root: === wubi 14.04 rev286 ===
09-28 15:57 DEBUG  root: Logfile is c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log
09-28 15:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Matt\\Downloads\\ubuntu-14.04.1-desktop-amd64\\wubi.exe"']
09-28 15:57 DEBUG  CommonBackend: data_dir=C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\data
09-28 15:57 DEBUG  WindowsBackend: 7z=C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\bin\7z.exe
09-28 15:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 15:57 DEBUG  CommonBackend: Fetching basic info...
09-28 15:57 DEBUG  CommonBackend: original_exe=C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe
09-28 15:57 DEBUG  CommonBackend: platform=win32
09-28 15:57 DEBUG  CommonBackend: osname=nt
09-28 15:57 DEBUG  CommonBackend: language=en_US
09-28 15:57 DEBUG  CommonBackend: encoding=cp1252
09-28 15:57 DEBUG  WindowsBackend: arch=amd64
09-28 15:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\data\isolist.ini
09-28 15:57 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-28 15:57 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-28 15:57 DEBUG  WindowsBackend: Fetching host info...
09-28 15:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 15:57 DEBUG  WindowsBackend: windows version=vista
09-28 15:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-28 15:57 DEBUG  WindowsBackend: windows_sp=None
09-28 15:57 DEBUG  WindowsBackend: windows_build=7601
09-28 15:57 DEBUG  WindowsBackend: gmt=-6
09-28 15:57 DEBUG  WindowsBackend: country=US
09-28 15:57 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 15:57 DEBUG  WindowsBackend: windows_username=Matt
09-28 15:57 DEBUG  WindowsBackend: user_full_name=Matt
09-28 15:57 DEBUG  WindowsBackend: user_directory=C:\Users\Matt
09-28 15:57 DEBUG  WindowsBackend: windows_language_code=1033
09-28 15:57 DEBUG  WindowsBackend: windows_language=English
09-28 15:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-28 15:57 DEBUG  WindowsBackend: bootloader=vista
09-28 15:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95368.5117188 mb free ntfs)
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(C: hd 95368.5117188 mb free ntfs)
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(F: hd 337756.179688 mb free ntfs)
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(I: hd 61.37890625 mb free ntfs)
09-28 15:57 DEBUG  WindowsBackend: drive=Drive(J: removable 2820.29296875 mb free fat32)
09-28 15:57 DEBUG  WindowsBackend: uninstaller_path=None
09-28 15:57 DEBUG  WindowsBackend: previous_target_dir=None
09-28 15:57 DEBUG  WindowsBackend: previous_distro_name=None
09-28 15:57 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 15:57 DEBUG  WindowsBackend: keyboard_layout=us
09-28 15:57 DEBUG  WindowsBackend: keyboard_variant=
09-28 15:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 15:57 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 15:57 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-28 15:57 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 15:57 DEBUG  CommonBackend: Searching for local CDs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
09-28 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:57 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-28 15:57 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 15:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 15:57 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-28 15:57 INFO   root: Running the installer...
09-28 15:57 DEBUG  WindowsFrontend: __init__...
09-28 15:57 DEBUG  WindowsFrontend: on_init...
09-28 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\translations, languages=['en_US', 'en']
09-28 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\translations, languages=['en_US', 'en']
09-28 15:58 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=matt
09-28 15:58 INFO   root: Received settings
09-28 15:58 DEBUG  CommonBackend: Searching for local CD
09-28 15:58 DEBUG  Distro:   checking whether C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp is a valid Ubuntu CD
09-28 15:58 DEBUG  Distro:     does not contain C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\casper\filesystem.squashfs
09-28 15:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-28 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-28 15:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-28 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-28 15:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-28 15:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-28 15:58 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-28 15:58 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-28 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\translations, languages=['en_US', 'en']
09-28 15:58 DEBUG  TaskList: # Running tasklist...
09-28 15:58 DEBUG  TaskList: ## Running select_target_dir...
09-28 15:58 INFO   WindowsBackend: Installing into C:\ubuntu
09-28 15:58 DEBUG  TaskList: ## Finished select_target_dir
09-28 15:58 DEBUG  TaskList: ## Running create_dir_structure...
09-28 15:58 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-28 15:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-28 15:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-28 15:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-28 15:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-28 15:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-28 15:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-28 15:58 DEBUG  TaskList: ## Finished create_dir_structure
09-28 15:58 DEBUG  TaskList: ## Running uncompress_target_dir...
09-28 15:58 DEBUG  TaskList: ## Finished uncompress_target_dir
09-28 15:58 DEBUG  TaskList: ## Running create_uninstaller...
09-28 15:58 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Matt\Downloads\ubuntu-14.04.1-desktop-amd64\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-28 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-28 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-28 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-28 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-28 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
09-28 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-28 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-28 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-28 15:58 DEBUG  TaskList: ## Finished create_uninstaller
09-28 15:58 DEBUG  TaskList: ## Running copy_installation_files...
09-28 15:58 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-28 15:58 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\winboot -> C:\ubuntu\winboot
09-28 15:58 DEBUG  WindowsBackend: Copying C:\Users\Matt\AppData\Local\Temp\pyl4E5E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-28 15:58 DEBUG  TaskList: ## Finished copy_installation_files
09-28 15:58 DEBUG  TaskList: ## Running get_iso...
09-28 15:58 DEBUG  TaskList: New task copy_file
09-28 15:58 DEBUG  TaskList: ### Running copy_file...
09-28 16:02 DEBUG  TaskList: ### Finished copy_file
09-28 16:02 DEBUG  TaskList: New task check_iso
09-28 16:02 DEBUG  TaskList: ### Running check_iso...
09-28 16:02 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
09-28 16:02 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
09-28 16:02 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
09-28 16:02 DEBUG  Distro:   parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
09-28 16:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
09-28 16:02 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
09-28 16:02 DEBUG  TaskList: New task get_metalink
09-28 16:02 DEBUG  TaskList: #### Running get_metalink...
09-28 16:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
09-28 16:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-28 16:02 DEBUG  downloader: download finished (read 45848 bytes)
09-28 16:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-28 16:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
09-28 16:02 DEBUG  downloader: download finished (read 560 bytes)
09-28 16:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-28 16:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-28 16:02 DEBUG  downloader: download finished (read 198 bytes)
09-28 16:02 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-28 16:02 INFO   saplog: Checking block bindings..
09-28 16:02 INFO   saplog: Key verified successfully.
09-28 16:02 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink

09-28 16:02 ERROR  CommonBackend: The md5 of the metalink does match
09-28 16:02 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-28 16:02 DEBUG  TaskList: #### Finished get_metalink
09-28 16:02 DEBUG  TaskList: New task get_file_md5
09-28 16:02 DEBUG  TaskList: #### Running get_file_md5...
09-28 16:03 DEBUG  TaskList: #### Finished get_file_md5
09-28 16:03 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dccff28314d9ae4ed262cfc6f35e5153 != e936fed2c0f3b1296e0fc6b15bafd13b)
None
09-28 16:03 DEBUG  TaskList: ### Finished check_iso
09-28 16:03 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
09-28 16:03 DEBUG  TaskList: # Cancelling tasklist
09-28 16:03 DEBUG  TaskList: # Finished tasklist
09-28 16:03 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'

```

I have no idea what this means or what to do. Any help would be greatly appreciated. If you have questions for me, just ask them.

---

### Post by Iowan on 2014-09-28
Not a forum issue - moved to General Help.

---

### Post by Old_Grey_Wolf on 2014-09-28
People need some more info to help. For starters,

What version of Windows is installed?
Does the computer use UEFI?

You will need to be patient. I noticed you tried a WUBI install.

I would recommend a normal dual boot. But, we need to find out why the computer doesn't recognize the cd/dvd.

---

### Post by sammiev on 2014-09-28
Please note that wubi is not supported any more.

---

### Post by ethanbmnz on 2014-09-28
Have you tried setting the CD/DVD/USB to boot first in the BIOS/UEFI System?

Try redownload the ISO if possible. I advise using a USB instead of CD/DVD

The USB may have to be GPT partition table instead of MBR for UEFI - not too sure (don't have UEFI)

---

### Post by mbrown122098 on 2014-09-28
OS: Windows 7 Ultimate 64-bit

CPU: Intel Core 2 Quad 2.40GHz

GPU: EVGA GeForce GTX 650

RAM: G.SKILL 8gb 1066MHz DDR2 

I do not know what UEFI is... I do know that I have my cd/dvd drive plugged in through my sata cable and my pc doesn't seem to know what it is anymore.
I tried the cable on my HDD and it worked for it well... I have my boot settings on 1) USB Device, 2) HDD, 3) CD/DVD Drive. When I use the boot menu to force boot from stick
it just says Current Drive Not Found... Anything else you might want to know?

---

### Post by mbrown122098 on 2014-09-28
> **Iowan said:**
> Not a forum issue - moved to General Help.
Thank you very much. I am new to the forum. And if you put the log in the code, thank you for that too! I didn't think about using BBcode here.

---

### Post by sandyd on 2014-09-28
> **mbrown122098 said:**
> OS: Windows 7 Ultimate 64-bit

CPU: Intel Core 2 Quad 2.40GHz

GPU: EVGA GeForce GTX 650

RAM: G.SKILL 8gb 1066MHz DDR2 

I do not know what UEFI is... I do know that I have my cd/dvd drive plugged in through my sata cable and my pc doesn't seem to know what it is anymore.
I tried the cable on my HDD and it worked for it well... I have my boot settings on 1) USB Device, 2) HDD, 3) CD/DVD Drive. When I use the boot menu to force boot from stick
it just says Current Drive Not Found... Anything else you might want to know?

Hi, how did you create the USB stick?

---

### Post by hakuna_matata on 2014-09-29
> ```
09-28 16:03 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso ([COLOR=#ff0000]dccff28314d9ae4ed262cfc6f35e5153[/COLOR] !=[COLOR=#ff0000] e936fed2c0f3b1296e0fc6b15bafd13b[/COLOR])
None
```
[COLOR=#ff0000]dccff28314d9ae4ed262cfc6f35e5153 [/COLOR]is md5sum of ubuntu-14.04-desktop-amd64.iso
[COLOR=#ff0000]e936fed2c0f3b1296e0fc6b15bafd13b[/COLOR] is not a valid md5sum of an Ubuntu iso file, IMHO it is an image of your drive J:

This means wubi needs ubuntu-14.04-desktop-amd64.iso but there is only a copy of your drive J: 

Maybe you copy all files of an Ubuntu iso file to your drive J: but this doesn't work.

If you want to create a bootable USB drive, use programs like [rufus]("http://rufus.akeo.ie") to do so.  If you have a bootable USB drive there is no need for not recommended Wubi.

---

### Post by mbrown122098 on 2014-09-29
> **sandyd said:**
> Hi, how did you create the USB stick?

There was a link i saw on how to make an ubuntu bootable usb stick with windows. [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by mbrown122098 on 2014-09-29
> **hakuna_matata said:**
> [COLOR=#ff0000]dccff28314d9ae4ed262cfc6f35e5153 [/COLOR]is md5sum of ubuntu-14.04-desktop-amd64.iso
[COLOR=#ff0000]e936fed2c0f3b1296e0fc6b15bafd13b[/COLOR] is not a valid md5sum of an Ubuntu iso file, IMHO it is an image of your drive J:

This means wubi needs ubuntu-14.04-desktop-amd64.iso but there is only a copy of your drive J: 

Maybe you copy all files of an Ubuntu iso file to your drive J: but this doesn't work.

If you want to create a bootable USB drive, use programs like [rufus]("http://rufus.akeo.ie") to do so.  If you have a bootable USB drive there is no need for not recommended Wubi.

Thank you, but I don't know how I would use this to make a bootable ubuntu usb. My motherboard is from a Dell optiplex 745. The bios is the latest from Dell.com would this be a problem?

---

### Post by hakuna_matata on 2014-09-30
[LIST]
[*]Download an Ubuntu .iso file from [here]("http://releases.ubuntu.com/trusty/") . I recommend latest point release [ubuntu-14.04.1-desktop-amd64.iso]("http://releases.ubuntu.com/trusty/ubuntu-14.04.1-desktop-amd64.iso") 
[*]Download latest version of rufus from [here]("http://rufus.akeo.ie/downloads/rufus.exe") 
[*]Run rufus.exe and create a bootable disk using downloaded Ubuntu iso image. You need an eraseable USB device like an USB key/pendrive. Further informations are [here]("http://rufus.akeo.ie/") 
[*]Change boot sequence in your BIOS. USB device should be first boot device in sequence. Here is a link for a manual of your mainboard: [ftp://ftp.dell.com/Manuals/all-products/esuprt_desktop/esuprt_optiplex_desktop/optiplex-745_user%27s%20guide_en-us.pdf](ftp://ftp.dell.com/Manuals/all-products/esuprt_desktop/esuprt_optiplex_desktop/optiplex-745_user%27s%20guide_en-us.pdf) 
[*]Boot from USB key/pendrive 
[*]Follow installation guide: [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) 
[/LIST]

---

### Post by mbrown122098 on 2014-10-01
> **hakuna_matata said:**
> 
[LIST]
[*]Download an Ubuntu .iso file from [here]("http://releases.ubuntu.com/trusty/") . I recommend latest point release [ubuntu-14.04.1-desktop-amd64.iso]("http://releases.ubuntu.com/trusty/ubuntu-14.04.1-desktop-amd64.iso") 
[*]Download latest version of rufus from [here]("http://rufus.akeo.ie/downloads/rufus.exe") 
[*]Run rufus.exe and create a bootable disk using downloaded Ubuntu iso image. You need an eraseable USB device like an USB key/pendrive. Further informations are [here]("http://rufus.akeo.ie/") 
[*]Change boot sequence in your BIOS. USB device should be first boot device in sequence. Here is a link for a manual of your mainboard: [ftp://ftp.dell.com/Manuals/all-products/esuprt_desktop/esuprt_optiplex_desktop/optiplex-745_user%27s%20guide_en-us.pdf](ftp://ftp.dell.com/Manuals/all-products/esuprt_desktop/esuprt_optiplex_desktop/optiplex-745_user%27s%20guide_en-us.pdf) 
[*]Boot from USB key/pendrive 
[*]Follow installation guide: [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) 
[/LIST]


This did not work. However I bought a new disk drive and installed ubuntu on my external hard drive. And of course it won't boot from it. It works when I try it but after install its a no go. There was no way to make a new partition on my hard drive without deleting the current one... So i would have to delete windows and all of my stuff.... Not gunna happen. I don't know what to do now anyway. Any suggestions?

---

### Post by hakuna_matata on 2014-10-02
> **mbrown122098 said:**
> It works when I try it but after install its a no go.
Does this mean that only the last step 
> Follow installation guide: [http://www.ubuntu.com/download/deskt...ubuntu-desktop]("http://www.ubuntu.com/download/desktop/install-ubuntu-desktop")
did not work ?

Maybe this post of yancek helps to install without Wubi: [http://ubuntuforums.org/showthread.php?t=2244802&p=13125284#post13125284](http://ubuntuforums.org/showthread.php?t=2244802&p=13125284#post13125284)

If Wubi is still the last remaining option for you:


[LIST]
[*]Copy [**ubuntu-14.04-desktop-amd64.iso**]("http://releases.ubuntu.com/trusty/ubuntu-14.04-desktop-amd64.iso") (note: 14.04) and [wubi.exe]("http://releases.ubuntu.com/trusty/wubi.exe") to same Windows folder 
[*]Run [wubi.exe]("http://releases.ubuntu.com/trusty/wubi.exe") 
[*]Follow Wubiguide from [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) 
[*]Follow this thread if "serious errors" occur: [http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696](http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696) 
[/LIST]

OR


[LIST]
[*]Copy [**ubuntu-14.04-1-desktop-amd64.iso**]("http://releases.ubuntu.com/trusty/ubuntu-14.04.1-desktop-amd64.iso") (note: 14.04.**1**) and my patched [wubi14041.exe]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AADSCV93EfKjH_B0PwUwUhWaa/wubi14041.exe?dl=0") to same Windows folder. 
[*]Run [wubi14041.exe]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AADSCV93EfKjH_B0PwUwUhWaa/wubi14041.exe?dl=0") 
[*]Follow Wubiguide from [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) 
[/LIST]

---

### Post by yancek on 2014-10-02
> I bought a new disk drive and installed ubuntu on my external hard drive.

Did you go through the total installation process after booting  from the flash drive you created with the Universal USB Installer?  Did the installer complete and tell you so and tell you to reboot?  You have an option as to where to install the Grub bootloader, do you remember what you selected?  The default?  What can you boot now, jsut windows 7?

> There was no way to make a new partition on my hard drive without deleting the current one.

Well, what are we talking about here?  You just said you installed it?  Are you talking about installing it on your internal drive?  You can shrink partitions from windows if you want but I though you were trying to install on an external drive?

More information needed.  With your external drive attached, boot the medium you used that had Ubuntu on it, which you used as the installer.  Select the Try Ubuntu option and wait until you get to the Desktop.  If you have an internet connection go to the site below and download and run the bootinfoscript.  There are instructions in a link in the Description box.  Read them and post the output, a results.txt file which will give us some information which will be helpful.

 [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Talinko on 2014-10-11
Hi all, I'm getting the same error though I'm not using Wubi. I created a usb live cd with Universal USB Installer and chose to install Ubuntu inside Windows. The computer restarted, Windows booted up, started installing Ubuntu and then failed with the same error 

[COLOR=#000000]"An error accourred:[/COLOR]

[COLOR=#000000]'NoneType' object has no attribute 'get_info'[/COLOR]

[COLOR=#000000]For more information, please see the log file:[/COLOR]
[COLOR=#000000]c:\users\matt\appdata\local\temp\wubi-14.04-rev286.log[/COLOR]  

I'm on Windows 7 32 bit

---

### Post by hakuna_matata on 2014-10-11
> **Talinko said:**
> I'm getting the same error though I'm not using Wubi. I created a usb live cd with Universal USB Installer and chose to install Ubuntu inside Windows.
If you choose to install Ubuntu inside Windows, Ubuntu installer copies wubi.exe to Windows autostart. "Ubuntu inside Windows" appears only if Ubuntu installer is not able to create own partitions for Ubuntu automatically.

edit: To put in a nutshell, you used Wubi !

---

### Post by Talinko on 2014-10-11
Not willingly badfully. So what should I do? Create an unallocated partition in Windows and install ubuntu on it, or choose the something else option and do it from there? (not sure how to do either of those things)

---

### Post by hakuna_matata on 2014-10-11
> **Talinko said:**
> So what should I do?
As yancek said in a previous post:
> **yancek said:**
> 
More information needed.  With your external drive attached, boot the  medium you used that had Ubuntu on it, which you used as the installer.   Select the Try Ubuntu option and wait until you get to the Desktop.  If  you have an internet connection go to the site below and download and  run the bootinfoscript.  There are instructions in a link in the  Description box.  Read them and post the output, a results.txt file  which will give us some information which will be helpful.

 [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

