---
title: "Problems with multiple apps after update to 2.6.24-17"
date: 2008-05-31
forum: General Help
---

### Post by mksql on 2008-05-31
After using Win desktops for may years, I am giving Xubuntu a go. It has gone very well, even after allowing the Update Manager to upgrade my laptop from 7.10 to 8.04. After the latest kernal update (and others that appeared at the same time), I have having a few problems.

First upon logging in, I noticed that the top panel bar was significantly rearranged, with some icons missing, others out of place, some launchers pointing to "nothing".

Then I noted that Firefox 2 (downgraded to FF2 until FF3 leaves beta) would not start period. Not from the menu, not from a terminal. Opera works, but not FF, even after a remove and install cycle via apt.

Obiously something is "broke", but I am not experienced enough with Linux to know how to start diagnosing. What logs should I begin looking at?

---

### Post by quelx on 2008-05-31
did you **--purge** when you uninstalled before reinstalling?

eg.
```
sudo apt-get --purge remove firefox-2
```

and 

```
sudo apt-get --purge remove xfce4-panel
```

and if that doesn't work what does firefox spit out in the terminal when you try to run it from there?

---

### Post by mksql on 2008-05-31
I did not purge, will try that now with Firefox.

Why do I want to remove xfce4-panel? 

On a possible cause, I noted that evince-thumbnailer was generating enough files in /tmp to consume all available diskspace, at which pint I began to have problems with the top panel again.

Is it possile that zero disk space can prevent a config or system file from being updated?

---

### Post by anjilslaire on 2008-05-31
> **mksql said:**
> Why do I want to remove xfce4-panel? 

On a possible cause, I noted that evince-thumbnailer was generating enough files in /tmp to consume all available diskspace, at which pint I began to have problems with the top panel again.

Is it possile that zero disk space can prevent a config or system file from being updated?

Because you mentioned that your panel was being funky.
In theory, yes, if a there is no disk space, then yes a file may have trouble updating...

---

### Post by mksql on 2008-05-31
> **quelx said:**
> did you **--purge** when you uninstalled before reinstalling?

eg.
```
sudo apt-get --purge remove firefox-2
```

and if that doesn't work what does firefox spit out in the terminal when you try to run it from there?

purged and installed - no change. Running "firefox-2" in a terminal does not provide any return messages at all. It appears to do nothing.

---

### Post by mksql on 2008-06-01
*Partly solved:* My profiles.ini and pluginreg.dat were both zero bytes, possibly a result of the disk volume running out of space (this is a test partition, with little room for growth).

Also removed evince for the time being to keep the thumbnail service from filling up the volume.

---

