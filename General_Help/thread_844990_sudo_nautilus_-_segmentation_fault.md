---
title: "sudo nautilus - segmentation fault"
date: 2008-06-30
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-06-30
When I go into terminal and type in sudo nautilus I get this error: 
```
sudo nautilus
[sudo] password for jared: 
Initializing nautilus-image-converter extension
Initializing nautilus-share extension
seahorse nautilus module initialized
Initializing nautilus-open-terminal extension
Segmentation fault
```

Any suggestions?

---

### Post by ajmorris on 2008-06-30
hi there,
try```
 gksudo nautilus
```
if that still doesnt work, remove nautilus (sudo apt-get remove --purge nautilus) then re-install it (sudo apt-get install nautilus)

Also, if you are just trying to run the file manager, not draw the desktop, run nautilus like this:

```
nautilus --no-desktop
```

AJ

---

### Post by frogitts on 2008-07-14
I'm having the same problem now, both before and after uninstalling and reinstalling nautilus. For me it started happening after installing Samba. After uninstalling and reinstalling, I get the following:

```
seahorse nautilus module initialized
Initializing nautilus-open-terminal extension
Segmentation fault
```

---

### Post by mc4man on 2008-07-14
I know almost nothing about samba but maybe there's a connection between samba and what happens when you run gksudo nautilus. When you run that command the system will attempt to mount any unmounted removable media under root. If it finds something that can't be mounted then either nautilus just won't open or you get a segmentation fault.

Examples of what can't get mounted are blank cd/dvd's.
On the other hand if you have a usb flash drive inserted but not mounted, it will mount under root and nautilus will open.
maybe your samba share or whatever is treated like this

just posted some info on 
[http://ubuntuforums.org/showthread.php?p=5387560#post5387560](http://ubuntuforums.org/showthread.php?p=5387560#post5387560)

---

### Post by frogitts on 2008-07-20
Thanks for that - the problem for me was simply that I had a blank CD-RW in my tray. Talk about a bug!! This one will get written up shortly if it doesn't already exist.

---

### Post by yamaplos on 2008-08-01
same exact problem, I was in the middle of preparing to write a CD, which once it is done I will test again.

OK, sudo nautilus...
It gave me a warning: unable to add monitor, which I have no idea, but otherwise it is working.  Thanks!  and yes, someone ticket that, I noob dunno how that is done.

Yama

---

### Post by mc4man on 2008-08-01
> It gave me a warning: unable to add monitor i don't think that's anything to worry about.

---

### Post by ChrisC on 2008-08-02
> **yamaplos said:**
> someone ticket that, I noob dunno how that is done.

I had this problem today when trying to burn a DVD for the first time in 8.04/hardy.  Removing the blank DVD from the drive allowed me to get sudo nautilus going.  Unfortunately, that presented a Catch-22 since I was going to use the nautilus session to burn some data to the DVD.  Hmmm, OK, let's see how well this Brasero thing works ... good enough.

Here's another ubuntuforums thread on this problem, much longer:
[http://ubuntuforums.org/showthread.php?t=820564&page=7](http://ubuntuforums.org/showthread.php?t=820564&page=7)

Here's a launchpad thread I found on this.  Can someone with a launchpad account ping that thread just to let the Ubuntu folks know that this is still a problem and to see if you can drum up a response?
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/245931](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/245931)

FYI, I think the presence of the blank DVD was also killing sbackup.  I'm not sure about that, but someone might want to test that and check the appropriate logs.

---

### Post by pkkid on 2008-08-26
> **frogitts said:**
> Thanks for that - the problem for me was simply that I had a blank CD-RW in my tray. Talk about a bug!! This one will get written up shortly if it doesn't already exist.

Wow, thanks!! -- Count me in on hitting the blank DVDR issue. :)

---

### Post by koba101 on 2008-09-05
count me in...wow

---

### Post by dugald on 2008-09-18
No idea how you worked it out but thanks!

---

### Post by insanity54 on 2008-11-09
I can confirm this. trying the command, "sudo nautilus" while a blank DVD is in my DVD drive, causes the following output:

```

(nautilus:6347): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6347): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6347): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6347): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

```

If I can help fix this problem(bug?) by running any more tests, let me know. I'd be glad to help.

---

### Post by flclvr8780 on 2009-02-11
i removed the blank cd but it still says
```
matt@matt-desktop:~$ nautilus --no-desktop
Initializing nautilus-share extension
seahorse nautilus module initialized
Segmentation fault
```
what am i doing wrong. i even tried running it without the desktop because i cant right click on desktop and sudo permission has been denied

---

### Post by Yashiro on 2009-02-21
You can sometimes fix this by closing and restarting the bonobo activation process. 

The usual fix is to remove any cdroms from your drives and retry.

Or you could try *gksudo dbus-launch nautilus*.

---

### Post by offchance on 2009-03-01
> **frogitts said:**
> Thanks for that - the problem for me was simply that I had a blank CD-RW in my tray. Talk about a bug!! This one will get written up shortly if it doesn't already exist.

Same thing here. I removed the blank disc and "gksu nautilus" worked without giving me a seg fault message. Strange.

---

