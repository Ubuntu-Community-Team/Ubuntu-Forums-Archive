---
title: "VMware Workstation 5.5.2 not responding"
date: 2006-11-13
forum: General Help
---

### Post by jeelliso on 2006-11-13
Hello,

I'm trying to install VMware Workstation 5.5.2 on my Ubuntu 6.10 system.  I've downloaded VMware-workstation-5.5.2-29772.tar.gz from the VMware website.  The install seemed to go fine, but when I try to run the vmware executable it just sits there.  The process gets 99% consumed and nothing happens.  Its like its in an infinite loop or something.  There are no error message or anything.  I've let it run for over 20 minutes with nothing else happening.  I've also tried running it from the Application menu item that the installer created.  Any ideas?

Here's the terminal output from the install (sorry for the long post):
```
root@patmos :~# tar -zxvf VMware-*
root@patmos:~# cd vmware-distrib
root@patmos:~/vmware-distrib# ./vmware-install.pl 
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Workstation.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done
   Virtual ethernet                                                    done

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

The removal of VMware Workstation 5.5.2 build-29772 for Linux completed 
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the library files? 
[/usr/lib/vmware] 

The path "/usr/lib/vmware" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] 

In which directory do you want to install the manual files? 
[/usr/share/man] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware Workstation 5.5.2 build-29772 for Linux completed 
successfully.
```

And here is the code from the configuration:
```
root@patmos:~/vmware-distrib# vmware-config.pl 
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-workstation.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Use of uninitialized value in addition (+) at /usr/bin/vmware-config.pl line 804, <STDIN> line 3.
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
/usr/share/applications/vmware-player.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Use of uninitialized value in addition (+) at /usr/bin/vmware-config.pl line 804, <STDIN> line 3.
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-10-386/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.17-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
WARNING: could not open /tmp/vmware-config0/vmnet-only/includeCheck.h: Invalid argument
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The file /lib/modules/2.6.17-10-386/misc/vmnet.o that this program was about to
install already exists.  Overwrite? [yes] 
The file /lib/modules/2.6.17-10-386/misc/vmnet.ko that this program was about 
to install already exists.  Overwrite? [yes] 

The module loads perfectly in the running kernel.

The file /etc/rc2.d/S90vmware that this program was about to install already 
exists.  Overwrite? [yes] 

The file /etc/rc2.d/K08vmware that this program was about to install already 
exists.  Overwrite? [yes] 

The file /etc/rc3.d/S90vmware that this program was about to install already 
exists.  Overwrite? [yes] 

The file /etc/rc3.d/K08vmware that this program was about to install already 
exists.  Overwrite? [yes] 

The file /etc/rc5.d/S90vmware that this program was about to install already 
exists.  Overwrite? [yes] 

The file /etc/rc5.d/K08vmware that this program was about to install already 
exists.  Overwrite? [yes] 

The file /etc/rc0.d/K08vmware that this program was about to install already 
exists.  Overwrite? [yes] 

The file /etc/rc6.d/K08vmware that this program was about to install already 
exists.  Overwrite? [yes] 


Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done

The configuration of VMware Workstation 5.5.2 build-29772 for Linux for this 
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command: 
"/usr/bin/vmware".

Enjoy,

--the VMware team
```

Thanks,
~Justin

---

