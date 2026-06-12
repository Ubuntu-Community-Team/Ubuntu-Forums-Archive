---
title: "Known Hardy bugs and workarounds"
date: 2008-04-29
forum: General Help
---

### Post by frodon on 2008-04-29
[COLOR=DarkOrange]**Disclaimer : The purpose of this thread is just to list known [SIZE=3]Hardy Heron[/SIZE] bugs and give the corresponding workarounds and launchpad entries. All discussions about the bug itself should go in the thread dedicated to the bug.**[/COLOR]
[COLOR=Red]**_Please do not list here bugs without any workaround_**[/COLOR]


_**sudo unable to resolve host**_
- Workaround : [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906)
[https://bugs.launchpad.net/ubuntu/+source/rescue/+bug/19553](https://bugs.launchpad.net/ubuntu/+source/rescue/+bug/19553)

_**Excessive disk I/O in Firefox 3b5**_ - Should be fixed now with firefox 3 release
- Workaround : [http://ubuntuforums.org/showpost.php?p=4770985&postcount=50](http://ubuntuforums.org/showpost.php?p=4770985&postcount=50)
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728)

_**Samba Shares**_
-Workaround : [http://ubuntuforums.org/showthread.php?t=772706](http://ubuntuforums.org/showthread.php?t=772706)
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810)

-Note : Basically right click on a directory and share it -> Install the needed samba server -> log out and back in -> Repeat right click on directory to share.

_Do Not Share $HOME_  : See [post #7]("http://ubuntuforums.org/showpost.php?p=4831320&postcount=7") in the "Workaround" above. ~ Thanks [Deeta]("http://ubuntuforums.org/member.php?u=415000")

_**ATI & Compiz**_ :
-Workaround : [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633) ~ Thanks [Rocket2DMn]("http://ubuntuforums.org/member.php?u=310232")
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/206845](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/206845)

_**GVFS and disk usage**_ :
-Workaround : [http://ubuntuforums.org/showthread.php?t=748778](http://ubuntuforums.org/showthread.php?t=748778)
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789)

_**SATA drives not detected in IDE mode (DELL users mainly)**_
-Workaround : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702/comments/35](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702/comments/35)
-related thread : [http://ubuntuforums.org/showthread.php?t=762257](http://ubuntuforums.org/showthread.php?t=762257)
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)

_**Install VMWare Server**_
- Workaround : [http://ubuntuforums.org/showthread.php?p=4868919](http://ubuntuforums.org/showthread.php?p=4868919)
Not really a bug, more of a FAQ.

_**VirtualBox OSE**_
- Problem : VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)
- Workaround : Remove VirtualBox OSE and install the PUEL version.
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807)

_**System -> Quit takes a long time to appear**_
-Bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078)
-Workaround: Reenable the gnome-power-manager in Administration-Sessions.

_**Shut down screen problem?**_
-Bug report :
-Workaround : [http://ubuntuforums.org/showthread.php?p=4858236#post4858236](http://ubuntuforums.org/showthread.php?p=4858236#post4858236)

_**Downgrade to Firefox 2, add-ons will not install**_
- Bug report :
- Workaround : [http://ubuntuforums.org/showthread.php?t=784628](http://ubuntuforums.org/showthread.php?t=784628)

_**Edit /etc/sudoers with gedit**_
- Workaround : [http://ubuntuforums.org/showthread.php?t=779902](http://ubuntuforums.org/showthread.php?t=779902)
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369)

_**High CPU usage in system monitor**_
- Workaround : [http://ubuntuforums.org/showpost.php?p=4825994&postcount=2](http://ubuntuforums.org/showpost.php?p=4825994&postcount=2) - use top or htop in the meantime, thanks vor.
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383) - fixed upstream and currently in -proposed [noparse](may 08th 2008)[/noparse]

**_Bluetooth headsets not working_**
Workaround : [http://ubuntuforums.org/showthread.php?p=4910397](http://ubuntuforums.org/showthread.php?p=4910397)
Bug report : [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/199266](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/199266)

_**USB devices and permissions**_
 - The syntax used in the 40-permissions.rules has changed with 8.04. In addition, any user changes now need to be in a user-numbered-and-named.rules file higher than 40.
- Workaround : [http://ubuntuforums.org/showpost.php?p=4916614&postcount=13](http://ubuntuforums.org/showpost.php?p=4916614&postcount=13)
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/210421](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/210421)
[color=blue]~ Thanks[/color] [anewguy]("http://ubuntuforums.org/member.php?u=331304")

_**Crash after installing system-config-samba**_
- Workaround : sudo touch /etc/libuser.conf
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/214959]("https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/214959")
Thanks [kikke]("http://ubuntuforums.org/member.php?u=183413")

**_Memory Leak in NetworkManager:_**
- Workaround : use Intrepid package which is fixed.
- Bug Report: [https://bugs.launchpad.net/ubuntu/hardy/+source/network-manager/+bug/203016](https://bugs.launchpad.net/ubuntu/hardy/+source/network-manager/+bug/203016)


Fell free to propose other known Hardy Heron bugs to be listed here but **[COLOR=Red]think to provide a link to the workaround and a link to the  corresponding launchpad entry.[/COLOR]**

---

### Post by chrisccoulson on 2008-04-29
**Excessive disk I/O in Firefox 3b5**

Workaround - [_http://ubuntuforums.org/showpost.php?p=4770985&postcount=50_]("http://ubuntuforums.org/showpost.php?p=4770985&postcount=50")
Bug report - [_https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728_]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728")

---

### Post by frodon on 2008-04-29
Added to first post, really helpful.

Thank you for your contribution :KS

---

### Post by funnypanks on 2008-04-29
for excessive io activity in firefox 3b5 a more permenant solution is 
Edit>Preferences>Security and then uncheck the 2 boxes that start out "tell me if the site I'm visiting"

also if u have random exits (aka segmentation fault) in ff3b5 type this into terminal, don't worry youtube still works
sudo mv /usr/lib/libflashsupport.so /usr/lib/libflashsupport.so.org

i didn't come up with either fix but i don't remember where i read it either, but both are working for me

if u use vlc and firefox at the same time where u need audio in both, in my computer (acer 5580) audio will only work for one or the other, to get around this in vlc click 
settings>preferences>click advanced advanced settings at the bottom> then on the left pane fan out audio>click output modules> change from default to alsa audio output>click save at the bottom 
and your done

---

### Post by Comhra on 2008-04-29
Very useful, thanks for that, my HH install is really coming together.

---

### Post by RAOF on 2008-04-30
> **funnypanks said:**
> ...
also if u have random exits (aka segmentation fault) in ff3b5 type this into terminal, don't worry youtube still works
sudo mv /usr/lib/libflashsupport.so /usr/lib/libflashsupport.so.org
...

Or, the much better way of doing this is
```
sudo aptitude remove libflashsupport
```
to actually remove the package rather than just make it not work :).

---

### Post by davidpbrown on 2008-05-01
_**SATA drives not detected in IDE mode**_

-Workaround : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702/comments/35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702/comments/35")
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702")

Either adding "all_generic_ide" to GRUB
Or switch the SATA mode in the BIOS from "IDE" to "RAID"

(See also [http://ubuntuforums.org/showthread.php?t=762257]("http://ubuntuforums.org/showthread.php?t=762257"))

---

### Post by frodon on 2008-05-01
Wil add that to first post with maybe a "Dell users" note as it seems mainly Dell related. Please correct me if i'm wrong.

Thanks for your contribution.

---

### Post by davidpbrown on 2008-05-01
Certainly, it seems to be principally Dell's Inspiron 530 and Vostro 200
Some posts suggest it might also affect systems using the same ?motherboard
eg [http://ubuntuforums.org/showthread.php?t=765195]("http://ubuntuforums.org/showthread.php?t=765195")

---

### Post by descentspb on 2008-05-03
_**System -> Quit takes a long time to appear**_

**Bug:** [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078)
**Workaround:** Reenable the gnome-power-manager in Administration-Sessions.

---

### Post by sdennie on 2008-05-07
**High CPU usage in system monitor**
Workaround: [http://ubuntuforums.org/showpost.php?p=4825994&postcount=2](http://ubuntuforums.org/showpost.php?p=4825994&postcount=2)
Bug Report: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)

---

### Post by frodon on 2008-05-08
Hello vor, thanks for your report.

When i check the bug report it says "Fix Committed", is this really solved now or are users still experiencing this bug with up to date hardy install ?

---

### Post by bapoumba on 2008-05-08
> **vor said:**
> **High CPU usage in system monitor**
Workaround: [http://ubuntuforums.org/showpost.php?p=4825994&postcount=2](http://ubuntuforums.org/showpost.php?p=4825994&postcount=2)
Bug Report: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)

Thanks vor. Looks there is a fix in -proposed to test out. Is it working for you?

---

### Post by bapoumba on 2008-05-08
> **frodon said:**
> Hello vor, thanks for your report.

When i check the bug report it says "Fix Committed", is this really solved now or are users still experiencing this bug with up to date hardy install ?

Sorry frodon, I did not see your post before I posted above.
The fix is in -proposed, not in the general updates yet :)

---

### Post by sdennie on 2008-05-08
> **frodon said:**
> Hello vor, thanks for your report.

When i check the bug report it says "Fix Committed", is this really solved now or are users still experiencing this bug with up to date hardy install ?

It's not fixed in either stock Hardy or -proposed.  I've tested it with full -proposed and, though it's better, it's still a bug.  The comments on the bug report seem to coming in to reflect that.

---

### Post by frodon on 2008-05-08
Ok, it's in first post, please let us know if you notice any fix committed for this bug.

Thanks again for your contribution.

---

### Post by kikke on 2008-05-09
Error: Crash after installing system-config-samba
Workaround: sudo touch /etc/libuser.conf

Reason: Error in the libuser1 package (which is a system-config-samba dependency) scripts, it does'nt create empty /etc/libuser.conf.

[https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/214959](https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/214959)

---

### Post by rolandixor on 2008-05-09
User won't give up windows.

Solution:
Install compiz configurator and after fiddling around, show off... if they won't switch after that, you may need to check their pulse...

---

### Post by TheExplorer on 2008-05-09
Hello everybody,

Sorry if I chose the wrong topic BUT (correct me please)

To all of you ASUS Mainboard people (especially M2N series) with AMD64 processors who faced the 'noapic' problem running 32-bit Ubuntu:

There is a new BIOS version already out (0808) and I haven't got a kernel panic this time. Believe it or not :)

---

### Post by joeinazyes on 2008-05-10
Add this to the list...

[http://ubuntuforums.org/showthread.php?t=788741&highlight=bittornado](http://ubuntuforums.org/showthread.php?t=788741&highlight=bittornado)

---

### Post by bapoumba on 2008-05-10
Kikke's bug and workaround added. Thanks :)

---

### Post by LorisMaria on 2008-05-11
> **funnypanks said:**
> 
if u use vlc and firefox at the same time where u need audio in both, in my computer (acer 5580) audio will only work for one or the other, to get around this in vlc click 
settings>preferences>click advanced advanced settings at the bottom> then on the left pane fan out audio>click output modules> change from default to alsa audio output>click save at the bottom 
and your done

Excellent solution. Worked with Exaile, too. Thanks for this!

---

### Post by Zorael on 2008-05-13
[SIZE="3"]**Bug description**[/SIZE]
KDE 3 paths for Desktop, Autostart and Documents, alterable in systemsettings under About Me -> Paths as well as in kcontrol under System Administration -> Paths are not saved correctly in [FONT="Courier New"]~/.config/user-dirs.dirs[/FONT].

[SIZE="3"]**What was expected**[/SIZE]
Paths are changed in [FONT="Courier New"]~/config/user-dirs.dirs[/FONT] and (in the case of the desktop directory) an automatic refresh of kdesktop correctly reflects this. A yes/no dialog box offering to move content from old directory to new one, creating it if necessary. 

[SIZE="3"]**What really happens**[/SIZE]
Path descriptions in [FONT="Courier New"]~/.config/user-dirs.dirs[/FONT] is appended with **[$E]** - making it **XDG_DESKTOP_DIR[$E]** in the case of the desktop directory - which makes kdesktop misparse it and use the root (/) directory instead. The yes/no dialog box appears, but it obviously can't write to the root directory unless user is a superuser. If you try to change it back and you answer yes to the dialog box (to move content to new dir), it will proceed to copy the entire root partition to the new directory. Unsure as to whether the Documents folder exhibits the same behavior.

[SIZE="3"]**Workaround**[/SIZE]
Edit [FONT="Courier New"]~/.config/user-dirs.dirs[/FONT] manually in a text editor and either remove any occurences of **[$E]** if systemsettings/kcontrol has been used to try to modify the path, or change the path manually if the file is virgin. A refresh of kdesktop may be needed, which can be done by right-clicking the desktop and picking Refresh, unless the right-click event has been changed in the Desktop settings. In that case a logout and login may be needed. Unsure as to whether the Documents folder reference exhibits the same behavior, but an educated guess would be that it would take effect immediately (i.e, reference is not cached, file managers read the file upon demand).

**Bug present in releases (at least):** 7.10 Gutsy Gibbon, 8.04 Hardy Heron
**Launchpad entry:** [#208253 ](https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/208253)

---

### Post by decoherence on 2008-05-16
Nvidia restricted driver not listed in Hardware Drivers (jockey)

bug: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/231069](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/231069)
workaround: [http://ubuntuforums.org/showthread.php?t=796322](http://ubuntuforums.org/showthread.php?t=796322)

(basic instruction on how to manually load and configure the nvidia driver from the command line)

---

### Post by kalpik on 2008-05-18
**Bug**: X crashes and restarts on opening some sites (eg. [http://www.ubuntuguide.org](http://www.ubuntuguide.org))

**Workaround**: [http://ubuntuforums.org/showpost.php?p=4987666&postcount=20](http://ubuntuforums.org/showpost.php?p=4987666&postcount=20)

**Cause**: Bad nvidia driver package.

---

### Post by mbsullivan on 2008-05-20
**Bug:** All mouse clicks on a Thinkpad notebook may be considered double clicks after upgrading.

**Fix:** Adding ```
Option "CorePointer"
``` in the ```
Section "InputDevice"
``` section of /etc/X11/xorg.conf (source: [here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/188351") and [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/196711"), among others).

---

### Post by IanW on 2008-05-20
Bug:-

Totem is unable to find any of its codecs, and Nautilus fails to thumbnail video files. [https://bugs.launchpad.net/bugs/219621](https://bugs.launchpad.net/bugs/219621)

What causes it:-

Multiple versions of x264 on the system. x264-57 installed by Hardy, and x264-54 left over from Gutsy.
(from thread [http://ubuntuforums.org/showthread.php?t=775943](http://ubuntuforums.org/showthread.php?t=775943))

Workaround:- 

1: Search Synaptic for x264 and select x264-57 for re-installation. x264-54 & x264-dev should be selected for complete removal.
2: Synaptic may complain that a whole bunch of apps depend on x264-54, so export the list of changes from Synaptic to a txt file.
3: Apply the changes in Synaptic.
4: Open the text file in Gedit, change every instance of "deinstall" for "install" and remove line for x264-54 (and x264-dev if it appears) entirely.
5: Import the altered file into Synaptic and Apply the changes, thus re-installing everything that got removed (except x264-54 & x264-dev).

---

### Post by damoxc on 2008-05-20
I've compiled latest libflashsupport from git and put it in:
```
deb http://ppa.launchpad.net/damoxc/ubuntu hardy main
deb-src http://ppa.launchpad.net/damoxc/ubuntu hardy main
```

This has reduced the firefox crashes (at least when using flash 10)

---

### Post by frodon on 2008-05-20
Thank you all for reporting known bugs here.

@decoherence and IanW, once the bugs you reported will be confirmed in launchpad i will add them to first the post.

---

### Post by Daboo on 2008-05-21
x

---

### Post by trazart on 2008-05-22
Not a bug but it is a problem if you dont know what is going on.

**Problem: hda, hdb... devices are missing so you cant mount your partitions.**

This is because the new kernel uses a different name for IDE devices: sda, sdb...

**Workaround**: [http://ubuntuforums.org/showthread.php?t=764762](http://ubuntuforums.org/showthread.php?t=764762)

Run> sudo fdisk -l
See what are your partition names
Change the entries in /etc/fstab

---

### Post by Keyper7 on 2008-05-23
Problem: Ugly window decoration, no shadows with compiz or pink shadows in compiz.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382)

Workaround: There's already a fix in hardy-proposed, but not enough people tested it yet.

---

### Post by Pjotr123 on 2008-06-02
I've published a couple of bugs plus workarounds here:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)

---

### Post by marcelo danico on 2008-06-03
Firefox crashes on flash contents when using libflashsupport
Bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/)

Workaround: Install Flashplayer10beta

[http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html](http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html)

---

### Post by Uchiha_madara on 2008-06-11
thanks dude , Very Wonderful and useful informations

and i face some thank u:guitar:

---

### Post by Portable_Jim on 2008-07-03
> **frodon said:**
> [COLOR=DarkOrange]**Disclaimer : The purpose of this thread is just to list known [SIZE=3]Hardy Heron[/SIZE] bugs and give the corresponding workarounds and launchpad entries. All discussions about the bug itself should go in the thread dedicated to the bug.**[/COLOR]
[COLOR=Red]**_Please do not list here bugs without any workaround_**[/COLOR]


_**sudo unable to resolve host**_
- Workaround : [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906)
[https://bugs.launchpad.net/ubuntu/+source/rescue/+bug/19553](https://bugs.launchpad.net/ubuntu/+source/rescue/+bug/19553)

_**Excessive disk I/O in Firefox 3b5**_
- Workaround : [http://ubuntuforums.org/showpost.php?p=4770985&postcount=50](http://ubuntuforums.org/showpost.php?p=4770985&postcount=50)
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728)

_**Samba Shares**_
-Workaround : [http://ubuntuforums.org/showthread.php?t=772706](http://ubuntuforums.org/showthread.php?t=772706)
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810)

-Note : Basically right click on a directory and share it -> Install the needed samba server -> log out and back in -> Repeat right click on directory to share.

_Do Not Share $HOME_  : See [post #7]("http://ubuntuforums.org/showpost.php?p=4831320&postcount=7") in the "Workaround" above. ~ Thanks [Deeta]("http://ubuntuforums.org/member.php?u=415000")

_**ATI & Compiz**_ :
-Workaround : [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633) ~ Thanks [Rocket2DMn]("http://ubuntuforums.org/member.php?u=310232")
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/206845](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/206845)

_**GVFS and disk usage**_ :
-Workaround : [http://ubuntuforums.org/showthread.php?t=748778](http://ubuntuforums.org/showthread.php?t=748778)
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789)

_**SATA drives not detected in IDE mode (DELL users mainly)**_
-Workaround : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702/comments/35](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702/comments/35)
-related thread : [http://ubuntuforums.org/showthread.php?t=762257](http://ubuntuforums.org/showthread.php?t=762257)
-Bug report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)

_**Install VMWare Server**_
- Workaround : [http://ubuntuforums.org/showthread.php?p=4868919](http://ubuntuforums.org/showthread.php?p=4868919)
Not really a bug, more of a FAQ.

_**VirtualBox OSE**_
- Problem : VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)
- Workaround : Remove VirtualBox OSE and install the PUEL version.
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807)

_**System -> Quit takes a long time to appear**_
-Bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078)
-Workaround: Reenable the gnome-power-manager in Administration-Sessions.

_**Shut down screen problem?**_
-Bug report :
-Workaround : [http://ubuntuforums.org/showthread.php?p=4858236#post4858236](http://ubuntuforums.org/showthread.php?p=4858236#post4858236)

_**Downgrade to Firefox 2, add-ons will not install**_
- Bug report :
- Workaround : [http://ubuntuforums.org/showthread.php?t=784628](http://ubuntuforums.org/showthread.php?t=784628)

_**Edit /etc/sudoers with gedit**_
- Workaround : [http://ubuntuforums.org/showthread.php?t=779902](http://ubuntuforums.org/showthread.php?t=779902)
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369)

_**High CPU usage in system monitor**_
- Workaround : [http://ubuntuforums.org/showpost.php?p=4825994&postcount=2](http://ubuntuforums.org/showpost.php?p=4825994&postcount=2) - use top or htop in the meantime, thanks vor.
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383) - fixed upstream and currently in -proposed [noparse](may 08th 2008)[/noparse]

**_Bluetooth headsets not working_**
Workaround : [http://ubuntuforums.org/showthread.php?p=4910397](http://ubuntuforums.org/showthread.php?p=4910397)
Bug report : [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/199266](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/199266)

_**USB devices and permissions**_
 - The syntax used in the 40-permissions.rules has changed with 8.04. In addition, any user changes now need to be in a user-numbered-and-named.rules file higher than 40.
- Workaround : [http://ubuntuforums.org/showpost.php?p=4916614&postcount=13](http://ubuntuforums.org/showpost.php?p=4916614&postcount=13)
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/210421](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/210421)
[COLOR=blue]~ Thanks[/COLOR] [anewguy]("http://ubuntuforums.org/member.php?u=331304")

_**Crash after installing system-config-samba**_
- Workaround : sudo touch /etc/libuser.conf
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/214959](https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/214959)
Thanks [kikke]("http://ubuntuforums.org/member.php?u=183413")

Fell free to propose other known Hardy Heron bugs to be listed here but **[COLOR=Red]think to provide a link to the workaround and a link to the  corresponding launchpad entry.[/COLOR]**
Thank you frodon & everyone els for this useful thread.

---

### Post by ger_mulvey on 2008-07-04
Hi,
Thanks for such great info!
Can the list be updated to indicate if any of the above are fixed in the maintanence release 8.04.1 I'm sure this info would be handy for many people!
Some of these issues have caused a few people to use other distros while awaiting fixes for some issues...me included!

Ger

---

### Post by computermacgyver on 2008-07-06
No specifically Hardy, but this first appeared for me once upgrading.

Bug: [http://bugzilla.gnome.org/show_bug.cgi?id=519071](http://bugzilla.gnome.org/show_bug.cgi?id=519071)

Description:
Using file browser to copy a to a bluetooth device (obex://) fails with the message: "The backend does not support this operation." This is an error with obex-ftp.

Workaround:
To send a file, you may:
1) right-click the Bluetooth icon in the system notification area
2) select "Send File"
3) Browse for the file and click ok
4) Select the device to send the file to and click ok
5) If the bluetooth device supports it, you may move the file using on board software, etc. to a sub-directory.

---

### Post by bford16 on 2008-07-14
**_SATA drives not recognized in Hardy with VIA VT8251 chipset_**

**Bug:** [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190492]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190492")
**Workaround:** Add "pci=nomsi" to GRUB boot parameters.

---

### Post by AlanJM01 on 2008-07-14
Anything on the System Updater keeps locking up?

I have to xkill the system update each time.

It worked for a while and now it does not.

---

### Post by yotam on 2008-07-17
> **chrisccoulson said:**
> **Excessive disk I/O in Firefox 3b5**

Workaround - [_http://ubuntuforums.org/showpost.php?p=4770985&postcount=50_]("http://ubuntuforums.org/showpost.php?p=4770985&postcount=50")
Bug report - [_https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728_]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728")

The suggestion to uncheck the 'Tell me ... suspected attack sites'
and remove urlclassifier* files seems to help only a little.
Soon after some surfing I had my 
 [FONT="Fixedsys"]~/.mozilla/firefox/*.default/urlclassifier3.sqlite[/FONT]
recreated.

---

### Post by Stilor on 2008-07-24
Bug: [https://bugs.launchpad.net/ubuntu/hardy/+source/network-manager/+bug/203016](https://bugs.launchpad.net/ubuntu/hardy/+source/network-manager/+bug/203016)
Fix: Install package from Intrepid, fix is still not in Hardy. [http://linux-tipps.blogspot.com/2008/06/memory-leak-in-ubuntus-networkmanager.html](http://linux-tipps.blogspot.com/2008/06/memory-leak-in-ubuntus-networkmanager.html)

---

### Post by frodon on 2008-07-24
> **Stilor said:**
> Bug: [https://bugs.launchpad.net/ubuntu/hardy/+source/network-manager/+bug/203016](https://bugs.launchpad.net/ubuntu/hardy/+source/network-manager/+bug/203016)
Fix: Install package from Intrepid, fix is still not in Hardy. [http://linux-tipps.blogspot.com/2008/06/memory-leak-in-ubuntus-networkmanager.html](http://linux-tipps.blogspot.com/2008/06/memory-leak-in-ubuntus-networkmanager.html)Added to the list, thanks for your feedback.

---

### Post by fhsm on 2008-08-05
**Setting an invalid mount point makes removable media unaccessible**
*Bug*: [107668]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668")
*Bug Description*:
 After accidentally setting a bad mount point for an external drive it becomes inaccessible.  Attempts to mount the drive return "Cannot mount volume. Unable to mount volume" "mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually /)".
  
*Workaround*:
1- Make a new spot to put mount your drive using mkdir.
```
sudo mkdir /media/yourdrivehere
```
Mounting external drives to /media is standard but not required.  You should replace 'yourdrivehere' with a more useful name.

2- Figure out what the system is calling the device you are looking to mount by running fdisk -l with the device attached to the system.
```
sudo fdisk -l
```
In my case I was looking for the last device listed:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1        9729    78148161    7  HPFS/NTFS
```
Of use here is the device name */dev/sdb1* and the format *NTFS*

3- Set your device to mount to the new mount point using the mount command.
```
sudo mount -t ntfs /dev/sdb1 /media/yourdrivehere
```
For this last command you'll obviously need to use whatever your device is called (as found in step 2) the file system of your devices (NTFS in the example, could be ext3, vfat, etc) and the mount point you made in step 1.

*continued in Update 2*
--------------------------------------------------------------------------------------
**Update:**
While this will get you to your drive without any problem the solution is not persistent.  The same error returns after a reboot.  The solution works on subsistent reboots.

---------------------------------------------------------------------------------------
**Update 2:**

So I think I've got an actual solution to this problem now.  Picking up from where I left off in the start of the post...

4- With the drive mounted successfully return to the HH gui and go to an icon for the drive (I used the icon on the desktop).  Right click and select “properties” then the “Drive” tab of the resulting pop-up.  On the “Drive” tab click “settings” to expand the options and delete anything that is in the three fields (Mount Point; File System; Mount Options) that appear.  Then select the “Volume” tab and click on “Settings” and clear the three fields that appear.  Click close on the bottom right side of the pop up.

5- Reboot the system with the drive attached.  It should restart with the drive mounted into a default location like /media/DriveLable.  At this point you are back where you started and can set a new mount point correctly.

---

### Post by editrix on 2008-08-09
Can't burn a CD: [https://bugs.launchpad.net/bugs/149076](https://bugs.launchpad.net/bugs/149076)

Two workarounds. One posted at the above URL that involves installing and configuring cdrecord, and one I just posted about using Wine and ImgBurn:
[http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700)

Just found a third: [http://ubuntuforums.org/showthread.php?p=5721644#post5721644](http://ubuntuforums.org/showthread.php?p=5721644#post5721644)

---

### Post by liam j dyer on 2008-08-14
[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

http://www.xtremetop100.com/in.php?site=1132252565[/url][/U][/B]

if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

---

### Post by zapree on 2008-08-17
Ok so last night i turn off my computer normal, and then turn it on in the morning and the ubuntu logo comes up status bar, it loads finishes, and then goes to a terminal window asking for my username/password.  Im stumped and not sure if the fix was in here.  Also before it asks for my username/password it comes up with kinit not loading, or something like that. Right now i am using the boot disk to try and find a solution without reinstalling the whole thing.
thanks a bunch
patrick

---

### Post by zapree on 2008-08-17
sorry for posting before looking elswhere, i found my answer by searching kinit seems it has happened to many people (and perhaps you have it as one of your solutions and i just diddnt find it)
thanks 
Patrick

---

### Post by bthoward on 2008-08-21
Gnome panel often crashes when clicking the clock to view the calendar.  

If you have enabled a google calendar in Evolution your calendar events are pulled in from google.  These are attempted to be displayed when you open the gnome calendar.  Sometimes this works but very often gnome-panel crashes.  Alt+F2 no longer works when in this state.

Do a CTRL+ALT+F1 then login and run killall gnome-panel then press ALT+F7 and gnome-panel will be automatically re-run and things will be back to normal.  Turn off the google calendar source in Evolution and the panel becomes MUCH more robust.

---

### Post by JolieRobert on 2008-08-22
Hi,
    I need to know what Syntax error represents.

---

### Post by JohnsShadow on 2008-08-22
dont forget the screen resolution problem

{run this in terminal}
gksu displayconfig-gtk

---

### Post by vadimash867 on 2008-08-25
Hello, i'm new in ubuntu and i have a problem, i've installed ubuntu on my laptop and whe i tried to set my wireless connection i saw that i need to install ndiswrapper , i downloaded it and when i tried to install it i got this error:


Userspace utilities for the ndiswrapper Linux kernel module
Some vendors do not release specifications of the hardware or provide a Linux driver for their wireless network cards. This project implements Windows kernel API and NDIS (Network Driver Interface Specification) API within Linux kernel. A Windows driver for wireless network card is then linked to this implementation so that the driver runs natively, as though it is in Windows, without binary emulation
 
And in add/remove panel i could'n install any aplication, i got this error AbiWord Word Processor cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type, can somebody help me, i tried the amd64 version too , the same problem, thx.

---

### Post by macvr on 2008-09-05
hi,
many might know this but adding to the list

if unable to access trash while using sudo nautlius
```
 gksudo nautilus
```

 workaround:>
```
gksudo dbus-launch nautilus
```

---

### Post by Penetration Testing on 2008-09-17
> **macvr said:**
> hi,
many might know this but adding to the list

if unable to access trash while using sudo nautlius
```
 gksudo nautilus
```

 workaround:>
```
gksudo dbus-launch nautilus
```
Thanks for that, that's been bugging me for ages.

---

### Post by Alex.peterson on 2008-09-18
Well this is amazing and fully recommended by the people. While this will get you to your drive without any problem the solution is not persistent. The same error returns after a reboot. The solution works on subsistent reboots.

---

### Post by sygrup on 2008-09-20
Thank you for your contribution

---

### Post by rpm13 on 2008-09-20
dapper to hardy is not an available installation path !!

Somewhere in the set {xfonts-scalable, xfonts-util, xfonts-base} the install breaks and then X shows only boxes.

See [http://ubuntuforums.org/archive/index.php/t-800574.html](http://ubuntuforums.org/archive/index.php/t-800574.html)
Also [http://ubuntuforums.org/showthread.php?t=921441](http://ubuntuforums.org/showthread.php?t=921441)
[https://bugs.launchpad.net/ubuntu/+source/xfonts-utils/+bug/54809](https://bugs.launchpad.net/ubuntu/+source/xfonts-utils/+bug/54809)

---

### Post by IanW on 2008-09-21
> **rpm13 said:**
> dapper to hardy is not an available installation path !!

Somewhere in the set {xfonts-scalable, xfonts-util, xfonts-base} the install breaks and then X shows only boxes.

See [http://ubuntuforums.org/archive/index.php/t-800574.html](http://ubuntuforums.org/archive/index.php/t-800574.html)
Also [http://ubuntuforums.org/showthread.php?t=921441](http://ubuntuforums.org/showthread.php?t=921441)
[https://bugs.launchpad.net/ubuntu/+source/xfonts-utils/+bug/54809](https://bugs.launchpad.net/ubuntu/+source/xfonts-utils/+bug/54809)

Hardly surprising considering you're trying to jump 4 generations in one leap!
Best bet would be to stop off at Feisty on the way (or backup your data & do a clean install).

---

### Post by frodon on 2008-09-21
The bug listed is marked as fixed. LTS to LTS upgrades are supported and should work without too much trouble.

---

### Post by rpm13 on 2008-09-22
> **IanW said:**
> Hardly surprising considering you're trying to jump 4 generations in one leap!
Best bet would be to stop off at Feisty on the way (or backup your data & do a clean install).

Well I had a similar problem going from dapper to edgy about a year and half ago. The problem showed in emacs but actually was that the xfonts were wrong. See my threads
[http://ubuntuforums.org/showthread.php?t=326773](http://ubuntuforums.org/showthread.php?t=326773)
[http://ubuntuforums.org/showthread.php?t=326876](http://ubuntuforums.org/showthread.php?t=326876)

It is sad that the xfonts mess is still with us four generations of ubuntu down. At that time only emacs showed the problem, now gnome/gdm/X itself is afflicted.

And that LTS to LTS does not work as claimed -- I spent four days with this one bug -- finally threw it out, fresh-installed hardy and now I have to replicate on it all my old stuff.

---

### Post by frodon on 2008-09-22
Please no discussion here, this thread is just to post bugs which have a known workaround.
If you want to discuss az specific bug please open a dedicated thread.

---

### Post by pbhj on 2008-09-23
> **AlanJM01 said:**
> Anything on the System Updater keeps locking up?

I have to xkill the system update each time.

It worked for a while and now it does not.

Not wanting to add to the problem - but the thread does say it's for solved/workaround-ed issues only. Make a thread for other problems then when you've got your workaround you can post here.

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

### Post by jARLAXL on 2008-10-11
**_A GNOME login without keypress dosn't set GNOME keyboard settings_**
- Workaround: [https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/196277) (e.g run setxkbmap)
- Bug report: [https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/196277)



**_Pulse audio problems:_**
- Workaround: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
- Bug reports:  [bug #198453]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453"), [bug #192888]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888"), [bug #239182]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182"), [bug #188226]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226") and [bug #190754]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754")

---

### Post by sananjana on 2008-10-24
Very  very useful comments, thanks for that,:lolflag::lolflag::lolflag::lolflag:

---

### Post by neighborlee on 2008-10-28
> **funnypanks said:**
> for excessive io activity in firefox 3b5 a more permenant solution is 
Edit>Preferences>Security and then uncheck the 2 boxes that start out "tell me if the site I'm visiting"

also if u have random exits (aka segmentation fault) in ff3b5 type this into terminal, don't worry youtube still works
sudo mv /usr/lib/libflashsupport.so /usr/lib/libflashsupport.so.org

i didn't come up with either fix but i don't remember where i read it either, but both are working for me

if u use vlc and firefox at the same time where u need audio in both, in my computer (acer 5580) audio will only work for one or the other, to get around this in vlc click 
settings>preferences>click advanced advanced settings at the bottom> then on the left pane fan out audio>click output modules> change from default to alsa audio output>click save at the bottom 
and your done

Or, for those less saavy with CLI, you can do alt-F2 and type that in, or for that matter just open synaptic and remove it . These little things can help keep converts instead of them running screaming back to windows/mac -whateva ;)

Its not only the advice we give sometimes, but the way its given that matters too,  as we aren't all geeks -this will change even more I suspect as vista users run away screaming from that  platform ? ( or run to them mac-who knows--;)

cheers
nl

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
love ubuntu!

---

### Post by 2hot6ft2 on 2008-12-26
Ooops wrong place sorry. Meant to post in the Intrepid thread.

---

### Post by ami_nakata on 2009-04-13
Bug:  Synaptic must automatically install packages listed in 'Recommends' field on install and upgrades in the default configuration if packages are to run as expected and without error. It doesn't do so for Hardy; a fix was released for Intrepid, but no backport to Hardy as yet. ( 13 Apr 2009 ) Problem documented in launchpad at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/8896](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/8896)

Workaround, by Christian Niemeyer, (with a typo correction by me, see below) is as follows: 

> Add an entry in the /etc/apt/apt.conf.d/ directory.
 Make a new file in there, e.g. sudo gedit 99recommends
 And paste
APT::Install-Recommends "true";
 into it.
 Go to Synaptic in Preference and just check if "consider recommendations as dependencies" is active, if not, check the box active.
 Then go >Synaptic >Settings >Filters,
Make a new one e.g. "Missing recommends"
Uncheck all boxes, only check the line "broken policy" (which means the apt policy in the config files)
 Reload package information (I guess it is not explicitly necessary).
 And with "Search filters" you have the Filter Missing Recommends.
 Christian's workaround also allows the user to see what the 'Recommends' are by creating a custom filter in Synaptic. ( Frodon, would you please double-check my understanding of that about the custom filter's purpose before editing this into the original post in this thread, if you intend to include it there?  Thanks! ) This workaround is documented in

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/8896/comments/28](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/8896/comments/28) and  [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/8896/comments/30](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/8896/comments/30) .
( That last link immediately above merely corrects a typo error, the necessity of which is confirmed by the workaround's poster, Christian Niemeyer, later in the thread, viz. at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/8896/comments/31](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/8896/comments/31) . )

---

### Post by jojom271 on 2009-08-22
**Re: file accidentaly placed in root file by frostwire** 			
 			 			 		   		 		 		it still will not let me 

root@jojom271-laptop:/home/jojom271# sudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6884): WARNING **: Unable to add monitor: Operation not supported
what is error 255

---

### Post by Schwalenberg on 2013-01-22
I was having a similar issue with the old Hardy bug involving sudo hostname resolution. I am using 12.10 quantal quetzal. It was not a bug in my case, probably a user error. Somehow during the install my hostname ended up being ubuntu instead of the hostname I chose. So while the /etc/hosts file had 127.0.1.1 hostname /etc/hostname said ubuntu. After some Google searches I came across this bug and in reading replies deduced that /etc/hosts should match /etc/hostname. I maybe stating the obvious but I didn't see it spelled out in any of the threads that are long since closed. They are however, the first answers that come up in searching this issue so I thought maybe someone should add a note in there that says "Make sure /etc/hosts 127.0.1.1 = /etc/hostname" type of deal. Or maybe this is spelled out better somewhere else and I just didn't know where to look.Just in case someone else has this problem of the mismatch after an install. Again it could very likely be user error but I do remember entering the name I wanted but somehow it only got to 1 out of 2 places it needed to be.

---

### Post by howefield on 2013-01-22
Old thread closed.

---

