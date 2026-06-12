---
title: "just Installed 16.04"
date: 2017-02-28
forum: General Help
---

### Post by rickrodriguez1971 on 2017-02-28
and I tried Terminal with Sudo Nautilus
this is what I get...bad installation?
I am not putting anything in, just that

```

(nautilus:1944): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:1944): CRITICAL **: Another desktop manager in use; desktop window won't be created
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
```

any suggestions?

---

### Post by Bucky Ball on 2017-02-28
Not that it will make much difference, but you should never be opening GUIs with 'sudo'. 

```
gksudo nautilus
```

Any good reason you need to open Nautilus as root? Not the greatest idea if you just intend to 'look around'. Avoid, particularly if you are new to Ubuntu and, as yet, have little idea. ;)

Better to tell us what you want to do and see if there's a better way of doing it. As for bad install: doubtful, but let's dig. Try 'gksudo' and let us know.

Suggest you also run these three commands, hitting return after each. 

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

These won't upgrade your release to a newer one. Incidentally, when you use sudo (or gksudo) you will be asked for your password. You must put that in. It will be invisible. This is a security thing and is normal.

PS: Please put terminal output between code tags. See the green link in the first line of my signature at the bottom of this post for how.

---

### Post by rickrodriguez1971 on 2017-02-28
well I just want to be able to install programs as needed such as printer, graphics drivers, Netflix and such

---

### Post by rickrodriguez1971 on 2017-02-28
I tried your suggestion and It still doesn't look like it will allow me to install anything correctly, I have used Window$ and Zorin for some time

---

### Post by Bucky Ball on 2017-03-01
> **rickrodriguez1971 said:**
> well I just want to be able to install programs as needed such as printer, graphics drivers, Netflix and such

Trying to open Nautilus as root has nothing to do with installing programs. The command I gave you has nothing to do with installing programs. Nothing in your support thread so far has suggested you are having trouble with installing programs or programs at all. Your thread so far has been about something unrelated: attempting to open Nautilus as root.

Did you get any errors from the commands I asked you to run and if so post them here between code tags, please.

So what is your problem with installing programs? If you want to install programs, you can use the package manager, whichever it is that you're using. As for the rest, tackle each in an individual thread. You want to know how to install your printer? Start a thread with a title that suggests that and give full details of your printer, what you've tried and where you're stuck. Graphics drivers? You may not even need to install any ...

And so on ... be specific and you have a much better chance of getting support. :)

---

### Post by vasa1 on 2017-03-01
Whenever you report terminal output, please include the *exact* command(s) that generated the output.

You mentioned > ... I tried Terminal with Sudo NautilusIt's always *_s_udo*, not *_S_udo*. Most applications are also lower case. Case is very important. The terminal is _not_ case-insensitive.

Also please use a thread title that describes what you need help with. There are some helpful suggestions in [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945") and in the first post in [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

---

