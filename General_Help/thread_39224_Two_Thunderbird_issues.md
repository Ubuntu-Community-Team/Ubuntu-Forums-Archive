---
title: "Two Thunderbird issues"
date: 2005-06-03
forum: General Help
---

### Post by Curlydave on 2005-06-03
Both are very basic.

1: How do you move the thunderbird folder off of the desktop to a folder on the hard-drive? (cut+paste=yea right.)

2: How do you make a desktop shortcut to it? If I do "make link" and click on the created link, it works. If I move that created link to the desktop/task bar etc, it does nothing.

---

### Post by Joeb on 2005-06-03
How did you install thunderbird?  Mine is installed via synaptic and doesn't show on the desktop at all and has a menu entry already created.  Did you manually install it from the mozilla sight?

---

### Post by Curlydave on 2005-06-03
Yes. This doesn't just apply to thunderbird either. I couldn't move other files or create a [working] UT2k4 desktop link either. The links break when I move them.

---

### Post by Joeb on 2005-06-03
If you installed it from the mozilla site, I'd go ahead and install the version via synaptic instead, since it has been tested and integrated into Ubuntu.  That is, of course, unless the version on the Mozilla site is a later version with some must have feature.  Using the official Ubuntu version (via Synaptic), would solve the problems you are experiencing.

In terms of the broken links when you move them, if I'm not mistaken, a desktop shortcut or link, is not the same as a link in a directory.  Instead, it is a .desktop file.  Moving it from the desktop breaks it, because on the desktop executes .desktop files.

You can drop to the command line, in a terminal, and create a symbolic link to the program you are wanting to execute.  But it won't show in the menus (unless you create the desktop file -- sounds like a circular argument, doesn't it).

Anyway, why not describe what you are trying to do (and why) and I'll try to help, unless someone else beats me to it.

Joeb

---

### Post by Curlydave on 2005-06-04
Well, for moving the files I guess I'm looking for a file explorer that doesn't question my authority over my HD, or for a console command that I can use with sudo that moves files.

For the shortcut, I want to be able to pick any file on my HD, and have a shortcut to it on my desktop.

---

### Post by Curlydave on 2005-06-04
bump!

---

### Post by Joeb on 2005-06-04
[QUOTE=Curlydave]Well, for moving the files I guess I'm looking for a file explorer that doesn't question my authority over my HD, or for a console command that I can use with sudo that moves files.

For the shortcut, I want to be able to pick any file on my HD, and have a shortcut to it on my desktop.[/QUOTE]

If I understand you correctly, you are looking to be able to circumvent the built in security permissions to be able to move or copy files where you want them.  From the command line, you would just enter  *sudo mv  directory-old-location directory-new-location*  and it would be done (or substitue files for directory and the files would be moved).

If you prefer using a file manager for that, you would enter *gksudo nautilus* in a terminal window or used in the command for a desktop icon and the nautilus file manager will open up with root access.

Of course, there is danger in doing the above, because you can really screw things up (which is why those permissions exist in the first place). 

As for shortcuts on the desktop, if the application you want is in the menu structure, just click on it and drag it to the desktop.  If it's not, you can right click on the desktop and select create launcher.  If you want to drag and drop it instead, you have more work to do.  While in nautilus as root, you can right click on a program and select create a link.  That will make the link in whatever directory you are in.  You could then drag that link to the desktop.  The better approach, however, would be to create a launcher on the desktop.

These extra steps aren't because of the file manager, but are in fact because how Linux security works.  Unlike Windows, where everyuser pretty much has full access to every file on the hard drive (something virus writes take advantage of), Linux users only have write access to their own files.  In Windows, to secure the system, you need to remove access for each user on the system.  Linux, on the otherhand, starts with the access already removed, and instead you add access to users who really need it.

So, in reality, it's not the filemanger questioning your authority, but the OS itself.



Joeb

---

