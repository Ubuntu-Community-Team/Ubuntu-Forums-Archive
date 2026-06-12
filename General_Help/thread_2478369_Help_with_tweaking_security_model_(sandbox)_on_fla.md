---
title: "Help with tweaking security model (sandbox) on flatpak, please"
date: 2022-08-24
forum: General Help
---

### Post by Paddy Landau on 2022-08-24
I need a bit of help with tweaking the security model of the flatpak version of gedit, please.

**Background**

Ubuntu 22.04: I installed the flatpak version of gedit.

The sandbox allows gedit to access all files (filesystem=host).

**The problem**

However, for reasons that I don't understand, it prevents access to some files. For example, while I can access /etc/hosts, I cannot access /etc/fstab.

I have added everything that I can think of: filesystem=host-os, filesystem=host-etc, filesystem=home, and both /etc and /etc/fstab.

However, gedit still doesn't see /etc/fstab.

(There are other files where I have the same problem, but I'll try to solve just this one to start.)

**Question**

How do I add /etc/fstab to flatpak's sandbox for gedit?

---

### Post by &amp;KyT$0P# on 2022-08-24
I could read it at [FONT=Courier New]/run/host/etc/fstab[/FONT] (went to gedit's Open button > "Other Documents..." and then browsed to that file in that window).  But it opened read-only.  (This is without adjusting the sandbox permissions)

---

### Post by Paddy Landau on 2022-08-24
> **halogen2 said:**
> I could read it at [FONT=courier new]/run/host/etc/fstab[/FONT]
Thank you! I had not heard of [FONT=courier new]/run/host[/FONT]. When I search for this online, I get a host of unrelated links. Is this meant to link directly to otherwise-inaccessible files and folders? Is it flatpak-specific?
> **halogen2 said:**
> it opened read-only.
For a normal user, it should be read-only. Only if opened with root privileges should it be read-write.

---

### Post by &amp;KyT$0P# on 2022-08-24
> **Paddy Landau said:**
> I had not heard of [FONT=courier new]/run/**host**[/FONT]. When I search for this online, I get a **host** of unrelated links.

(bolding mine)
pun intended? :D

I believe I learned about /run/host from one of the Flatpak man pages, but unfortunately not sure which one and not finding it again :(

> Is this meant to link directly to otherwise-inaccessible files and folders? Is it flatpak-specific?

These answers were also in the same man page.  If I remember correctly it's a Flatpak-specific way to provide access to system files and folders that are located at paths that could conflict with the flatpak environment.

---

### Post by pbear42 on 2022-08-24
I've been sitting out Flatpak so far (also Snap), but follow casually.  You might want to review [Sandbox Permissions]("https://docs.flatpak.org/en/latest/sandbox-permissions.html") in the official documentation.  Among other things, mentions that /etc is mounted under /var/run/host.  Testing in a VM, that indeed works for me.  Which is to say, gedit as Flatpak doesn't see fstab when try to open directly, but does see (and can open) when use /var/run/host path.  Interestingly, also can open with the gedit Flatpak from right-click of regular location in File Manager.

ETA: In the interesting computer tricks department, wondered how to go directly to elevated editing privileges.  Thing is, *gedit* isn't recognized in Terminal.  There, the command to run as Flatpak is *flatpak run org.gnome.gedit*.  So, it's not elegant, but *flatpak run org.gnome.gedit admin:///etc/fstab*. will open the file directly and available-for-edit (not read-only).  Requires sudo/admin password, of course, but works.  If doing this sort of thing often, the flatpak command could be made an alias.

---

### Post by Paddy Landau on 2022-08-25
> **halogen2 said:**
> pun intended? :D
It wasn't! But it's a nice one, ha ha
> **halogen2 said:**
> I learned about /run/host from one of the Flatpak man pages…
> **pbear42 said:**
> You might want to review [Sandbox Permissions]("https://docs.flatpak.org/en/latest/sandbox-permissions.html")…
Ah! I missed that before. Thank you; it explains it all.
> **pbear42 said:**
> … *flatpak run org.gnome.gedit admin:///etc/fstab*
I have found an easy way around this.

As some background, I use SUDO_EDITOR, so in my .bashrc, I have
```
export SUDO_EDITOR=gedit
```
Thus, I can issue (for example)
```
sudoedit /etc/fstab
```
With flatpak, this still works, if I create a file [FONT=courier new]~/bin/gedit[/FONT] that contains just one line:
```
flatpak run org.gnome.gedit "${@}"
```
But…

You must add [FONT=courier new]/var/tmp[/FONT] to gedit's permissions. Do that in either Flatseal or the CLI:
```
flatpak override --user --filesystem=/var/tmp org.gnome.gedit
# --user means for you only, not everyone on the system.
```
Then, you can use either:
```
gedit /var/run/host/etc/fstab  # Read-only, obviously
sudoedit /etc/fstab            # Read-write
```
With some fiddling in the [FONT=courier new]gedit[/FONT] script, you'd be able to prefix suitable paths with [FONT=courier new]/var/run/host[/FONT], so that you could use gedit [FONT=courier new]/etc/fstab[/FONT].

EDIT: The documentation says that we should use [FONT=courier new]/var/run/host[/FONT], but I have found that [FONT=courier new]/run/host[/FONT] also works! I shall stick with the documentation, for safety.

I think that I can mark this thread as solved! Thank you all!

---

### Post by &amp;KyT$0P# on 2022-08-25
You're welcome! :KS

> **Paddy Landau said:**
> EDIT: The documentation says that we should use [FONT=courier new]/var/run/host[/FONT], but I have found that [FONT=courier new]/run/host[/FONT] also works! I shall stick with the documentation, for safety.

For what it's worth, on Ubuntu (and some other distros as well) [FONT=Courier New]/var/run[/FONT] is deprecated in favor of [FONT=Courier New]/run[/FONT] and is just a symlink to [FONT=Courier New]/run[/FONT] (and whichever man page I saw did use literally [FONT=Courier New]/run/host[/FONT] )

> **pbear42 said:**
> Interestingly, also can open with the gedit Flatpak from right-click of regular location in File Manager.

In this case it uses a portal to access the file.

---

### Post by Paddy Landau on 2022-08-25
> **halogen2 said:**
> For what it's worth, on Ubuntu (and some other distros as well) [FONT=Courier New]/var/run[/FONT] is deprecated in favor of [FONT=Courier New]/run[/FONT] and is just a symlink to [FONT=Courier New]/run[/FONT] (and whichever man page I saw did use literally [FONT=Courier New]/run/host[/FONT] )
That's interesting, thank you.

I used Google to search the man pages for [FONT=courier new]/run/host[/FONT], and it used [FONT=courier new]/var/run/host[/FONT]. So, we must have seen different pages.

---

