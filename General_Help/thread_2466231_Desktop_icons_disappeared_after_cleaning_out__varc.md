---
title: "Desktop icons disappeared after cleaning out  /var/crash"
date: 2021-08-23
forum: General Help
---

### Post by artist-wavenet on 2021-08-23
I upgraded from Ubuntu 18.04 to 20.04. In Ubuntu 18.04, whenever I booted up, I would get a dialog box with the message "System program problem detected . Report?". I expected this would go away after the upgrade but it did not. In an effort to eliminate this message I executed this command:

```
sudo rm -r /var/crash *
```

This cleaned out all in my /var/crash directory. This did work to eliminate the error message after reboot, and log in. It also eliminated most of the shortcut icons on my desktop. I can't figure how deleting crash reports would do that.

Why did the shortcut desktop icons disappear? What is the best way to recover them?

---

### Post by monkeybrain20122 on 2021-08-23
Just backup data and do a clean install. If you have cruffs in your system and getting error upgrading is more likely to give you issues.

---

### Post by artist-wavenet on 2021-08-23
The mistake was the asterisk in the command that also deleted all in my home directory. When I did it I thought it was a wild card that would select all in /var/crash.

Fortunately just before I upgraded to Ubuntu 20.04 I backed up all in the home directory. I used that backup to restore it.

---

### Post by GhX6GZMB on 2021-08-23
The icon files for your desktop are normally in $Home/Desktop in the form of .desktop files.

---

### Post by tea for one on 2021-08-24
> **artist-wavenet said:**
> I upgraded from Ubuntu 18.04 to 20.04. In Ubuntu 18.04, whenever I booted up, I would get a dialog box with the message "System program problem detected . Report?". I expected this would go away after the upgrade but it did not. In an effort to eliminate this message I executed this command:

```
sudo rm -r /var/crash *
```

This cleaned out all in my /var/crash directory. This did work to eliminate the error message after reboot, and log in. It also eliminated most of the shortcut icons on my desktop. I can't figure how deleting crash reports would do that.

Why did the shortcut desktop icons disappear? What is the best way to recover them?
When you executed the command, which directory were you in?

Why is there a space between crash and the asterisk?

In effect, I think the command applied to two destinations.

---

### Post by HermanAB on 2021-08-25
Yes, if you look at man rm, you will see that it can indeed operate on multiple paths at the same time, so it is that space, instead of a slash, that broke your system.

Remove files from arbitrary locations:
rm {{/path/to/file}} {{/otherpath/to/file2}}

---

