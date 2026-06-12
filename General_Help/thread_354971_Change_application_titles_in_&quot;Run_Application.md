---
title: "Change application titles in &quot;Run Application&quot;?"
date: 2007-02-06
forum: General Help
---

### Post by feed5000 on 2007-02-06
How do I make it so that I can use "terminal" instead of "gnome-terminal" in the "Run Application" window (alt+F2)?

I gather that the change must occur in the gnome-terminal.desktop file under /usr/share/applications.  But I can't figure out what change to make exactly.

I've tried changing each of the following options from "gnome-terminal" to "terminal," but none of them worked (even with all at once changed):
TryExec=
Exec=
X-GNOME-Bugzilla-Product=
X-Ubuntu-Gettext-Domain=

I've also noticed that if I use Nautilus to bring up the /usr/share/applications folder, and if I right-click on the Terminal icon, go to properties, and click the Launcher tab, there is a promising dialog for changing the command.  However, I don't know how to get the authority to modify this tag apart from the command line.  Besides, I would ideally like to know where exactly this setting is stored on the gnome system.

Any ideas?

---

### Post by etank on 2007-02-06
You can create a symbolic link like this.
```
sudo ln -s /usr/bin/gnome-terminal /usr/bin/terminal
```

Then you have a shortcut named terminal that points to gnome-terminal

---

### Post by kerry_s on 2007-02-06
I'm not sure if it's the same in gnome, but i usally /usr/share/applications and  /usr/share/menu, so they both match up.

---

### Post by feed5000 on 2007-02-06
Ok, cool.  The link worked perfectly.  Thanks for the helpful tip.

---

### Post by feed5000 on 2007-02-06
kerry_s,

Your post is missing a verb, and I can't figure out what you were trying to say.

The symbolic link mentioned in the post previous to yours is what I was looking for. I guess the Run Application window has access to all of the executables referenced in $PATH, and not just what has a .desktop entry in /usr/share/applications?  Thus, I don't need to mess with the .desktop files and can simply create symbolic links.

---

### Post by kerry_s on 2007-02-06
> **feed5000 said:**
> kerry_s,

Your post is missing a verb, and I can't figure out what you were trying to say.

The symbolic link mentioned in the post previous to yours is what I was looking for. I guess the Run Application window has access to all of the executables referenced in $PATH, and not just what has a .desktop entry in /usr/share/applications?  Thus, I don't need to mess with the .desktop files and can simply create symbolic links.

Sorry, i'm alittle tired. I'm doing home repairs for grandma and had just finished stripping and painting the security doors. I just been hitting up the forums when taking a break. I'm usally better at helping :)  Well time to fix that leaky kitchen sink. Laters ):P

---

