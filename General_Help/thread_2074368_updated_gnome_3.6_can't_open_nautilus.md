---
title: "updated gnome 3.6 can't open nautilus"
date: 2012-10-21
forum: General Help
---

### Post by Driftu on 2012-10-21
Hello, need help.
I installed Ubuntu 12.10 and then installed gnome-shell 3.4.2. Then found on the internet, that i can update my gnome-shell 3.4.2 to 3.6 and add repository to software sources.

sudo add-apt-repository ppa:gnome3-team/gnome3

After that upgraded my ubuntu, did restart and can't open nautilus
in terminal got this error:


(nautilus:2187): Gdk-CRITICAL **: gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

---

### Post by Frogs Hair on 2012-10-21
The default Gnome Shell from the repository is 3.6.1 for 12.10 so the PPA wasn't really needed . Ubuntu is using an older version of Nautilus in 12.10 because of the changes in the 3.6 version. I would first find out what version of Nautilus you have installed from synaptic if installed . The Gnome PPA that I know of is for testing so there  is a risk it won't work properly.

---

### Post by mpmistr on 2012-10-21
> **Driftu said:**
> Hello, need help.
I installed Ubuntu 12.10 and then installed gnome-shell 3.4.2. Then found on the internet, that i can update my gnome-shell 3.4.2 to 3.6 and add repository to software sources.

sudo add-apt-repository ppa:gnome3-team/gnome3

After that upgraded my ubuntu, did restart and can't open nautilus
in terminal got this error:


(nautilus:2187): Gdk-CRITICAL **: gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

(nautilus:2723): Gdk-CRITICAL **: gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

I am getting the same error after apt-get prompted me to upgrade Nautilus from the Gnome 3 Team PPA. I have been running Nautilus 3.6.1 on Ubuntu 12.10 Gnome Shell Remix so this issue has something to do with the recent build of Nautilus released a few hours ago apparently.

---

### Post by Driftu on 2012-10-21
> **Frogs Hair said:**
> The default Gnome Shell from the repository is 3.6.1 for 12.10 so the PPA wasn't really needed . Ubuntu is using an older version of Nautilus in 12.10 because of the changes in the 3.6 version. I would first find out what version of Nautilus you have installed from synaptic if installed . The Gnome PPA that I know of is for testing so there  is a risk it won't work properly.

I did sudo ppa-purge ppa:gnome3-team/gnome3

then downgraded all files from ubuntu repositories, and got nautilus 3.4.2 with old interface. :(

---

### Post by Frogs Hair on 2012-10-21
I installed from the software center and the shell version is displayed as follows. :confused:
Do you have 12.04 or 12.10 ```
lsb_release -a
```

---

### Post by Driftu on 2012-10-21
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
n0name@n0name:~$ 


gnome-shell 3.6.1, but nautilus 1:3.5.90.really.3.4.2-0ubuntu4 in synaptic.

---

### Post by mpmistr on 2012-10-21
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

GNOME nautilus 3.6.1

(nautilus:7258): Gdk-CRITICAL **: gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

---

### Post by Frogs Hair on 2012-10-21
That would be correct because of using the older nautilus version. 

Try the following restart command and post the output if any. ```
nautilus -q
```

---

### Post by Driftu on 2012-10-21
Nothing the same.


I wanna this nautilus result in right side of picture.

[IMG]http://worldofgnome.org/uploads/2012/10/nemo-nautilus-700x375.png[/IMG]

---

### Post by mpmistr on 2012-10-21
I was able to get Nautilus to open again but I had to install a previous version of Nautilus from the Gnome 3 PPA.. in a terminal it shows Nautilus 3.4.2 but when I launch Nautilus and check version it shows 3.6.1.. so I am confused lol..

---

### Post by Andy1988 on 2012-10-21
Exactly the same here. I did the update of today via the PPA and now it segfaults for me.

So, don't update to the newest version of nautilus if you use the gnome3-team PPA!

---

### Post by mc4man on 2012-10-21
Are you guys using GS or unity?
The ppa nautilus will break on opening from the unity launcher & from a terminal, should still work from a Desktop folder.
Haven't tried on GS

I did warn them a few weeks ago that a commit to the nautilus trunk would do this, guess they paid me no mind...

The commit that cause (vcs imports
[http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16646](http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16646)

I've been reverting this commit with no ill effects though there may be a fix that could keep it

```
--- nautilus-3.6.1.orig/src/nautilus-application.c
+++ nautilus-3.6.1/src/nautilus-application.c
@@ -1152,7 +1152,7 @@ nautilus_application_local_command_line
 
 	context = g_option_context_new (_("\n\nBrowse the file system with the file manager"));
 	g_option_context_add_main_entries (context, options, NULL);
-	g_option_context_add_group (context, gtk_get_option_group (FALSE));
+	g_option_context_add_group (context, gtk_get_option_group (TRUE));
 
 	argv = *arguments;
 	argc = g_strv_length (argv);
```

screen shows working fine from terminal, also works fine from launcher (I've made some add. changes to improve nautilus for my taste

---

### Post by mpmistr on 2012-10-21
I emailed the person who updated the latest Nautilus package about the segfault issue. Hopefully they'll resolve this soon!

---

### Post by mpmistr on 2012-10-21
I am using Gnome Shell Remix Ubuntu 12.10; everything was working perfectly fine until the Nautilus update today.

---

### Post by Frogs Hair on 2012-10-21
Here is my 12.10 default version.

---

### Post by ariel on 2012-10-21
Same issue - ubuntu 12.10 / gnome3 ppa & nautilus 3.6.1

nautilus was working just fine up until today's upgrade in the gnome-ppa. 


(nautilus:3092): Gdk-CRITICAL **: gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

Can't wait for a properly supported & managed ubuntu-based distro with reasonable pure gnome. It is sad that ubuntu made the gnome experience so miserable for all of us. Broken file manager... it's been years since I saw this last.

---

### Post by Andy1988 on 2012-10-22
> **mc4man said:**
> Are you guys using GS or unity?
The ppa nautilus will break on opening from the unity launcher & from a terminal, should still work from a Desktop folder.
Haven't tried on GS

I'm using Gnome Shell.
And opening Nautilus with a Desktop folder in fact works. That's at least a workaround until it's fixed upstream.

---

### Post by mc4man on 2012-10-22
There should be a new naut package coming shortly, likely will revert the commit I mentioned previously.
Never really saw what that commit was fixing, ("This fixes the busy spinning cursor being stuck when opening multiple Nautilus windows"),  so if the new build does in fact revert it & any issue is seen then please post..

(I don't get a spinning cursor here, possibly because using nautilus to handle the Desktop?

---

### Post by mpmistr on 2012-10-22
> **mc4man said:**
> There should be a new naut package coming shortly, likely will revert the commit I mentioned previously.
Never really saw what that commit was fixing, ("This fixes the busy spinning cursor being stuck when opening multiple Nautilus windows"),  so if the new build does in fact revert it & any issue is seen then please post..

(I don't get a spinning cursor here, possibly because using nautilus to handle the Desktop?

From what I noticed with the spinning cursor issue the reason it was doing that was because Nautilus was being launched with a toggle (I think it was %u or something similar).

When opening Nautilus from the terminal it did not get the spinning cursor.

---

### Post by mc4man on 2012-10-22
There is a new build avail.  - 
The current chosen fix is to keep the commit prev. mentioned but remove an Ubuntu timestamp patch that was there to assure opened nautilus windows had focus
(most common scenario was to open a terminal, then open nautilus - nautilus would open without focus.

GS will be fine as far as the focus issue, those using the ppa naut in Unity will likely see the prev. focus problem return.

(myself never had any issue with cursor spin on, either in general or "when opening multiple nautilus windows", so here where I use unity will either continue to revert that commit or patch gtk
(probably the latter

---

### Post by ariel on 2012-10-23
the nautilus 3.6 update from yesterday works just fine.

Only thing I noticed is that the "backspace" key no longer works to go back in the navigation history (like alt-"left arrow") does.

wondering if the backspace key removal a "feature" or a bug?  Other than this, nautilus 3.6 looks and feels really neat

---

