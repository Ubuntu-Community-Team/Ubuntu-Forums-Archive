---
title: "How to install tar.bz2 for suse into Ubuntu"
date: 2013-12-11
forum: General Help
---

### Post by RogerDavis on 2013-12-11
.../XTS/PSS-SUSE-UBUNTU-4.04.2.T.101206-LINUX.zip

I've followed the below instructions to the best of my ability, I have the files mentioned, they just don't work.
======================================
1.Copy PSSClient.tar.bz2 to your specified folder.
2.Decompress PSSClient.tar.bz2 to your specified folder.
3.Go to PSSClient and run InitPSS to initialize the PSS environment.
4.Double click PSSCient to run PSS applications.
6.After the initialization, you can just click the PSSClient in the PSSClient folder to run the PSS.

---

### Post by RogerDavis on 2013-12-13
Bump...

---

### Post by Mark de J on 2013-12-13
Is it excutable?

---

### Post by RogerDavis on 2013-12-13
I'm not sure how to answer your question, but both InitPSS and PSSClient are shown as executable in file managers.  When I click them, the cursor turns into a rotating circle for a few seconds, but nothing else happens.

I can't get any of the files to work with the upload feature here, so I can't post those.  But here is the text from start_pss.sh.  I see "suse" in there, but this is supposed to also work in Ubuntu.  Is there a conversion I need to do?  On the .zip, the tar.bz2, or?

export PATH=/root/zhaojian/suse/PSSClient/AppFile/runlib/bin;/usr/lib/mpi/gcc/openmpi/bin:/sbin:/usr/sbin:/usr/local/sbin:/root/bin:/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/X11R6/bin:/usr/games:/opt/kde3/bin:/usr/lib/mit/bin:/usr/lib/mit/sbin
export MALLPREFIX=/root/zhaojian/suse/PSSClient/AppFile/cfg_mall/
export DYLD_FALLBACK_LIBRARY_PATH="/root/zhaojian/suse/PSSClient/AppFile/runlib/libgl;/usr/lib;"

mall pssproject.dse

---

### Post by steeldriver on 2013-12-13
I'm not at all familiar with this software, but I suggest opening a terminal, navigating to the directory containing the executable files, and running them from there e.g.

```
./InitPSS
```

Based on its name (**Init**PSS) and description ("initialize the PSS environment") I suspect that the 'suse' will disappear from those paths when you successfully execute the first file. If it fails, at least you should get some kind of error message that helps shed some light.

---

### Post by RogerDavis on 2013-12-13
The result is below :
roger@roger-desktop:~/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ InitPSS
InitPSS: command not found
roger@roger-desktop:~/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ PSSClient
PSSClient: command not found
roger@roger-desktop:~/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ dir
AppFile  InitPSS  PSSClient

These files are CLEARLY marked as executable in Nautilus and XFE !!!

PSSClient
folder (inode/directory)
2,523 items, totalling 323.9 MB
/home/roger/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206

InitPSS
executable (application/x-executable)
10.3 kB (10,326 bytes)
/home/roger/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient

PSSClient
executable (application/x-executable)
10.3 kB (10,288 bytes)
/home/roger/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient

---

### Post by steeldriver on 2013-12-13
Because the directory will not be in your executable path (as given by your $PATH environment variable), you need to give an explicit relative path as I showed in my previous post

```
[COLOR=#0000cd]**./**[/COLOR]InitPSS
```

---

### Post by RogerDavis on 2013-12-13
Making some headway, but still a problem...
-------------------------------------------------------
roger@roger-desktop:~/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ ./InitPSS
cpRet = /home/roger/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient , WorkDir=/home/roger/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient
Finish InitPSS
nRet = 0 
roger@roger-desktop:~/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ ./PSSClient
cpRet = /home/roger/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient , WorkDir=/home/roger/PSSClient 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient
nRet = 0 
./start_pss.sh: 2: export: 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/AppFile/runlib/bin: bad variable name
------------------------------------------------------------
Any ideas for the next try?

---

### Post by steeldriver on 2013-12-13
It looks like it can't handle the fact that your installation path has a space in it - it is undergoing 'word splitting' - try renaming the directory with a dash or underscore instead of a space e.g.

```
~/PSSClient[SIZE=2]**[COLOR=#ff0000]_[/COLOR]**[/SIZE]4.04.2
```

---

### Post by RogerDavis on 2013-12-13
Back to spinning the wheels again:
---------------------------------------------------
roger@roger-desktop:~/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ ./PSSClient
cpRet = /home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient , WorkDir=/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient
nRet = 0 
./start_pss.sh: 2: export: 4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/AppFile/runlib/bin: bad variable name
-----------------------------------------------------
Would the file name also be a variable name?

---

### Post by steeldriver on 2013-12-13
Did you run the ./InitPSS again after changing the directory name?

---

### Post by RogerDavis on 2013-12-13
DOH... IT'S ALIVE!!!  ** T H A N K S !!!**

Now... just a CMA to make sure... how do I create a desktop launch Icon to start this thing normally?

Thanks again...

FYI
-------------------------
roger@roger-desktop:~/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ ./InitPSS
cpRet = /home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient , WorkDir=/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient
Finish InitPSS
nRet = 0 
roger@roger-desktop:~/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ ./PSSClient
cpRet = /home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient , WorkDir=/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient
nRet = 0 
./start_pss.sh: 2: ./start_pss.sh: /home/roger/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: not found
roger@roger-desktop:~/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient$ err:menubuilder:init_xdg error looking up the desktop directory
err:module:load_builtin_dso failed to load .so lib for builtin L"mallmp3.acm": /home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/AppFile/runlib/bin/../lib/mall/mallmp3.acm.so: invalid ELF header
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:ntdso:NtLockFile I/O completion on lock not implemented yet
fixme:win:EnumDisplayDevicesW ((null),0,0x32c5cc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32c5cc,0x00000000), stub!
.\PSSProject.cpp:840  2
fixme:system:SetProcessDPIAware stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x315144,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x315144,0x00000000), stub!
fixme:system:SetProcessDPIAware stub!
fixme:font:MallEngCreateFontInstance Untranslated charset 255
.\View\AlarmLinkVideoDlg.cpp:63 wndCount:4
.\View\AlarmLinkVideoDlg.cpp:580, cx:768,cy:540
fixme:keyboard:RegisterHotKey (0x10062,0,0x00000002,46): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x30f2f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x30f2f8,0x00000000), stub!
fixme:font:MallEngCreateFontInstance Untranslated charset 255
fixme:font:MallEngCreateFontInstance Untranslated charset 255
fixme:font:MallEngCreateFontInstance Untranslated charset 255
-------------------------------------------------------------------------------

---

### Post by RogerDavis on 2013-12-14
I can get the desktop icon created, I can fill in the command line with various versions of the path, they all get me "permission denied" except the below line, which gets me nothing except a few hits on the hard drive light.
----------------------------------
/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/PSSClient
-------------------------------------

I need the desktop icon to do the same as the terminal command line :
-----------------------------------------
roger@roger-desktop:~$ /home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/ ./PSSClient
--------------------------------------------------

So far, no luck...

And yes, I have tried 
-------------------------------
/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/ ./PSSClient
-----------------------------------
It gets me "Details: Failed to execute child process "/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/" (Permission denied)"

---

### Post by monkeybrain20122 on 2013-12-14
Right click the .desktop file you created and in Properties > Permission set it to be executable.

---

### Post by RogerDavis on 2013-12-14
Owner, Group, and Others are already checked to enable Execute, looking at permissions on the icon.  Is there another place to look?  

I also checked usr/share/applications.

---

### Post by monkeybrain20122 on 2013-12-14
How did you make the .desktop file? You should know where it is since you created it.

Edited: in case the .desktop file was created automatically it would be in /home/yourusername/.local/share/applications if you run the install script as normal user (no sudo). .local is a hidden folder. To see it open the file manager to show your home and then either do ctrl+h or from the drop down menu of your file manager (whatever it is) and choose "show hidden files".

---

### Post by RogerDavis on 2013-12-14
I didn't create a file.  I copied a similar icon, and put into the properties the info for the new program.  

So I take it that there is a better process...

---

### Post by monkeybrain20122 on 2013-12-14
Where did you copy it from? It has to be put in ~/.local/share/applications if it is created correctly.

Here is how to do it (it is for blender, but the procedures are the same)
[http://ubuntuforums.org/showthread.php?t=2183179](http://ubuntuforums.org/showthread.php?t=2183179)

---

### Post by RogerDavis on 2013-12-14
Nope, not there either.  Is it "traceable" in any way, like to search by the name?

---

### Post by monkeybrain20122 on 2013-12-14
So where did you copy it to? What is in it?

You can create one following the link I posted.

---

### Post by RogerDavis on 2013-12-14
Is this it?  In home/roger/desktop

[Desktop Entry]
Type=Application
Version=0.9.4
Name=PSSClient
Comment=PSSClient Application
Icon=/home/roger/PSSClient/PSS.ico
Exec=/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/PSSClient
Terminal=false
Path=/home/roger/PSSClient
Name[en_US]=PSS - Palace 8 icon
GenericName[en_US]=PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient

---

### Post by monkeybrain20122 on 2013-12-14
You shouldn't put in on the desktop. Move it to .local/share/applications. Then it will show up in the dash (may have to logout first). After that you can drag it from the dash or .local/share/applications to your desktop if you want it to show there. But you have to save the actual file in .local/share/applications first.

---

### Post by RogerDavis on 2013-12-14
Now got it to open the app, but the icon is gone... just a generic one now...  damn...

---

### Post by monkeybrain20122 on 2013-12-14
You have to link it to the actual location of the icon and .ico is a MicroSoft format so it won't show. You have to convert the .ico to .png first.
Imagemagick should be installed in your system. If not then just install it from the software center/synaptic  or 
```
sudo apt-get install imagemagick

```
then, say the path to your .ico file is /home/roger/PSSClient/PSS.ico, open a terminal, type

```
cd PSSClient
convert PSS.ico PSS.png
```

It may produce several .png files of different resolutions. 
Now in the .desktop file above, change the icon line to point to a .png icon

---

### Post by RogerDavis on 2013-12-14
Imagemagick was already installed, but I didn't convert, at least yet.

I simply moved a copy of the icon (.ico type) from the original version (antique) into the current directory, and linked it to the Icon spec in the file.  I had to resize the icon, and poof, there it was.  Hopefully, it will stay after reboot, etc.  If not, I'll convert.

THANKS! for everything!

---

### Post by RogerDavis on 2013-12-14
It works after reboot!  FYI, here is a copy of the working file, in home/Roger/Desktop
--------------------------------
[Desktop Entry]
Type=Application
Version=4.04.2
Name=PSSClient
Comment=PSSClient Application
Icon=/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/PSS.ico
Exec=/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/PSSClient
Terminal=false
Path=/home/roger/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient
Name[en_US]=PSS - Palace 8 icon
GenericName[en_US]=PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient
----------------------------------------------------
Any further advice would be greatly appreciated, if there is any!!!
Thanks!

---

### Post by RogerDavis on 2013-12-14
Come to think of it, in order to put it on another users desktop, simply copy the desktop file there?  Too late for more tonight, I have to be across town in the morning, 35 miles away...  but I'll do that later.

as usual, Thanks!

---

### Post by monkeybrain20122 on 2013-12-14
What other user? The program is in your home, right? another user account has no access to it.

---

### Post by RogerDavis on 2013-12-14
The other user is my girlfriend.  The program is to monitor the cameras at her house when she's over here.  She has a user account on this same machine, with a separate log-in for her.  So she needs to be able to access it directly from her log-in.

I could either install it twice, or give it a separate active icon, to start the same program from her log-in?

I can see her asleep on the chair now, I'm gonna be in deep stuff for being so late.  I still have to take out the garbage, and drive 35 miles, and MAYBE sneak in without waking her as I open the door...   But it's for a good cause, right?

But the cat will probably jump up, and that will be the end of it...

---

### Post by monkeybrain20122 on 2013-12-14
If your software is installed for the whole system (that typically means you install as root, with "sudo") then she would be able to access it from her account. But you installed it locally in your home  in that case no, she won't be able to run it from her account. However, since the whole program is inside one folder you can just copy  PSSClient-4.04.2 to her home, without reinstalling. Of course you have to change the paths of the .desktop file accordingly. I think instead of the whole path,  you should be able to write something like 

Exec=~/PSSClient-4.04.2/General_PSS_Suse_Eng_IS_V4.04.2.T.101206/PSSClient/PSSClient

That way you can copy it to her home without change.

---

