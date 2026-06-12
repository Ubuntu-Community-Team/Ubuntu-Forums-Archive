---
title: "Sound Software Messed Up Everything"
date: 2014-08-02
forum: General Help
---

### Post by stinkyboner on 2014-08-02
Hi,

I was looking for an easy way to switch the default sound output in Lubuntu to my usb headphones and I found a thread on some forum where some idio.. guy suggested installing some program called veromix.

I installed it, and it has messed up everything. When I start lubuntu I get 3 error messages, most likely because of gnome software.

To even get firefox to run I have to run it as root now or else I get these errors:
```
null@nothing:~$ firefox

(process:2685): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(firefox:2685): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(firefox:2685): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(firefox:2685): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(firefox:2685): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
Could not create gnome accelerators directory `/home/null/.gnome2/accels': Permission denied
null@nothing:~$ 

```

And to put the icing on the cake, my sound no longer works at all.

Can someone help me sort this out?

---

### Post by Bucky Ball on 2014-08-02
How did you install it? If via the Software Centre, can you uninstall, open a terminal and run these four commands:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report back any errors.

I suggest you use the more conventional Pulseaudio Volume Control (if you have Pulse installed, of course, and not sure if that is default in Lubuntu). With that, get a stream going (play some music), open PAVControl, hit the Playback tab and experiment. You should see the sound stream playing. You can also experiment with the Output tab options. You should see your headphones and be able to set it to that. It sometimes just takes a little tweaking. Good luck.

---

### Post by claracc on 2014-08-02
Well, other way to uninstall package and its config files (if any) with the following commands:

First of all, open a xterm: ```
ctrl+alt+t
```

Then in this xterm, run the remove veromix package:

```
sudo apt-get remove --purge veromix
```

Then run the four commands forementioned by Bucky Ball.

Also, it is a very bad idea to run firefox as root, it is a security risk, so don't do that.

And last, here you have a comprehensive guide for troubleshouting audio problems: 

[https://wiki.ubuntu.com/Audio](https://wiki.ubuntu.com/Audio)

---

### Post by stinkyboner on 2014-08-02
> **Bucky Ball said:**
> How did you install it? If via the Software Centre, can you uninstall, open a terminal and run these four commands:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report back any errors.

I suggest you use the more conventional Pulseaudio Volume Control (if you have Pulse installed, of course, and not sure if that is default in Lubuntu). With that, get a stream going (play some music), open PAVControl, hit the Playback tab and experiment. You should see the sound stream playing. You can also experiment with the Output tab options. You should see your headphones and be able to set it to that. It sometimes just takes a little tweaking. Good luck.

I installed veromix via sudo apt-get install veromix.

I just uninstalled via sudo apt-get remove veromix
Then I ran all those commands and rebooted and still the same errors on startup and can't run firefox unless i run it as root.

here's a screenshot of the errors I'm getting. when I reboot.

[IMG]http://i.imgur.com/t7OGlXe.png[/IMG]

I think veromix installed some gnome crap and it's conflicting with stuff on my lubuntu distro, idk?

EDIT:

I'd like to add that my sound is now working through my usb headphones, I'm afraid to unplug them and see if my speakers are working.

---

### Post by stinkyboner on 2014-08-02
> **claracc said:**
> Well, other way to uninstall package and its config files (if any) with the following commands:

First of all, open a xterm: ```
ctrl+alt+t
```

Then in this xterm, run the remove veromix package:

```
sudo apt-get remove --purge veromix
```

Then run the four commands forementioned by Bucky Ball.

Also, it is a very bad idea to run firefox as root, it is a security risk, so don't do that.

And last, here you have a comprehensive guide for troubleshouting audio problems: 

[https://wiki.ubuntu.com/Audio](https://wiki.ubuntu.com/Audio)

I uninstalled it via sudo apt-get remove before I saw your post.. I'm still having the problems, but now the sound has begun to work through my usb headphones.

Here are some errors firefox is spitting out:
```
(firefox:1592): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::activate-slider' of type `gboolean' from rc file value "((GString*) 0x7f5023e8afa0)" of type `GString'
Home directory not accessible: Permission denied
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::activate-slider' of type `gboolean' from rc file value "((GString*) 0x7f5023e8aea0)" of type `GString'
```

Do you think it's because veromix installed some gnome crap and it's conflicting with lubuntu/openbox/gtk stuff?

---

### Post by claracc on 2014-08-02
Really, I don't know, but it seems to be the situation.

If you have synaptic package manager installed in your system, you can look for veromix package in it and clicking on properties-->dependencies, see what other packages were installed as dependencies. (Or perhaps look for it with history menu)

I have explored my system, ubuntu 12.04, and the only reference ( not installed) to veromix is plasma-widget-veromix, which dependencies are listed in the attached image:

---

### Post by stinkyboner on 2014-08-02
> **claracc said:**
> Really, I don't know, but it seems to be the situation.

If you have synaptic package manager installed in your system, you can look for veromix package in it and clicking on properties-->dependencies, see what other packages were installed as dependencies. (Or perhaps look for it with history menu)

I have explored my system, ubuntu 12.04, and the only reference ( not installed) to veromix is plasma-widget-veromix, which dependencies are listed in the attached image:

Thanks for the help, if I encounter problems in the future I'll probably stop being lazy and do that.

For now, I've found working solutions to both of my problems. Although, they're probably not the best solution as I'm still getting weird glib errors when launching firefox. I'll post them in case others have this problem in the future.

To fix the error message popups on boot:
```
ls /var/crash/
```
If there are any files in that directory then:
```
sudo rm -r /var/crash/*
```

Then, I figured out that if you run software that writes files/folders in your home directory as root, and it writes them as root, your regular user account doesn't have permission to view these files/folders.

This is why Firefox wasn't starting, it wanted to read some some folders/files owned by root in my home directory. Kind of stupid I guess, but to fix it make sure you are in your home directory, and are not root!

then:
```
sudo chown -R null:null ./
```
substitute null:null with your own username:usergroup

Lesson learned, never install veromix ever again.

---

### Post by claracc on 2014-08-02
You are welcome. Glad you got fixed your problem.

As I can see the problem was that the installation of the package had changed the permissions and ownwer of certain files in you home directory and firefox couldn't read them with your user permissions, isn't it?. Is if it in this way, I think the software and the installation are doing  things in the wrong way.

If you think the problem is solved, please mark the thread as solved with thread toolsin the right upper part of the webpage.

Thanks.

---

