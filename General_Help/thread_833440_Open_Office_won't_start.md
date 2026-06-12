---
title: "Open Office won't start"
date: 2008-06-18
forum: General Help
---

### Post by alecspoons on 2008-06-18
Help!

Nothing in Open Office will start since today's Ubuntu update.
The Open Office logo shows and it looks like it's going to start, but then shuts down again!?

I'm using the AMD64 flavour of Ubuntu.

Anybody...?

Thanks

---

### Post by TeoBigusGeekus on 2008-06-18
Open a terminal and type
```
openoffice
```
Post us any error messages.

---

### Post by alecspoons on 2008-06-18
Thanks

I got this:

helenandalec@helenandalec-desktop:~$ openoffice
javaldx: Could not find a Java Runtime Environment! 
helenandalec@helenandalec-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fc933b1e97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7fc933b1ea15]
#2 /usr/lib/libX11.so.6 [0x7fc9377e8323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7fc9377dfd54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7fc9336c8c05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7fc92ed574c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7fc932b5cbcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7fc932b70386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7fc932b720d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7fc932b72483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7fc92ed48957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fc92f10076d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fc92f10116a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fc92f10182b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fc92f0d9f64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7fc93b0854ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7fc93b01a322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7fc93b0571cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7fc927d89084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7fc927f5ddb4]
helenandalec@helenandalec-desktop:~$

---

### Post by TeoBigusGeekus on 2008-06-18
> **alecspoons said:**
> 
javaldx: Could not find a Java Runtime Environment! 


I get this as well, but openoffice starts...
Unless someone else has something better to suggest, I think a complete uninstallation of openoffice
```
sudo apt-get --purge remove openoffice
```
and then a reinstallation
```
sudo apt-get install openoffice
```
could do the trick.

---

### Post by alecspoons on 2008-06-18
OK...I just tried that and got this:

helenandalec@helenandalec-desktop:~$ sudo apt-get --purge remove openoffice
[sudo] password for helenandalec: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice
helenandalec@helenandalec-desktop:~$ sudo apt-get install openoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice
helenandalec@helenandalec-desktop:~$ 

Thant's not right, is it....

---

### Post by TeoBigusGeekus on 2008-06-18
Try openoffice.org instead of plain openoffice in the 2 commands.

---

### Post by alecspoons on 2008-06-18
The commands worked and Open Office re-installed - but it still won't run!

---

### Post by TeoBigusGeekus on 2008-06-18
Do you get the same messages in terminal?

---

### Post by alecspoons on 2008-06-18
Looks like it:

helenandalec@helenandalec-desktop:~$ openoffice
helenandalec@helenandalec-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f98fdf2397c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f98fdf23a15]
#2 /usr/lib/libX11.so.6 [0x7f9901bed323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f9901be4d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f98fdacdc05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f98f915c4c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f98fcf61bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f98fcf75386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f98fcf770d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f98fcf77483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f98f914d957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f98f950576d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f98f950616a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f98f950682b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f98f94def64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f990548a4ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f990541f322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f990545c1cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f98f2189084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f98f235ddb4]
helenandalec@helenandalec-desktop:~$

---

### Post by TeoBigusGeekus on 2008-06-18
Ok, plan B.
Delete the folder .openoffice.org2 from your /home folder and reboot.

---

### Post by alecspoons on 2008-06-18
Just tried a Google search for 

"Locking assertion failure" open office

and found this:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676")

Could be a known problem...

---

### Post by alecspoons on 2008-06-18
I've tried removing .openoffice.org2 as you suggested, but same results.

---

### Post by dawithers on 2008-06-18
I had this same problem. I found that the problem lies in the openoffice.org-gtk package. If you remove this it will require the removal of openoffice.org-gnome as well, but it will allow openoffice to start. It just won't match your gnome theme. I'm not sure what is wrong with the openoffice.org-gtk package, but it clearly is the root of the problem. This is also mentioned on that bug report you mentioned.

The javaldx: Could not find a Java Runtime Environment! error that was showing up will go away if you mark the openoffice.org package for install.

---

### Post by TeoBigusGeekus on 2008-06-19
> **alecspoons said:**
> Just tried a Google search for 

"Locking assertion failure" open office

and found this:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676")

Could be a known problem...

Excellent job!!!
```
sudo apt-get remove openoffice.org-gtk
sudo apt-get remove openoffice.org-gnome
```

According to the bug report, openoffice will look ugly but it will be functional.
Do your job and stay put for updates as it is a crucial bug (Standard Ubuntu office application non-operational?) and it is bound to be fixed soon.

---

### Post by phildaman46 on 2008-06-19
I also have this problem. It seems if you have the Openoffice.org Quickstarter loaded, Openoffice.org will load from the menu.

---

### Post by herorev on 2008-06-19
I'm also experiencing this problem on Kubuntu 8.04 64-bit. I was able to get things working by removing the openoffice.org-kde and openoffice.org-gtk packages.

Aren't the LTS releases supposed to be more stable than this?

---

### Post by spacepirates on 2008-06-19
I have the same problem on Ubuntu 64 bit. Openoffice won't start if I try to launch it from the app menu or from the terminal, but if I open an existing document (.doc format), openoffice starts right up (even asks if i want to recover the untitled doc from before).

From here I can open up a new document and continue working. I'm assuming the latest update is what did this, but I can't say for sure as I don't use Openoffice all that often.

Error code:
```
spacepirates@orangeiguanas:~$ openoffice Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fd718b7497c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7fd718b74a15]
#2 /usr/lib/libX11.so.6 [0x7fd71c83e323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7fd71c835d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7fd71871ec05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7fd713dad4c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7fd717bb2bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7fd717bc6386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7fd717bc80d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7fd717bc8483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7fd713d9e957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fd71415676d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fd71415716a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fd71415782b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fd71412ff64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7fd7200db4ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7fd720070322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7fd7200ad1cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7fd70d372084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7fd70d546db4]

```

---

### Post by alecspoons on 2008-06-19
Weird.

I'm getting the same result as spacepirates: I can now open a document from a file or folder (.odt), but OO still won't open from the menu.

That definitely didn't work this time yesterday.

---

### Post by dawithers on 2008-06-23
When you open a file by double-clicking it is essentially running the command:
```
$ ooffice file.odt
```
which consequently works from the command line. It seems strange that that would work but nothing else. But it does.

---

### Post by TRAyres on 2008-06-23
I tried opening from a file, and it doesn't seem to work in my case.

Going to try the making it ugly route.

*Edit
See, I take umbrage with calling it ugly. I prefer retro, and trying to see it as positively as possible, will consider it a refreshing throwback. 
*Note
It now opens, but as said, it looks a bit 'retro'.

---

### Post by davidpeace on 2008-06-25
Same problem. Did the removal of gtk and gnome components and it now works. Wish I was a programmer so I could look at the error messages... and do this myself, but I am grateful for the forums. Where can I start with the programming?

---

### Post by jamesstansell on 2008-06-25
> **davidpeace said:**
> Where can I start with the programming?

There are lots of ways, and here's a suggestion.  It's a book I'm reading right now.

Programming from the ground up : [an introduction to programming using Linux assembly language] / Jonathan Bartlett

Even if assembly language sounds scary you should still consider this book.  It goes to great lengths to explain things in simple terms.  And you'll be a better programmer for having an understanding at this level.  This book also includes an introduction to C and higher-level languages.

---

### Post by davidpeace on 2008-06-26
Thanks. I have placed an order.

---

### Post by alecspoons on 2008-06-27
> **alecspoons said:**
> I can now open a document from a file or folder (.odt), but OO still won't open from the menu.

Not any more, I can't. 
It's stopped doing it now.
Seems to come and go...

P.S. This is the only time in the six months I've used Ubuntu that I've had any problems. Trouble is, it's a pretty serious one. I've come to rely on OO for work. Hope it's sorted soon.

---

### Post by alecspoons on 2008-06-28
> **TeoBigusGeekus said:**
> 
```
sudo apt-get remove openoffice.org-gtk
sudo apt-get remove openoffice.org-gnome
```


This worked for me - and it's not that ugly, really.

---

### Post by alecspoons on 2008-07-02
Hooray for Ubuntu!

Open Office all better now.
Today's update has fixed this.

Just reinstalled openoffice.org-gtk through Synaptic Package Manager, and it works and looks just great!

---

### Post by ultrageeky on 2008-12-09
Open Office 3 on KDE has the same problem for me.  I tried completely removing anything related to OO then re-installed it post a reboot.  The only option that worked was to uninstall openoffice.org-kde.

As someone said above, it looks like crap without full desktop integration but at least it works.  For an idea of how it looks, think of Windows 3.1.  Definitely a step backwards.  I look forward to being able to re-install openoffice.org-kde but until it works properly...

Thank you for the advice.

---

### Post by apswartz on 2008-12-09
Yes, same problem here with Kubuntu. I to uninstall openoffice.org-kde to get it working again. 

Thanks for the fix, I really didn't want to completely remove and reinstall it all.

---

### Post by dragos_iliescu_2005 on 2008-12-09
It seem that Java is not installed on the machine. Check in (Synaptic) Package Manager and install Java runtime environment.

---

### Post by Arup on 2008-12-09
OO3 is back again in the repos and all the previous problems with gnome desktop update is all fixed now. Good work team Ubuntu, OO3 works fine here, as for Java, I have both Sun and Open JDK installed, I prefer using Sun for OO3. Previously I had to install open office java common to get it to recognize with the installed JRE, otherwise OO doesn't see installed JRE.

---

### Post by linux_tech on 2008-12-09
open office issues can also be submitted here-  [http://qa.openoffice.org/issue_handling/project_issues.html](http://qa.openoffice.org/issue_handling/project_issues.html)

---

### Post by apswartz on 2008-12-11
Still having problems with KDE integration.
Package: openoffice.org-kde

OpenOffice crashes when this package is installed. Works when it is removed.

---

### Post by apswartz on 2008-12-11
Filed a new bug report...
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/307207](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/307207)

---

