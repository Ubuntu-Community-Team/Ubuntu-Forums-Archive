---
title: "xsession errors gtk"
date: 2007-10-27
forum: General Help
---

### Post by evilc on 2007-10-27
"Refusing to initialize GTK+." This error has been in since (and before) Gutsy was released 9 days now. There have been almost 100 updates but still nothing to fix this!  Can someone with the knowledge help solve the problem.

I have had to reload 6 times in the last 9 days, and please don't say it's still early days for Gutsy after all it has been officially released so it should not be "beta".

Sorry for the gripe, but all the bull about it shows it should not been released when it was. New users are going to think Ubuntu installs easy, but is a load of rubbish especially as it's only an update of Feisty, the only difference should be updated programs.

---

### Post by johnnyg on 2007-10-27
Could you provide a bit more information?

I'm assuming that the message you are quoiting is coming from .xession-errors?

At what point do you get this message?

Re: upgrades ought to be simpler than fresh installs.   This actually tends not to be the case.   With a fresh install the installer is working with a clean state, so the machine is in a known state at the start of the install.  

Each upgrade is likely to encounter a slightly different setup (eg different users will have installed different packages during the lifetime of the previous version).   It is, unfortunately, pretty difficult to test everything that upgrades might encounter.  

I've had a few problems myself since doing a feisty to gutsy upgrade.   Most of my problems are side-effects of stuff I've tinkered with in Feisty.

John

---

### Post by evilc on 2007-10-27
> **johnnyg said:**
> Could you provide a bit more information?

I'm assuming that the message you are quoiting is coming from .xession-errors?

At what point do you get this message?

Re: upgrades ought to be simpler than fresh installs.   This actually tends not to be the case.   With a fresh install the installer is working with a clean state, so the machine is in a known state at the start of the install. ....  

John

I get it when my machine has loaded up  *eg. *opening nautilus with nothing other than the system installed. This particular error/problem has been in Gutsy since about half way through it dev, but still nothing done. 

There are numerous posts regarding this problem and the infill answer anyone has come up with is delete the file (every time) as it grows and could be quite large eventually. 
I have used Ubuntu full time since Dapper and every version has been loaded as clean installation. The last time I saw problems this bad was in Warty.

---

### Post by johnnyg on 2007-10-28
I'm still a  bit puzzled what the actual problem here is.

As far as I can tell, you boot the system and get a gdm login screen.

You log on, fire up nautillus and the "Refusing to initialise gtk+" message appears in .xsession-errors.

Apart from the message, does everything work fine?   If not, what does not work?

You mention that other threads have advised deleting "the file".  Which file is that?

John

---

### Post by evilc on 2007-10-28
> **johnnyg said:**
> I'm still a  bit puzzled what the actual problem here is.

As far as I can tell, you boot the system and get a gdm login screen.

You log on, fire up nautillus and the "Refusing to initialise gtk+" message appears in .xsession-errors.

Apart from the message, does everything work fine?   If not, what does not work?

You mention that other threads have advised deleting "the file".  Which file is that?

John

Maybe I don't explain myself clearly so I suggest do a search on "Refusing to initialize GTK+". You will find plenty of various problems associated, over my own reloads I have had "sound,video and graphics fail (and unknown lock ups).

One of my friends who has changed to linux (6mths) installed Gutsy thinking it was similar but more up to date to Feisty now has no _sound_ , big problem as he works with music. He now thinks linux is a joke and considering going back to his original MS setup. This is the type of reaction the linux community face.

---

### Post by evilc on 2007-10-28
Sorry forgot to add my xsession error file,  (this is straight from boot up).
_________________
(process:5326): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5330): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/clive:/tmp/.ICE-unix/5323
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Initializing gnome-mount extension

(process:5488): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed
** Message: Not starting remote desktop server
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by johnnyg on 2007-10-29
> **evilc said:**
> Maybe I don't explain myself clearly so I suggest do a search on "Refusing to initialize GTK+". You will find plenty of various problems associated, over my own reloads I have had "sound,video and graphics fail (and unknown lock ups).

One of my friends who has changed to linux (6mths) installed Gutsy thinking it was similar but more up to date to Feisty now has no _sound_ , big problem as he works with music. He now thinks linux is a joke and considering going back to his original MS setup. This is the type of reaction the linux community face.

Clive,

I'm not prepared to go googling to find out what your >specific< problem is here.   I did do a bit of googling on the gtk error, but like you say it >seems< to be associated with a number of problems.  It may well be completely unrelated to many of them. 

Just some background here, I was going through unanswered forum posts the other day and came across yours + it seemed to me the main reason you were not getting an answer was you were not providing enough information for people to understand what the problem was.

Re: you friend.  This is unfortunate.  I just went through feisty -> gutsy myself and it was not without its problems, mostly due to stuff I had tinkered with in feisty.

Unfortunately, upgrades can be precarious (fresh installs tend to be much less troublesome, since the installer is working with a clean slate).   Backups are always a good idea in case you have to bail out back to the previous version.

John

---

### Post by evilc on 2007-10-29
All the reloads have been new installations. I have been with Ubuntu since Warty, Gutsy by far the worse released may have to go back to Feisty and just give up.

---

