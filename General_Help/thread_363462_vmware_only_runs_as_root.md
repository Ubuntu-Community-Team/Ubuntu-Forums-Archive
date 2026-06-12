---
title: "vmware only runs as root"
date: 2007-02-16
forum: General Help
---

### Post by m.musashi on 2007-02-16
I recently reinstalled edgy and as a result had to reinstall vmware too. I've had this running fine in the past but now it won't start. If I run it in a terminal I have to use sudo or I get
```
jim@edgy:~$ vmware
exec: 180: /usr/lib/vmware/lib/wrapper-gtk24.sh: Permission denied
```
If I chown /usr/lib/vmware/ to my username it will work fine but I'm pretty sure I didn't do that before and do I really want to change a /usr/lib directory permission to a user and not root? I'm guessing that it should stay root and most likely was before. Any ideas why it won't work now unless I change permissions? My only guess is that it's because I have a new kernel but I ran 
```
sudo /usr/bin/vmware-config.pl
``` so that should have taken care of that?

Any help would be appreciated.

Thanks.

EDIT: I figured this out. Check my last post

---

### Post by yabbadabbadont on 2007-02-17
The vmware installation creates a vmware group.  Your user must be a member of that group.  Use "id username" to see if you are a member.  If not use, "sudo gpasswd -a username vmware", to add yourself to that group.  You will need to logout and back in for group membership changes to take effect.

---

### Post by m.musashi on 2007-02-17
Thanks, that does seem like a possible reason. Vmware is not listed under my id. However, when I run "sudo gpasswd -a username vmware" I get
```
jim@edgy:~$ sudo gpasswd -a jim vmware
Password:
unknown group: vmware
gpasswd: Permission denied.
```
Does that suggest anything?

---

### Post by yabbadabbadont on 2007-02-17
Look around in /usr/lib/vmware and see what group is actually being used.  I'm almost certain that the install created a vmware group when I ran it on Dapper.  I know for a fact that it did when I had it installed in Gentoo.  If you have to, you might try uninstalling it, removing the /etc/vmware directory, and then reinstalling it again.

---

### Post by m.musashi on 2007-02-17
/usr/lib/vmware is owned by root. I changed it to my username and then it worked but that seems bad form so I changed it back. I guess I can try the reinstall.

---

### Post by yabbadabbadont on 2007-02-17
Deleted unintentional misinformation.  See following post.

---

### Post by yabbadabbadont on 2007-02-17
[ebuild](http://sources.gentoo.org/viewcvs.py/gentoo-x86/app-emulation/vmware-server/vmware-server-1.0.1.29996-r5.ebuild?view=markup)
It looks like they copy a pam authentication file from the vmware-server installation directory tree to /etc/pam.d so that only members of the vmware group can login to the vmware-console.  I haven't messed with that yet, but I did make sure to change /etc/xinetd.conf to add an "only_from" option so that only users on the local machine (127.0.0.1) could start the console.
```
/home/bubba $ cat /etc/xinetd.conf 
# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{
        only_from = 127.0.0.1

}

includedir /etc/xinetd.d

```

---

### Post by m.musashi on 2007-02-17
My original install also worked fine. After reinstalling edgy, I did run the upgrade to the new kernel before reinstalling vmware if that makes any difference. I just did a remove and reinstall and I still get the same error. I check permissions as you suggested
```
jim@edgy:~$ sudo ls -l /usr/lib/vmware/bin/vmware-vmx
-r-sr-xr-x 1 root root 4383540 2007-02-16 23:36 /usr/lib/vmware/bin/vmware-vmx
```
It looks like yours but still doesn't work. My only guess is it has something to do with the new kernel as that is really all that changed.

---

### Post by yabbadabbadont on 2007-02-17
> **m.musashi said:**
> My original install also worked fine. After reinstalling edgy, I did run the upgrade to the new kernel before reinstalling vmware if that makes any difference. I just did a remove and reinstall and I still get the same error. I check permissions as you suggested
```
jim@edgy:~$ sudo ls -l /usr/lib/vmware/bin/vmware-vmx
-r-sr-xr-x 1 root root 4383540 2007-02-16 23:36 /usr/lib/vmware/bin/vmware-vmx
```
It looks like yours but still doesn't work. My only guess is it has something to do with the new kernel as that is really all that changed.

Sorry, I'm out of suggestions.  It works fine on Dapper.  :(

---

### Post by m.musashi on 2007-02-17
Well, thanks for the help. It was working fine in edgy too. It installs fine and will run if I use sudo vmware so I know the install is good. It's just a permission thing and I can't figure out why it's an issue now but wasn't before.

How bad would it be to change the /usr/lib/vmware permissions from root to my username? Obviously it's supposed to run even if owned by root but it's not and that's all I can think of.

---

### Post by yabbadabbadont on 2007-02-17
That would probably be safer than leaving it set as root.  ;)  As long as you are the only one using the machine, I don't see a problem doing that.

---

### Post by m.musashi on 2007-02-17
Okay. I changed everything in /usr/lib/vmware to my username for ownership and now it vmware runs but when I go to power on the vm I get this
```
Unable to change virtual machine power state: The process exited with an error:


VMware Server Error:
VMware Server must be set-UID root, "/usr/lib/vmware/bin/vmware-vmx" is not. 
Are you running /usr/lib/vmware/bin/vmware-vmx from its distribution directory? 
That copy of the program is not set-UID root.
```
I guess it has to stay root in order to work but then I have to run as root to get it to work.

I wonder if this has anything to do with reinstallilng edgy but not /home (it's on a separate partition). It seems when I do that there are some files that need to be overwritten but aren't Does anyone know what vm files I need to keep and which ones I can trash with regard to what's in the folder with the actual vm os?

Or any other thoughts?

Thanks.

EDIT: while reinstalling I noticed I get this error. Any idea what it means or how to fix?
```

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
/usr/share/applications/vmware-console-uri-handler.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
```

---

### Post by m.musashi on 2007-02-17
Oh Yeah!!! Fixed it!!!

On a hunch, I deleted the install directory and re-extracted the original downloaded tarball. It think there are some config files, logs or something in there that prevent a new installation from being a NEW installation.

To reinstall vmware, uninstall and remove the /etc/vmware folder
```
sudo /usr/bin/vmware-uninstall.pl
sudo rm -Rf /etc/vmware
```
and then delete the entire /vmware-server-distrib/ folder from your /home (if that is where you put it. Re-extract the archive or just download a new copy. Then run the install as usual. It fixed the problem for me.

Thanks for the help.

---

