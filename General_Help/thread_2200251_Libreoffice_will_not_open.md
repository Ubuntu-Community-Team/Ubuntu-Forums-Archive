---
title: "Libreoffice will not open"
date: 2014-01-18
forum: General Help
---

### Post by jweiner on 2014-01-18
I cannot open Libreoffice because I get the following error message in a pop-up window.

The application cannot be started. 
LibreOffice user installation could not be processed due to missing access rights. Please make sure that you have sufficient access rights for the following location and restart LibreOffice:


/home/john/.config/libreoffice/4

I tried uninstalling and then reinstalling, but this tactic does not work.  I get the same message. How do I "make sure that I have sufficient access rights for the following location..."?

Do I need to edit something in /home/john/.config/libreoffice/4?

The "4" directory is owned by root.

---

### Post by Bucky Ball on 2014-01-18
*Thread moved to [I]**General Help***.[/I]

What Ubuntu and Libreoffice releases are you using? How are you installing it?

---

### Post by claracc on 2014-01-18
Why is the directory /home/john/.config/libreoffice/4 owned by root?, have you messed with owner in your /home/john folder or have you installed libreoffice as root?

It is not advisable to run libreoffice as root, you take security risks.

I recommend you change the owner of your user folder /home/john to the (I suposse) john user, also you will have to change group user. Please, see [http://manpages.ubuntu.com/manpages/lucid/man1/chown.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/chown.1.html) in order to know howto from the command line.

---

### Post by ajgreeny on 2014-01-18
The big question to ask, however, is how much more of your /home is wrongly owned, or has incorrect permissions.  Can we see the output of command ```
ls -la | grep root
```

---

### Post by jweiner on 2014-01-18
Reply to Buckyball:  The ubuntu version is 13.10 (64) and the Libreoffice is whatever comes with that.  It came preinstalled and I just clicked on its icon in the Ubiquity GUI (left-hand side).  After posting this query I thought that maybe I should just remove everything in Libreoffice and try again.
So I did sudo apt-get remove --purge libreoffice*.  This ripped everything out, and I then reinstalled from the dash.  Unfortunately I get the same message.

In answer to claracc, no I did not install anything as root (uh-oh...is "sudo apt-get install..." tantamount to installing as root?)...I was logged in as john when invoked sudo...

In answer to ajgreeny, from /home/john the ls -la | grep root produces to directories owned by root: .. and .gvfs.  I don't know what either of them does.

---

### Post by jweiner on 2014-01-18
Actually if I just do ls -la from /home/john, the entry for .gvfs has a lot of question marks and it's ownership cannot be changed (function not implemented).  I changed all root-owning directories to john-owning directories from /home/john/.config/libreoffice/4.  The problem still persists.

---

### Post by jweiner on 2014-01-18
After "sudo apt-get remove --purge libreoffice*" takes out the software, I notice now that /home/john/.config still has a libreoffice subdirectory.  If I go down further I find
~/.config/libreoffice/4/user/config and in this config directory there are lots of files belonging to root:

drwxr-xr-x 11 john john   4096 janv. 18 16:21 ..
-rw-r--r--  1 root root   4308 oct.  22 19:49 arrowhd.soe
-rw-r--r--  1 root root  48408 oct.  22 19:49 autotbl.fmt
-rw-r--r--  1 root root  30852 oct.  22 19:49 classic.sog
-rw-r--r--  1 root root  13132 oct.  22 19:49 cmyk.soc
-rw-r--r--  1 root root   4408 oct.  22 19:49 gallery.soc
-rw-r--r--  1 root root   5238 oct.  22 19:49 hatching.soh
-rw-r--r--  1 root root  10766 oct.  22 19:49 html.soc
-rw-r--r--  1 root root    428 janv. 17 13:36 javasettings_Linux_X86_64.xml
-rw-r--r--  1 root root   2334 oct.  22 19:49 libreoffice.soc
-rw-r--r--  1 root root   6840 oct.  22 19:49 modern.sog
-rw-r--r--  1 root root   5271 oct.  22 19:49 palette.soc
-rw-r--r--  1 root root  31320 oct.  22 19:49 scribus.soc
drwxr-xr-x  3 root root   4096 janv. 17 13:37 soffice.cfg
-rw-r--r--  1 root root 155895 oct.  22 19:49 standard.sob
-rw-r--r--  1 root root  11162 nov.  21 23:31 standard.soc
-rw-r--r--  1 root root   2426 oct.  22 19:49 standard.sod
-rw-r--r--  1 root root   4972 oct.  22 19:49 standard.soe
-rw-r--r--  1 root root   8838 oct.  22 19:49 standard.sog
-rw-r--r--  1 root root   2171 oct.  22 19:49 standard.soh
-rw-r--r--  1 root root   1708 oct.  22 19:49 styles.sod
-rw-r--r--  1 root root   2331 oct.  22 19:49 tango.soc
-rw-r--r--  1 root root  14420 oct.  22 19:49 web.soc
[email]john@samba:~/.config[/email]/libreoffice/4/user/config$ 

These files have prefixes like .soc, .soh, .soe, etc.  They don't look like files I should be concerned with.  Are these root files the problem?

---

### Post by ajgreeny on 2014-01-18
> **jweiner said:**
> After "sudo apt-get remove --purge libreoffice*" takes out the software, I notice now that /home/john/.config still has a libreoffice subdirectory.  If I go down further I find
~/.config/libreoffice/4/user/config and in this config directory there are lots of files belonging to root:

drwxr-xr-x 11 john john   4096 janv. 18 16:21 ..
-rw-r--r--  1 root root   4308 oct.  22 19:49 arrowhd.soe
-rw-r--r--  1 root root  48408 oct.  22 19:49 autotbl.fmt
-rw-r--r--  1 root root  30852 oct.  22 19:49 classic.sog
-rw-r--r--  1 root root  13132 oct.  22 19:49 cmyk.soc
-rw-r--r--  1 root root   4408 oct.  22 19:49 gallery.soc
-rw-r--r--  1 root root   5238 oct.  22 19:49 hatching.soh
-rw-r--r--  1 root root  10766 oct.  22 19:49 html.soc
-rw-r--r--  1 root root    428 janv. 17 13:36 javasettings_Linux_X86_64.xml
-rw-r--r--  1 root root   2334 oct.  22 19:49 libreoffice.soc
-rw-r--r--  1 root root   6840 oct.  22 19:49 modern.sog
-rw-r--r--  1 root root   5271 oct.  22 19:49 palette.soc
-rw-r--r--  1 root root  31320 oct.  22 19:49 scribus.soc
drwxr-xr-x  3 root root   4096 janv. 17 13:37 soffice.cfg
-rw-r--r--  1 root root 155895 oct.  22 19:49 standard.sob
-rw-r--r--  1 root root  11162 nov.  21 23:31 standard.soc
-rw-r--r--  1 root root   2426 oct.  22 19:49 standard.sod
-rw-r--r--  1 root root   4972 oct.  22 19:49 standard.soe
-rw-r--r--  1 root root   8838 oct.  22 19:49 standard.sog
-rw-r--r--  1 root root   2171 oct.  22 19:49 standard.soh
-rw-r--r--  1 root root   1708 oct.  22 19:49 styles.sod
-rw-r--r--  1 root root   2331 oct.  22 19:49 tango.soc
-rw-r--r--  1 root root  14420 oct.  22 19:49 web.soc
[EMAIL="john@samba:~/.config"]john@samba:~/.config[/EMAIL]/libreoffice/4/user/config$ 

These files have prefixes like .soc, .soh, .soe, etc.  They don't look like files I should be concerned with.  Are these root files the problem?
Yes, that is exactly your problem, though it is impossible to know at this stage why those files are owned by root, and not by you as user.

Run command ```
sudo chown -R john:john .config
```assuming your username is john. Should you also have problems with other applications it could be for the same reason and it may be worth running the command on all of your home with ```
sudo chown -R john:john /home/john
```Reinstall LO now and all should be well.

PS:
.**gvfs** should be owned by you and have permissions like this
```
dr-x------  2 john john     0 Jan 18 10:42 ./
```
If this really is owned by root on your system, I think you really do need to run the command above on all your home.

---

### Post by whitesmith on 2014-01-18
The advice given by claracc is sound and should be followed. I would add only one point:> **claracc said:**
> It is not advisable to run libreoffice as root, you take security risks. Fact is, it is  inadvisable to install **anything** as root because doing so can open your computer to mischief. For example, let's say you install some Windows software as root using Wine. If that SW contains a malware payload, you have given it unfettered access to your entire machine, exactly as it would have in Windows. This is not what you want, is it?

---

### Post by jweiner on 2014-01-18
Thank you ajgreeny.  Putting everything in john ownership did the trick (at least for libreoffice writer--so I suppose it will work for the other libreoffice programs as well).
I have no idea how or why those files got installed with root ownership.  I did nothing unconventional installing ubuntu 13.10...just installed it from a live CD burned from a downloaded iso-file.

---

