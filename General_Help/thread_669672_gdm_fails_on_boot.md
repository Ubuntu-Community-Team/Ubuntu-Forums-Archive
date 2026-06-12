---
title: "gdm fails on boot"
date: 2008-01-16
forum: General Help
---

### Post by Plaguester on 2008-01-16
I've been using ubuntu 7.10 for about a month now and managed to get my system all fubared yesterday.

Yesterday I did two things: updated the system with the package manager (last update was a couple of days ago) and tried to install glib-2.0.7 and rythmbox 0.11.4. After doing this, today I noticed that I could only run the apps that were already open (firefox and the like) and could not open new windows. When I tried opening apps in the terminal, I consistently get a "undefined symbol" message. I then tried restarting but now gdm fails to start at all. I have logged in to the command line and tried a couple of things that I found on google to no avail.

Any help would be greatly appreciated!

---

### Post by rocketman768 on 2008-01-16
Well, what does /var/log/Xorg.0.log say? If you can't figure it out from that, post it here so we can see.

---

### Post by kellemes on 2008-01-16
> **Plaguester said:**
> When I tried opening apps in the terminal, I consistently get a "undefined symbol" message.


Can you please post the complete message you're getting?
Or is this it?

---

### Post by Plaguester on 2008-01-16
Exact message is as follows:

gdm: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled

I'm working on getting the contents of /var/log/Xorg.0.log on here, but I can't seem to get my usb drive working through the command line.

---

### Post by SunnyRabbiera on 2008-01-16
hmm, well see if you can go into a terminal and put in sudo apt-get install-kdm...

---

### Post by rocketman768 on 2008-01-16
So, did you already try:

```
sudo aptitude reinstall libgtk2.0-0
```

---

### Post by Plaguester on 2008-01-16
> **rocketman768 said:**
> So, did you already try:

```
sudo aptitude reinstall libgtk2.0-0
```

I have now, but I still get the same error.

---

### Post by Plaguester on 2008-01-17
/var/log/Xorg.0.log is attached.

---

### Post by rocketman768 on 2008-01-17
Alright, that log looks fine to me. Looks like that log was from when everything was working fine. You have a warning in there (WW), but no errors (EE). I suppose this means that the error is  not even letting X create new logs.

I also searched and found out that g_signal_accumulator_true_handled is a functioned defined by glib. Look here: [http://www.gtk.org/api/2.6/gobject/gobject-Signals.html]("http://www.gtk.org/api/2.6/gobject/gobject-Signals.html"). So, my guess is that either you installed the glib-2.0.7 package wrong, it was corrupt, or that the package no longer contains that function. I would reinstall the normal glib package unless you need the other glib package...

```

sudo apt-get install libglib2.0-0

```

If you think the 2.0.7 package was corrupt...
```

sudo apt-get --purge --reinstall install whatever-the-package-name

```

---

### Post by Plaguester on 2008-01-17
> **rocketman768 said:**
> Alright, that log looks fine to me. Looks like that log was from when everything was working fine. You have a warning in there (WW), but no errors (EE). I suppose this means that the error is  not even letting X create new logs.

I also searched and found out that g_signal_accumulator_true_handled is a functioned defined by glib. Look here: [http://www.gtk.org/api/2.6/gobject/gobject-Signals.html]("http://www.gtk.org/api/2.6/gobject/gobject-Signals.html"). So, my guess is that either you installed the glib-2.0.7 package wrong, it was corrupt, or that the package no longer contains that function. I would reinstall the normal glib package unless you need the other glib package...

```

sudo apt-get install libglib2.0-0

```

If you think the 2.0.7 package was corrupt...
```

sudo apt-get --purge --reinstall install whatever-the-package-name

```

I tried the following and it has no effect on the problem:
```
sudo aptitude reinstall libglib2.0-0
```

---

### Post by Plaguester on 2008-01-17
Does Ubuntu have something resembling the repair install on Windows XP (installs system files over again to fix any corrupted ones but does not overwrite user data or installed programs)? If not, I'm not above dumping my data to an external drive and doing a fresh install to fix this if no one has any further ideas.

---

### Post by rocketman768 on 2008-01-17
Well, in my system, the g_signal_accumulator_true_handled is defined in /usr/lib/libgobject-2.0.so.0

To check to see if this is the case in your system,
```
objdump -d /usr/lib/libgobject-2.0.so.0 | grep g_signal_acc
```

You should see a line that says:
```
00017e00 <g_signal_accumulator_true_handled>:

```

...as well as some other lines that say "call..." and "jnz..." or "j..."

Also, this file IS provided by libglib2.0-0
```

/usr/lib$ dpkg -S libgobject-2.0.so.0
libglib2.0-0: /usr/lib/libgobject-2.0.so.0
libglib2.0-0: /usr/lib/libgobject-2.0.so.0.1400.1

```

I don't know what to tell you if you have this symbol defined in the same file as me except remove the new glib thing you installed, and purge and reinstall the libglib2.0-0.

---

### Post by rocketman768 on 2008-01-17
Oh, the way I figured out the symbol was in that file was to actually run objdump on every single file in /usr/lib. I did this with the following script if you need it for some reason. Just make a file called dumpit.sh in /usr/lib and put this inside it:

```

#!/bin/bash

for f in `ls`
do
   found=""
   found=$(objdump -d $f | grep g_signal_acc)
   if [ -n "$found" ]
   then
      echo "File: $f \nMessage: $found"
   fi
done


```

---

### Post by t.alex on 2008-01-21
Hi,
i had a simmilar issue after i tried to install 'glib-2.2.3' from the sources. make uninstall solved the problem for now:)
Greetings,
Alex

---

### Post by yongmuller on 2008-01-30
wow. I'm happy this thread was here.  i tried to upgrade glib to 2.0.1 and it screwed the pooch.  re-downloading the package and make uninstall did the trick.  Thanks!

---

