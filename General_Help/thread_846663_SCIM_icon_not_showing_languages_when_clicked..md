---
title: "SCIM icon not showing languages when clicked."
date: 2008-07-01
forum: General Help
---

### Post by akshar_patel_47 on 2008-07-01
I had scim before in my previous ubuntu 8.04. But due to some reasons I had to reinstall the whole the ubuntu. Now I don't remember how I configured it before but now I'm stuck with just the icon appearing in the main panel.

When I click the panel, ideally the languages whose tables are installed should be displayed, but now nothing appears.

Please help me friends!

---

### Post by akshar_patel_47 on 2008-07-01
when I try to restart it, it gives me the following error.

Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to launch SCIM.

---

### Post by Popaul on 2008-09-12
Hello akshar-patel-47!
Did you get any success in the end? I am having same problem. All solutions I found on the forum are of no help so far.
Thank you in advance!

---

### Post by Popaul on 2008-09-12
> **akshar_patel_47 said:**
> when I try to restart it, it gives me the following error.

Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to launch SCIM.

:)Fixed, but the hard way. Probably some file was corrupted in the end.
So, what I did:

system: Ubuntu Hardy Heron 8.04 up-to-date
Started Synaptic through menu system/Administration/Synaptic Package Manager
Search for "scim"
All file with 'scim' in their name: marked them for Complete Removal (I guess if just 'removal', some files will be left on the system and will be used again during the next install, so problem).
Some files are automatically marked for removal once you mark 'scim' for example. I made sure that all these are really marked for Complete Removal.
That removes all the language support files (files starting with language...).
CTRL+Alt+Bckspce to log out and log-in so that the changes get some effects.
Then I went to menu System/Administration/Language Support
I ticked the languages I wanted to add. The system then re-installed automatically all the files needed. Oooops... as I wanted Japanese and Chinese (I suppose that is valid also for Thai, Vietnamese or some others languages like these): I checked the box Input method: Enable support to enter complex characters. And of course I verified that the Default Language was the correct one, i.e. my locale.
But it installs only SCIM alone, which is not good enough for Hardy.
So back to Synaptic, search for 'scim' and select for installation all the 4 scim-bridge-... files (agent, gtk...), as Hardy needs the bridges to use SCIM.
Re log-out and log-in, and... the little applet liek a keyboard was up there. Right-click to open the SCIM setup, menu 'GTK' to select 'Toolbar/Show' "Always" (or "On Demand"... up to you) and a little square with "SCIM" on it appear magically in the lower right corner of the screen. And... OOWriter opened, did ctrl+space and the SCIM toolbar opened: I could select any of the languages I've checked in Language Support and it works. Paradise.

---

### Post by Zorael on 2008-09-12
edit: Guess I was too slow. Oh well. +1!

Did you redirect your xinput alternatives to scim? (That makes sense, right? :>)

Try this. It's what I do for KDE, but should hopefully do the trick in Gnome, too.

Make a backup of your **/etc/X11/xinit/xinput.d/skim** file, and overwrite the original file with the following.
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
    GTK_IM_MODULE=scim
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi

DEPENDS="skim, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```
Then enter the following in a terminal.
```
$ sudo aptitude install ~nscim-bridge
$ for X in `ls -w1 /etc/alternatives/xinput*`; do sudo update-alternatives --config $X; done
```
After entering that last line, pick **scim** in all the dialog windows that spawn, whenever possible. If it's not there, no worries, hopefully won't mess things up.

And lastly, of course, set up your languages in **scim-setup**, if you haven't already. Run it from a run box (Alt+F2) or a terminal.

---

