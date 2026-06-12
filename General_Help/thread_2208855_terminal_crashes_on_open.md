---
title: "terminal crashes on open"
date: 2014-03-02
forum: General Help
---

### Post by jj4 on 2014-03-02
When I press ctl alt t, the terminal opens but then immediately closes.
I tried reinstalling it through synaptic and it doesn't make a difference.
Any ideas how I can fix this?

---

### Post by oldos2er on 2014-03-02
Can you open xterm? Alt-F2, type in *xterm*

---

### Post by jj4 on 2014-03-02
> **oldos2er said:**
> Can you open xterm? Alt-F2, type in *xterm*

it does the same thing, it opens and crashes immediately

---

### Post by steeldriver on 2014-03-02
How about Alt-F2 and then

```
gnome-terminal -x /bin/bash --norc
```

---

### Post by jj4 on 2014-03-03
that works. so what do I need to reinstall?

---

### Post by steeldriver on 2014-03-03
It suggests there's something nasty in one of the bash startup files, most likely your local ~/.bashrc - either open it up in a text editor and try to fix, it or copy a 'clean' default one from the /etc/skel directory

```

mv ~/.bashrc ~/bashrc.old

cp /etc/skel/.bashrc ~/

```

---

### Post by jj4 on 2014-03-03
crashes as soon as I try to run this command:
mv ~/.bashrc ~/bashrc.old
the cp command crashes it as well
I tried opening up the file with nano and it seems empty

---

### Post by Lars Noodén on 2014-03-03
Can you log in to a console at all?  ctrl-alt-f1 will bring you to one.  Ctrl-alt-f7 will bring you back to the graphical environment afterward.

---

### Post by jj4 on 2014-03-03
> **Lars Noodén said:**
> Can you log in to a console at all?  ctrl-alt-f1 will bring you to one.  Ctrl-alt-f7 will bring you back to the graphical environment afterward.



I can get to the console but it asks me for a login. I then login but it returns me to the login prompt almost immediately.
When I press ctrl Alt f7 I get the following error;
segmentation fault (core dumped)

---

### Post by steeldriver on 2014-03-03
Can you execute the mv and cp commands directly from the Alt-F2 command box?

---

### Post by jj4 on 2014-03-03
> **steeldriver said:**
> Can you execute the mv and cp commands directly from the Alt-F2 command box?

they seem to execute but not sure whether they are running or crashing, the alt f2 screen just closes.

---

### Post by tgalati4 on 2014-03-03
Boot into a Rescue Shell and examine the following:

```
sudo smartctl -a /dev/sda
```  

Sounds like your disk drive is not allowing write operations, so anything that causes a write crashes.

If you can't boot into a rescue shell from GRUB, then boot a LiveUSB or DVD and run the *smartctl* command, because it seems that your disk is ready to check out.

---

### Post by jj4 on 2014-03-04
> **tgalati4 said:**
> Boot into a Rescue Shell and examine the following:

```
sudo smartctl -a /dev/sda
```  

Sounds like your disk drive is not allowing write operations, so anything that causes a write crashes.

If you can't boot into a rescue shell from GRUB, then boot a LiveUSB or DVD and run the *smartctl* command, because it seems that your disk is ready to check out.


But I can store files on the desktop and pictures etc so it must be writing something?
I had a problem recently removing teamviewer so I think it may have removed some libraries - shouldn;t have removed any with dependencies obviously but...

---

### Post by tgalati4 on 2014-03-04
Compare the dependencies between teamweaver and nautilus:

```
apt-cache depends nautilus
```

How did you install teamweaver?

Reload any packages shared between the two.

Do you have errors in your package manager?

```
sudo apt-get check
```

---

### Post by jj4 on 2014-03-05
> **tgalati4 said:**
> Compare the dependencies between teamweaver and nautilus:

```
apt-cache depends nautilus
```

How did you install teamweaver?

Reload any packages shared between the two.

Do you have errors in your package manager?

```
sudo apt-get check
```


one problem..I cannot enter a command into any terminal without it crashing! :)

update manager has:
Global symbol "$Prevcongmg" requires explicit package name at /usr/share/perl/5.14/Getopt/Long.pm line 1374.
Missing right curly or square bracket at /usr/share/perl/5.14/Getopt/Long.pm line 1379, at end of line
syntax error at /usr/share/perl/5.14/Getopt/Long.pm line 1379, at EOF
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 173.
dpkg: warning: files list file for package 'libapt-pkg4.12:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgconf-2-4:i386' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libgconf2-4:i386' is missing final newline
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:



Global symbol "$Prevcongmg" requires explicit package name at /usr/share/perl/5.14/Getopt/Long.pm line 1374.
Missing right curly or square bracket at /usr/share/perl/5.14/Getopt/Long.pm line 1379, at end of line
syntax error at /usr/share/perl/5.14/Getopt/Long.pm line 1379, at EOF
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 173.
dpkg: warning: files list file for package 'libapt-pkg4.12:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgconf-2-4:i386' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libgconf2-4:i386' is missing final newline
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

---

### Post by Lars Noodén on 2014-03-05
Do you have Synaptic?  It has the ability to re-install packages.  Which version and flavor are you running?  There should be a meta-package to call which will re-install most things.  

However, what about the Live DVD and testing *smartctl* ?

---

