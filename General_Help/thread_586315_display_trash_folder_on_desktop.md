---
title: "display trash folder on desktop"
date: 2007-10-22
forum: General Help
---

### Post by Irti on 2007-10-22
hey is there any way i can display my trash folder on the desktop instead of the panel

---

### Post by prince_niceguy on 2007-10-22
right click on desktop --> create new launcher...

give name as Trash
command as nautilus trash:

select the icon that you like...

you are all set.... double click on the icon will open the trash.

---

### Post by nick_h on 2007-10-23
You can also do this by running:
```
gconf-editor
```
and then under /apps/nautilus/desktop setting trash_icon_visible.

---

### Post by ubuntios on 2007-10-27
When I double click the icon I get  ' Failed to execute child process "trash:" (No such file or directory)'

But it works with nick_h's procedure!

---

### Post by Irti on 2007-10-30
both the methods worked fine for me....thanx a lot

---

### Post by Izek on 2007-10-30
> **nick_h said:**
> You can also do this by running:
```
gconf-editor
```
and then under /apps/nautilus/desktop setting trash_icon_visible.

That doesn't exist in my Xubuntu distro. apps/nautilus doesn't exist >>;

---

### Post by Irti on 2007-10-31
i dont think u will have nautilus running in xubuntu.....i aint a pro on the topic but i think u will have to type the name of your file system instead of nautilus.......like nautilus runs for ubuntu....for kde its something else.....and it i think its different for xubuntu as well......try to find out the substitute for nautilus that runs on xubuntu....

---

### Post by jespdj on 2007-10-31
> **Izek said:**
> That doesn't exist in my Xubuntu distro. apps/nautilus doesn't exist >>;
Well, you didn't say you were running Xubuntu, so people are assuming you are running the default Ubuntu with GNOME desktop which includes Nautilus as the file manager.

---

### Post by Izek on 2007-10-31
> **jespdj said:**
> Well, you didn't say you were running Xubuntu, so people are assuming you are running the default Ubuntu with GNOME desktop which includes Nautilus as the file manager.

Xubuntu runs GNOME when you first start it up (Programs bundled with Xubuntu need it), but some things aren't bundled with Xubuntu that should be:

```
metacity package (this is needed if you need to go back to metacity. Xubuntu has libmetacity already installed.)
```

Which makes Xubuntu interesting for support issues >>; 

**Edit:** My profile information above my posts says I run Xubuntu Gutsy. I edited it to say as such *before* I posted here.
**Edit:** I can install nautilus though, as well as the above metacity package. It pays to look through the Synaptics Package Manager.

---

