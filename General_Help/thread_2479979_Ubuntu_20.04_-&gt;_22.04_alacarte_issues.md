---
title: "Ubuntu 20.04 -&gt; 22.04 alacarte issues"
date: 2022-10-14
forum: General Help
---

### Post by cscj01 on 2022-10-14
I just upgraded Ubuntu from 20.04 to 22.04.  I use Gnome Flashback as my desktop.  When I want to edit Menu items, I usually use Main Menu from the pop-up menu and select the application there.   However, after the upgrade, nothing happens if I click Properties.  So I ran alacarte in a terminal .  The terminal messages are :```
$ alacarte

(alacarte:74316): Gtk-CRITICAL **: 13:17:05.553: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(alacarte:74316): Gtk-CRITICAL **: 13:17:05.553: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(alacarte:74316): Gtk-WARNING **: 13:17:10.451: Could not load a pixbuf from icon theme.
This may indicate that pixbuf loaders or the mime database could not be found.
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 451, in on_properties_button_clicked
    self.on_edit_properties_activate(None)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 327, in on_edit_properties_activate
    editor = Editor(self.main_window, file_path)
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 135, in __init__
    self.load()
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 227, in load
    self.set_icon('icon-image', "Icon")
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 166, in set_icon
    set_icon_string(self, self.builder.get_object(ctl), val)
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 91, in set_icon_string
    set_icon_file(editor, image, icon)
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 76, in set_icon_file
    pixbuf = GdkPixbuf.Pixbuf.new_from_file_at_size(file_name, size, size)
gi.repository.GLib.GError: g-file-error-quark: Failed to open file “/var/lib/app-info/icons/ubuntu-focal-universe/64x64/luckybackup_luckybackup.png”: No such file or directory (4)

```I see that the last line is referring to a locations that is from 20.04 and is no longer there.  Where do I change the settings so the location is correct?  I have a /var/lib/app-info/icons/ubuntu-jammy-universe which contains the icon.

---

### Post by Holger_Gehrke on 2022-10-14
The icons files in /var/lib/app-info/icons are cached there by gnome-software / snap-store / ubuntu-store or whatever other name they come up with for that thing. There are icons in there for programs that can be installed and possible are. Installed programs have their icons in /usr/share/icons/ or / usr/share/pixmaps/ and these don't change when you upgrade to a newer version of Ubuntu.

Alacarte reads the .desktop files for the programs, so you have to find the .desktop for luckybackup and edit that. Like a lot of configuration on a Linux system it's a simple text file. The structure of the file should be obvious after reading a few of them, but you can also find the specification on [freedesktop.org]("https://specifications.freedesktop.org/desktop-entry-spec/latest/"). The file should be in /usr/share/applications/ or possibly in ~/.local/share/applications/.

Holger

---

### Post by cscj01 on 2022-10-14
> **Holger_Gehrke said:**
> The icons files in /var/lib/app-info/icons are cached there by gnome-software / snap-store / ubuntu-store or whatever other name they come up with for that thing. There are icons in there for programs that can be installed and possible are. Installed programs have their icons in /usr/share/icons/ or / usr/share/pixmaps/ and these don't change when you upgrade to a newer version of Ubuntu.

Alacarte reads the .desktop files for the programs, so you have to find the .desktop for luckybackup and edit that. Like a lot of configuration on a Linux system it's a simple text file. The structure of the file should be obvious after reading a few of them, but you can also find the specification on [freedesktop.org]("https://specifications.freedesktop.org/desktop-entry-spec/latest/"). The file should be in /usr/share/applications/ or possibly in ~/.local/share/applications/.

Holger

I appreciate your reply.  I searched the system for luckybackup.desktop files.  I examined each one and can find nothing that would lead me to ubuntu-focal-universe.  I also searched for ubuntu-focal-universe and found nothing (which I suppose is to be expected).  This is an enigma to me.

---

### Post by vanadium on 2022-10-15
An upgrade is not always flawless, because, and this appears here, old configuration may be left behind that may cause an app to malfunction.

As a first check, it is always good to create a temporary second account, and see whether the problem happens there. If yes, you know the issue is system wide. Otherwise it is an issue in the configuration stored in your user account.

If it is system wide, purging and reinstalling the program likely will help: that removes (old) configuration data at the level of the system.

```

sudo apt autoremove --purge alacarte
sudo apt install alacarte

```

If it is only happening in your own account, hunt for hidden configuration files/directories in your home folder and delete it. It will be recreated next time you start the program.

---

### Post by cscj01 on 2022-10-15
> **vanadium said:**
> An upgrade is not always flawless, because, and this appears here, old configuration may be left behind that may cause an app to malfunction.

As a first check, it is always good to create a temporary second account, and see whether the problem happens there. If yes, you know the issue is system wide. Otherwise it is an issue in the configuration stored in your user account.

If it is system wide, purging and reinstalling the program likely will help: that removes (old) configuration data at the level of the system.

```

sudo apt autoremove --purge alacarte
sudo apt install alacarte

```

If it is only happening in your own account, hunt for hidden configuration files/directories in your home folder and delete it. It will be recreated next time you start the program.

If I remove alacarte and then install, will the system add back all the applications/programs that are currently there?

---

### Post by vanadium on 2022-10-16
You just remove and reinstall a single program.

---

### Post by cscj01 on 2022-10-16
> **vanadium said:**
> You just remove and reinstall a single program.

I meant to say would all the applications/programs that were in alacarte be in the reinstalled alacarte that were there before I deleted and reinstalled the programs.  I worded it incorrectly.

---

### Post by Holger_Gehrke on 2022-10-16
> **cscj01 said:**
> I meant to say would all the applications/programs that were in alacarte be in the reinstalled alacarte that were there before I deleted and reinstalled the programs.  I worded it incorrectly.

The menu system exist independently of alacarte, the program only allows you to create,edit, and delete menu items. Think back to when you first installed alacarte. Did you have to do anything to have the programs that were already installed come up in alacarte ? Unless you're using a very different build of alacarte you didn't.

Holger

---

### Post by cscj01 on 2022-10-16
Thanks.  I started with Ubuntu back when Gnome desktop was Flashback.  I guess I never thought of it before.  I'll give it a go.

---

### Post by cscj01 on 2022-10-16
Well, I uninstalled alacarte and then installed.  No change in behavior.  I guess I'm going to have to find the offending file in one of the many files I have.  I'll re-post when I know more.

---

### Post by vanadium on 2022-10-17
I can assume you removed and reinstall according to the commands I gave? That is important to also remove old system configuration data.

Other possibility: old user configuration in your own account. Test by temporarily creating a new account, and see how alacarte behaves there.

---

### Post by rag2 on 2022-12-18
Also had an issue with **alacarte** not performing correctly under 22.04 GNOME Flashback. The instant solution was to install **menulibre**, which, so far, has performed correctly.

---

