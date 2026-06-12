---
title: "can't create successful leafpad/gedit file?!"
date: 2014-11-17
forum: General Help
---

### Post by lucy3 on 2014-11-17
Hi, I can't create new files with gedit/leafpad, tried both.

Typing [I]sudo gedit ~/etc/udev/rules.d/99-android.rules
[/I]
gets

```
lucy@lucy-N150P:~$ sudo gedit ~/etc/udev/rules.d/99-android.rules
[sudo] password for lucy: 

** (gedit:3418): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-RxGSRpiEGW: Connection refused

(gedit:3418): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

Tried with leafpad cos I'm a NOOB but it asked me where I wanted to save it. Probably should of exited but navigated to rules.d so now I have a txt file called 99-android.rules, (see screenshot) but when I try to edit permissions no such file, see terminal screenshot.

Help please,

Thanks

---

### Post by sudodus on 2014-11-17
You need superuser privileges for graphics apps (gksu, or sudo -H if you haven't got gksu installed). Try

```
gksudo gedit /etc/udev/rules.d/99-android.rules
```

If that does not work, you can try a text-only editor, for example nano

```
sudo nano /etc/udev/rules.d/99-android.rules
```

---

### Post by Dennis N on 2014-11-17
An option is to copy and paste the root-owned file you want to edit to your Desktop (without using sudo) where it will become owned by you. (Optionally) backup the original to the Desktop before editing. Open file from the Desktop with the text editor, edit, then save the edited file back to the Desktop. Last, copy it back to the original location with the terminal (using sudo) where it again (automatically) becomes owned by root.

---

### Post by Impavidus on 2014-11-17
Don't use sudo with leafpad or gedit, as sudodus explained.

Your first command, **sudo gedit [COLOR=#ff0000]~[/COLOR]/etc/udev/rules.d/99-android.rules**, tries to create a file somewhere in your home directory, signified by the ~. Most likely the directory **~/etc/udev/rules.d** doesn't exist. I'm not sure about gedit, but here on Xubuntu the default text editor refuses to save a file to a directory that doesn't exist.

Your next command is scrambled. You first used **ls** with a path to prove the presence of that file, but attached a sudo chmod command to it. Now **ls** thinks it has to print the file names or directory contents of
```
/etc/udev/rules.d/sudo
chmod
a+r
/etc/udev/rules.d/99-android.rules
```Only the last file exists. **chmod** doesn't run this way.

---

### Post by lucy3 on 2014-11-17
Thanks all, I have managed to create these files before. You will see in the screenshot that there is an android 51 android rules file. I'm following this tutorial [http://forums.androidcentral.com/verizon-galaxy-nexus-rooting-roms-hacks/147311-linux-guide-noobs-rooting-unlocking-locking-flashing.html](http://forums.androidcentral.com/verizon-galaxy-nexus-rooting-roms-hacks/147311-linux-guide-noobs-rooting-unlocking-locking-flashing.html). The android 51 file was created as a result as another followed guide, (didn't work.)

  The results of trying the suggested command by sudodus is shown in the screenshot. When it says that the 99-android file doesn't exist, doesn't the terminal command create the file? Sorry if you have answered this in the posts some of it reads like a different language.

---

### Post by sudodus on 2014-11-17
Now I see. There should be no tilde (~) character in the beginning of the file name, only a slash (/)

Edit: this is the risk with 'copy and paste': an error can survive longer, than when typed in all characters from the beginning.

---

### Post by lucy3 on 2014-11-17
Thanks sudodus,

Removed ~ but still get an error. :(

```
lucy@lucy-N150P:~$ sudo gedit /etc/udev/rules.d/99-android.rules
[sudo] password for lucy: 

** (gedit:3122): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-0Ff6qReGeN: Connection refused

```

Edit: no other errors when trying to save the file though.

---

### Post by mc4man on 2014-11-17
You really should stop using sudo gedit if on an ubuntu install after 13.04. While not the worst thing it could start creating some root owned files in your $HOME directory.
(- typically ~/.dbus, ~/.gvfs & temp ownership of ~/.local/share/recently-used.xbel

---

### Post by coldraven on 2014-11-17
You did not read Sudous' post carefully.
 For a GUI editor use 
```
gksu gedit /etc/udev/rules.d/99-android.rules
```
or for a text editor use
```
sudo nano /etc/udev/rules.d/99-android.rules
```

---

### Post by lucy3 on 2014-11-17
Mac4man - > You really should stop using sudo gedit if on an ubuntu install after  13.04. While not the worst thing it could start creating some root owned  files in your $HOME directory.
(- typically ~/.dbus, ~/.gvfs & temp ownership of ~/.local/share/recently-used.xbel 				 What should I use instead? sorry don't understand > - typically ~/.dbus, ~/.gvfs & temp ownership of ~/.local/share/recently-used.xbel

coldraven - > You did not read Sudous' post carefully I did but I obviously don't understand it. Used gedit before this and had no problem and I assume nano is an alternative to leafpad which I already tried, with errors resulting. 

What am I missing? sorry really confused now. I just want to plug in my phone with no udev error and have adb see the phone and I'm messing everything up, don't have permissions to copy and paste folders anymore. Really want to avoid a fresh install, is the damage repairable?

---

### Post by nerdtron on 2014-11-17
> I assume nano is an alternative to leafpad which I already tried, with errors resulting.
Relax. What errors are you having?

```
sudo nano /etc/udev/rules.d/99-android.rules 
```

If the file currently doesn't exist you'll be presented with a blank screen with some command shortcuts on the bottom. use arrow keys to navigate.
Now you should be able to type here what you want to type. Also copy  and paste works here just select and right click on the mouse.

Press Ctrl+o then Enter to save the file.
Press Ctrl+x to exit.

Now you have just saved a file.

---

### Post by Impavidus on 2014-11-17
sudo can make any program run as root, but it doesn't provide the full environment for root. If you run gedit, it may edit some config files (like ~/.dbus, ~/.gvfs) along with the files you want to edit. If you run gedit with sudo, those config files may become owned by root, and other applications will no longer be able to edit these config files and may no longer work. Worst case scenario is that your entire graphical environment can no longer work and you have to login on the console and fix the problem using a text-only interface. Using sudo -H or gksu the environment is changed, so that gedit no longer messes with user-owned config files. Non-GUI editors might change ownership of some files to root too,* but this should never break your GUI. This is because they are less integrated into the desktop environment.

gedit, nano, leafpad, mousepad, vim, nedit, kate, emacs, ed and many others are text editors, simple (not necessarily in use) programs that can edit text files – as you probably guessed. You can use any or all of them. Some of them, like nano or vim, run in a terminal and are quite safe to run with sudo, others, like gedit or leafpad, use a GUI and need more precautions when used as root. Don't worry too much because of the warnings you get from gedit or leafpad. They are just warnings, not errors.

__________________________
*: After a new install, the first thing I used vim for was changing fstab. This caused ~/.viminfo to be owned by root. It took a while before I noticed (the history wasn't saved) and the fix was easy.

---

### Post by lucy3 on 2014-11-17
Impavidus - thanks got it.

Nerdtron - no errors using Nano so I saved the file and exited. 

When I get to the next step in tutorial > Save the file and close your editor.  Now lets change permissions for android.rules:
[BOX="Command:"]ls /etc/udev/rules.d/sudo chmod a+r /etc/udev/rules.d/99-android.rules (I didn't include box etc)

I get ```
lucy@lucy-N150P:~$ ls /etc/udev/rules.d/sudo chmod a+r /etc/udev/rules.d/99-android.rules
ls: cannot access /etc/udev/rules.d/sudo: No such file or directory
ls: cannot access chmod: No such file or directory
ls: cannot access a+r: No such file or directory
/etc/udev/rules.d/99-android.rules]
```

But I just saved it successfully?

---

### Post by nerdtron on 2014-11-17
Are you sure your command has no typo?

I think it should be two commands, executed one after the other.
```
ls /etc/udev/rules.d

sudo chmod a+r /etc/udev/rules.d/99-android.rules
```

---

### Post by lucy3 on 2014-11-17
Well I feel sheepish! ;) Thank you. However after ALL that I still get an error connecting my phone. I posted about it a few days ago with no replies yet. I'd be grateful if someone could help me out. Thread [http://ubuntuforums.org/showthread.php?t=2252795](http://ubuntuforums.org/showthread.php?t=2252795) Thanks for your patience.

---

