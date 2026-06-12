---
title: "Can't open folders/home directory"
date: 2016-10-20
forum: General Help
---

### Post by kashir on 2016-10-20
Hello!

I have Ubuntu 16.04, fresh install no partitions etc
Maybe is related: I have an ambiance/radiance theme pack and is enabled ([http://www.ravefinity.com/p/download-ambiance-radiance-colors.html](http://www.ravefinity.com/p/download-ambiance-radiance-colors.html))

When I sign in my session, I can open my home folder with a mouse clic in "Files", pinned in the dock, but later, for apparently no reason, it does not open anymore.
I clic and then the icon start glowing but nothing happens.

Some things I tried in terminal searching this problem

**nautilus** (it took a good long time)```
(nautilus:4302): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed


(nautilus:4302): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
No se pudo registrar la aplicación: Se alcanzó el tiempo de expiración


(nautilus:4302): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(nautilus:4302): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(nautilus:4302): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
```[B]

nautilus -q[/B] (it took a good long time)```
(nautilus:4291): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:4291): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
No se pudo registrar la aplicación: Se alcanzó el tiempo de expiración


(nautilus:4291): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(nautilus:4291): GLib-GObject-WARNING **: invalid (NULL) pointer instance



(nautilus:4291): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
```[B]

sudo nautilus
[/B]This opened a Files window, but prints this error in terminal:
```
(nautilus:5051): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (nautilus:5051): CRITICAL **: Another desktop manager in use; desktop window won't be created
Nautilus-Share-Message: Called "net usershare info" but it failed: Falló al ejecutar el proceso hijo «net» (No existe el archivo o el directorio)
```

**sudo nautilus -q ** (it took a good long time)
```
(nautilus:5121): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:5121): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
No se pudo registrar la aplicación: Se alcanzó el tiempo de expiración


(nautilus:5121): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(nautilus:5121): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(nautilus:5121): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
```

**sudo apt-get install --reinstall nautilus**
This executes without problem, but error still persists.
[B]
Also, I tried to login in guest session and the same occurs. I can open FIles/Folders at the beginning but in a time I can't.[/B]

Thanks!

---

### Post by ajgreeny on 2016-10-20
Unfortunately using **sudo nautilus** might be part of the reason for this problem as it can change the ownership of files and folders in your home to root.

If you want or need to use nautilus with root permissions you must use **gksudo nautilus**, I think you will have to install gksudo first, or even simpler use **sudo -H nautilus**.

However, to get things working again, let's see the output in terminal of command ```
sudo ls -la /home/kashir
```assuming your username is kashir; change it if you use something else.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by kashir on 2016-10-20
Thanks for your reply. Here is the output:

```
total 264
drwxr-xr-x 35 kashir kashir  4096 oct 20 22:25 .
drwxr-xr-x  3 root   root    4096 sep 28 14:20 ..
drwxrwxr-x  9 kashir kashir  4096 oct 17 11:01 .atom
-rw-------  1 kashir kashir 20520 oct 20 22:21 .bash_history
-rw-r--r--  1 kashir kashir   220 sep 28 14:20 .bash_logout
-rw-rw-r--  1 kashir kashir   200 sep 28 19:51 .bash_profile
-rw-r--r--  1 kashir kashir  3955 sep 28 19:59 .bashrc
drwx------ 29 kashir kashir  4096 oct 20 21:50 .cache
drwx------  3 kashir kashir  4096 sep 29 04:05 .compiz
drwx------ 32 kashir kashir  4096 oct 20 18:16 .config
drwx------  3 root   root    4096 sep 28 15:30 .dbus
drwxr-xr-x  2 kashir kashir  4096 oct 20 22:18 Desktop
-rw-r--r--  1 kashir kashir    25 sep 28 14:26 .dmrc
drwxr-xr-x  5 kashir kashir  4096 oct 20 18:15 Documents
drwxr-xr-x  3 kashir kashir  4096 oct 20 18:15 Downloads
-rw-r--r--  1 kashir kashir  8980 sep 28 14:20 examples.desktop
drwx------  4 kashir kashir  4096 oct 20 22:25 .gconf
drwxrwxr-x  3 kashir kashir  4096 sep 28 19:53 .gem
-rw-rw-r--  1 kashir kashir    23 sep 28 19:53 .gemrc
drwxr-xr-x 24 kashir kashir  4096 oct 17 09:36 .gimp-2.8
-rw-rw-r--  1 kashir kashir   100 sep 28 20:17 .gitconfig
drwx------  3 kashir kashir  4096 sep 28 14:39 .gnome
drwx------  3 kashir kashir  4096 oct 20 22:25 .gnupg
drwx------  2 root   root    4096 sep 28 15:31 .gvfs
-rw-------  1 kashir kashir 10894 oct 20 22:25 .ICEauthority
-rw-rw-r--  1 kashir kashir   123 sep 29 06:25 .irb-history
drwxrwxr-x  3 kashir kashir  4096 oct 17 12:31 ironhack
drwx------  5 kashir kashir  4096 sep 28 18:00 .local
-rw-rw-r--  1 kashir kashir    68 sep 28 19:51 .mkshrc
drwx------  4 kashir kashir  4096 sep 28 14:29 .mozilla
drwxr-xr-x  2 kashir kashir  4096 oct 20 18:14 Music
drwxrwxr-x  2 kashir kashir  4096 oct  8 04:12 .nano
drwx------  3 kashir kashir  4096 sep 29 03:47 .nv
-rw-r--r--  1 kashir kashir   255 oct 20 18:11 .pam_environment
drwxr-xr-x  3 kashir kashir  4096 oct 20 18:15 Pictures
drwx------  3 kashir kashir  4096 sep 28 14:39 .pki
-rw-r--r--  1 kashir kashir   841 sep 28 19:51 .profile
-rw-------  1 kashir kashir   548 oct 20 12:35 .pry_history
drwxr-xr-x  2 kashir kashir  4096 oct 20 18:14 Public
-rw-------  1 kashir kashir   256 oct  4 02:22 .pulse-cookie
drwxrwxr-x 12 kashir kashir  4096 sep 28 20:16 .rbenv
drwxrwxr-x 25 kashir kashir  4096 sep 28 19:51 .rvm
drwx------  2 kashir kashir  4096 sep 28 20:36 .ssh
drwxrwxr-x  2 kashir kashir  4096 oct 20 14:09 .steam
lrwxrwxrwx  1 kashir kashir    31 oct 20 14:09 .steampath -> /home/kashir/.steam/bin32/steam
lrwxrwxrwx  1 kashir kashir    29 oct 20 14:09 .steampid -> /home/kashir/.steam/steam.pid
-rw-r--r--  1 kashir kashir     0 sep 28 14:46 .sudo_as_admin_successful
drwxrwxr-x  4 kashir kashir  4096 oct 20 21:01 .TelegramDesktop
drwxr-xr-x  2 kashir kashir  4096 oct 20 18:14 Templates
drwxrwxr-x  2 kashir kashir  4096 oct 20 17:02 Tests
drwx------  3 kashir kashir  4096 sep 29 03:56 .thumbnails
drwx------  4 kashir kashir  4096 sep 28 20:50 .thunderbird
drwxr-xr-x  2 kashir kashir  4096 oct 20 18:14 Videos
-rw-------  1 kashir kashir    54 oct 20 22:25 .Xauthority
-rw-rw-r--  1 kashir kashir   131 oct 20 18:10 .xinputrc
-rw-------  1 kashir kashir    82 oct 20 22:25 .xsession-errors
-rw-------  1 kashir kashir  1227 oct 20 22:25 .xsession-errors.old
-rw-rw-r--  1 kashir kashir   118 sep 28 19:51 .zlogin
-rw-rw-r--  1 kashir kashir    68 sep 28 19:51 .zshrc



```

Anyway, I read a lot about Nautilus and looks like people is a bit upset with it. I installed Nemo and set as default file manager (using this tutorial [http://www.noobslab.com/2013/10/nemo-file-manager-with-extensions-for.html](http://www.noobslab.com/2013/10/nemo-file-manager-with-extensions-for.html)) and at the beginning all was perfect, but now I am suffering some issues :( like I can't see my wallpaper, some configs resets at start, etc

I am thinking in delete everything, do a fresh install of Ubuntu and install Nemo without touching anymore, and ignore Nautilus forever xD

PS: Sorry, did i a bad use of the code format in my first post? I thought I did well :(

---

### Post by monkeybrain20122 on 2016-10-20
I have experienced the same a few times, got the same errors as you did when I tried open it with the terminal. But this happens only a few times  (3 or 4?) and only after some intense usage (like compiling something big for a long time) A reboot always fixes it. So I assumed I might have done something to corrupt the session and just leave it at that.

 I never gksudo Nautilus , not my habit.

---

### Post by kashir on 2016-10-20
That's exactly my current situation. I am doing an intense usage everyday.
I am in a bootcamp of web development and I am like 8 hours coding and compiling ruby on rails and other stuff :o

But reboot does not fix anything for me xD

---

### Post by ajgreeny on 2016-10-20
```
drwx------  3 root   root    4096 sep 28 15:30 .dbus
drwx------  2 root   root    4096 sep 28 15:31 .gvfs
```
These two entries are both incorrect as they must be owned by you as user, not by root as they are at present.

As a start run command ```
sudo chown -R kashir:kashir /home/kashir
``` to see if that changes things for you.

---

### Post by kashir on 2016-10-21
Hey. I added that command as start run command, but .dbus and .gvfs keeps with root owner :(

I really appreciate your time and help, but I was forced to format yesterday because I need my environment working 24/7
In another situation I would keep trying real solutions, for my learning and yours. Sorry.

Greetings and thanks.

---

### Post by CantankRus on 2016-10-21
> **kashir said:**
> 
Anyway, I read a lot about Nautilus and looks like people is a bit upset with it. I installed Nemo and set as default file manager (using this tutorial [http://www.noobslab.com/2013/10/nemo-file-manager-with-extensions-for.html](http://www.noobslab.com/2013/10/nemo-file-manager-with-extensions-for.html)) and at the beginning all was perfect, but now I am suffering some issues :( like I can't see my wallpaper, some configs resets at start, etc

I am thinking in delete everything, do a fresh install of Ubuntu and install Nemo without touching anymore, and ignore Nautilus forever xD

If you want to use nemo as your default file browser
I suggest you allow nautilus to keep drawing the desktop as 
this allows you to still change backgrounds using **System Settings > Appearance**

After installing nemo I set it as the default and then run these gsettings commands 
to make sure nautilus still draws the desktop. No need to autostart nemo.
```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
gsettings set org.gnome.desktop.background show-desktop-icons true
gsettings set org.nemo.desktop show-desktop-icons false
```

Ubuntu hides the system startups from startup applications.
To see them run...
```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
```

You should see a "Files" entry with **nautilus -n** set as the command.

---

