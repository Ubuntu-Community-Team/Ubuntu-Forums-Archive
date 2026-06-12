---
title: "Firefox and Audacity not starting"
date: 2014-01-22
forum: General Help
---

### Post by carrier-simon on 2014-01-22
Hi,

I know the 2 program are not related. I'm also more or less new to Ubuntu. I have Ubuntu 13.10 64 bit.  I might have tweak something while installing something else and there's a conflict somewhere, I don't know. When I try to start Firefox or Audacity, their icon flash on the launcher bar (dock) but nothing else happen. I have try to open a lot of my other program and everything work fine with all the other I tried. I did uninstall Audacity and Firefox and reinstall them and still no luck.

I try what is explain in : [http://ubuntuforums.org/showthread.php?t=1919977](http://ubuntuforums.org/showthread.php?t=1919977) but I can't find /usr/bin/     I did find a file name firefox to rename it in /usr/lib/firefox but I can't rename it. I can copy it, paste it somewhere else, rename it, but I can not paste it back it the /usr/lib/firefox folder.

---

### Post by deadflowr on 2014-01-22
/usr/bin, is a system folder, look in the file manager and on the left side panel should be an option for "Computer".
Most program executables are in there.

Basically though, I would suggest that you open the program "Terminal", and try running the programs by name
you should be able to run them with just the name, without the filepath.
Example
```
firefox
```
as a opposed to /usr/bin/firefox.
Post the output of what the terminal says.
Please use the code tags option
code tags are the # symbol in the new reply box)

---

### Post by carrier-simon on 2014-01-22
Thanks for the fast reply. I'm not sure if it is what you ask me to do, but I open the terminal and type firefox. Below is what I got

```
sg@SG-Desktop:~$ firefox

(process:19107): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(firefox:19107): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(firefox:19107): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(firefox:19107): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(firefox:19107): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
Could not create gnome accelerators directory `/home/sg/.gnome2/accels': Permission denied



```

and I did the same with Audacity :

```
sg@SG-Desktop:~$ audacity

(process:19130): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(process:19130): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(process:19130): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(process:19130): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
Could not create gnome accelerators directory `/home/sg/.gnome2/accels': Permission denied



```

---

