---
title: "alternate for /usr/local"
date: 2018-09-10
forum: General Help
---

### Post by Skaperen on 2018-09-10
in the past i have been putting my stuff or our stuff (in cases where i work as sysadmin somewhere) in [FONT=courier new]/usr/local[/FONT], typically commands in [FONT=courier new]/usr/local/bin[/FONT] and libraries in [FONT=courier new]/usr/local/lib[/FONT] (configured under [FONT=courier new]/etc/ld.so.conf.d[/FONT]).  lately, i have been encountering difficulties managing this because many packages (not from Ubuntu repositories) put files under [FONT=courier new]/usr/local[/FONT].  apparently FSB makes this OK so some programmers do it.  apparently the semantics are what the local admin chooses to install, regardless of who developed it or how it is managed.  and my/our stuff is managed in a different way than building [FONT=courier new]deb[/FONT], [FONT=courier new]pip[/FONT], or [FONT=courier new]rpm[/FONT] packages.

so what i want to do is create a whole new tree under [FONT=courier new]/usr[/FONT] to hold locally developed stuff (that i manage builds for, and so on).  most of it is in [FONT=courier new]bash[/FONT] or [FONT=courier new]C[/FONT] or [FONT=courier new]Python[/FONT].  a few other languages are there.

i am trying to come up with a name for this since "[FONT=courier new]local[/FONT]" is already used.  the name bouncing around in my head right now is "[FONT=courier new]site[/FONT]".  so that would mean commands would be in [FONT=courier new]/usr/site/bin[/FONT].

does anyone have any suggestions?

---

### Post by TheFu on 2018-09-11
/opt/ is for commercial software. Why not use that?

---

### Post by Skaperen on 2018-09-12
> **TheFu said:**
> /opt/ is for commercial software. Why not use that?

this is not software being marketed commercially.  and i need it to be a distinct directory, not shared with other software.

---

### Post by Holger_Gehrke on 2018-09-13
'/opt/' is not exclusively for commercial software. On a Solaris system I had access to some years ago the Gnu tools where found in '/opt/gnu/', probably to avoid name collisions. Putting packages in /opt in their own sub directory is standard operating procedure. It keeps the programs separate and distinct from the rest of the system, which makes manual management easier.

Another option would be to create .deb packages of your programs so installation and removal can be handled through apt or dpkg. Then it's completely irrelevant where they install, the package manager remembers it for you and sets the package up by executing various scripts during installation or removal.

Holger

---

### Post by HermanAB on 2018-09-13
Hmm, ever since I started to save my schtuff under /fubar, I never had others clobbering it anymore.

---

### Post by TheFu on 2018-09-13
Nothing says you have to place anything in /usr/local/bin ... /lib ... /share ... do like JDK does.
If your program is called Joeth, 
```
/usr/local/Joeth
+-- bin
+-- doc
+-- etc
+-- lib
```
Then modify your LD_LIBRARY_PATH and PATH as needed.
Or use /opt/  ... or put it into a userids HOME.
This was how we did things before package managers.  Every program had their own TOP_DIR and was self-contained.

Not that it will help, but there is the Linux File System Hierarchy Standards - google finds it easily. With wikipedia summary is almost always sufficient. IMHO.

---

### Post by Skaperen on 2018-09-13
i have read _[FONT=arial black]FHS[/FONT]_.  that's where i realized that other stuff in _[FONT=courier new]/usr/local[/FONT]_ was to be expected.  the software i'm putting is not one single specific program; it is a mix of stuff that needs some generic name.  that's why i originally used _[FONT=courier new]local[/FONT]_ and why my recent thought of _[FONT=courier new]site[/FONT]_.  so now the consideration is whether to use a subdirectory under _[FONT=courier new]/opt[/FONT]_ or just stay in _[FONT=courier new]/usr[/FONT]_ where _[FONT=courier new]/usr/local[/FONT]_ is. so _[FONT=courier new]/usr/site[/FONT]_ or _[FONT=courier new]/opt/site[/FONT]_ is the current thought.

---

### Post by TheFu on 2018-09-14
A friend is using slackware and has selected epkg as the package manager he prefers.  It uses symlinks for the different versions of installed packages.  Switching between versions just changes the non-versioned link to a different versioned directory.

I have seen "site" used.  Also seen where different teams would get versioned, dynamically mounted, locations.  These environments had thousands of workstations and about 40 different teams using different mounts based on their roles.  At login, the mounts would be determined.

Just trying to provide options.

---

### Post by Skaperen on 2018-09-15
interesting.  did you happen to see how "site" was used and/or what they put in it?

i want to keep things separate; that was the motivation to come up with a name.  i would now avoid even [FONT=courier new]/opt/local[/FONT] as that might get confused with [FONT=courier new]/usr/local[/FONT].  so i guess [FONT=courier new]/usr/site[/FONT] or [FONT=courier new]/opt/site[/FONT] might be what i use.  i might ene use both.

---

### Post by TheFu on 2018-09-15
/usr/local/{group}/{program}
/usr/site/{group}/{program}

Groups were either based on the role/group or the programming team.

---

