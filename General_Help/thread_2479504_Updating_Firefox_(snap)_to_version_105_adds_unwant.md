---
title: "Updating Firefox (snap) to version 105 adds unwanted fs in System Monitor"
date: 2022-09-27
forum: General Help
---

### Post by Seb71 on 2022-09-27
I have this issue on two computers (both with Ubuntu 22.04 LTS).


After updating Firefox (snap) from version 104 to version 105 (105.0.1 64bit), Gnome System Monitor shows an additional file system:

**/var/snap/firefox/common/host-hunspell**


See the attached screenshot:

[IMG]https://i.imgur.com/5UIYlS3.png[/IMG]

I looked in the gnome-system-monitor settings (using dconf) and could not find any option to remove this.

**How can I fix this (remove from display)?**

---

### Post by vanadium on 2022-09-27
You do not really want to remove this. There is no point. It does not affect your daily use of the computer. Quite opposite, removing it may affect your daily work.

---

### Post by Seb71 on 2022-09-27
> **vanadium said:**
> you do not really want to remove this. There is no point. It does not affect your daily use of the computer. Quite opposite, removing it may affect your daily work.

wat

---

### Post by Seb71 on 2022-09-27
Just to clarify, I want that to remove it from showing in gnome-system-monitor. It has no place there when "show all file systems" is not enabled.
I do not want to delete the directory/folder.

Also, look at its size. It's obviously wrong. The size values (Total/Available/Used) duplicate the "/" size values.

---

### Post by ian-weisser on 2022-09-27
host-hunspell is a snap application, commonly associated with Firefox. Like all snap applications, you "remove the filesystem" by simply quitting the application.

```

$ snap list firefox hunspell-dictionaries-1-7-2004 
Name                            Version             Rev   Tracking         Publisher  Notes
firefox                         105.0.1-1           1883  latest/stable/&#8230;  mozilla&#10003;   -
hunspell-dictionaries-1-7-2004  1.7-20.04+pkg-6fd6  2     latest/stable    brlin      -

$ snap info hunspell-dictionaries-1-7-2004 
...snip...
description: |
  This is a content-shared snap for snaps that depend on the Hunspell spellchecking dictionaries.
  
  This snap does not provide any applications and is not meant for regular users.
  
  Refer "The content interface - doc - snapcraft.io" topic for information of using this snap:
  https://forum.snapcraft.io/t/the-content-interface/1074/1
...snip...

```

And let's also refer to [https://snapcraft.io/install/hunspell-dictionaries/ubuntu](https://snapcraft.io/install/hunspell-dictionaries/ubuntu)

Okay, we can put two and two together now.

You're looking at a content-sharing snap, likely intended so Firefox can access the hunspell dictionary.

It's a snap, which is why it looks unusual in System Monitor.

To "remove the filesystem", try using "ps" to identify the process using hunspell, and terminate that process.

---

### Post by Seb71 on 2022-09-27
I do not want to kill any process (which would have consequences).

I want to make gnome-system-monitor to only display the actual partitions on my SSD, like it's supposed to do (when "show all file systems" is disabled).

I use it for a quick glance to the free space on each partition.

/var/snap/firefox/common/host-hunspell has no place being shown there. It's not a partition.

---

### Post by ian-weisser on 2022-09-27
> **Seb71 said:**
> I do not want to kill any process (which would have consequences).

Then consider revisiting your willingness to live with what you have.

Or let us know what changes you are willing to make.

Stopping the process that creates the issue --if you are not using it-- is the easiest and safest way to accomplish what you seek.

---

### Post by Seb71 on 2022-09-27
> **ian-weisser said:**
> Then consider revisiting your willingness to live with what you have.

If you do not have an answer to the actual question, then do not reply.

Also I know I can switch distributions, no need to tell me that either.

---

### Post by vanadium on 2022-09-28
This mount is a trick from the snap developers to allow firefox snap to see the user's hunspell directories (dictionaries for spell check). If you insist on removing it, you can the usual way:
```

sudo umount /var/snap/firefox/common/host-hunspell

```
Likely, the only side effect will be that Firefox cannot use dictionaries installed on your system, but you may have enough with the dictionaries available in the snap.

---

### Post by Seb71 on 2022-09-28
> **vanadium said:**
> This mount is a trick from the snap developers to allow firefox snap to see the user's hunspell directories (dictionaries for spell check). If you insist on removing it, you can the usual way:
```

sudo umount /var/snap/firefox/common/host-hunspell

```
Likely, the only side effect will be that Firefox cannot use dictionaries installed on your system, but you may have enough with the dictionaries available in the snap.

What's so difficult to understand?

I do not want to remove the spellchecker.

I want to make System Monitor (gnome-system-monitor) to not show that file system (when "show all file systems" is NOT enabled in System Monitor's preferences).

---

### Post by Seb71 on 2022-09-28
So I want to hide the 4th line from this screenshot:

[IMG]https://i.imgur.com/5UIYlS3.png[/IMG]

That line should not be displayed when "Show all file systems" is NOT enabled in System Monitor's preferences. In that case only the actual disk partitions should be shown.

---

### Post by vanadium on 2022-09-30
Hiding the entry in System Monitor: System Monitor is programmed to show File Systems. It does not have a feature to hide a line you do not want to see. You will need to file a feature request.

---

### Post by Seb71 on 2022-09-30
> **vanadium said:**
> Hiding the entry in System Monitor: System Monitor is programmed to show File Systems. It does not have a feature to hide a line you do not want to see. You will need to file a feature request.

Yes it is supposed to hide file systems.

When "Show all file systems" setting is OFF, it looks like this:

[IMG]https://i.imgur.com/0AaAqvx.png[/IMG]

When "Show all file systems" setting is ON, it looks like this:

[IMG]https://i.imgur.com/tfv6F2r.png[/IMG]

/var/snap/firefox/common/host-hunspell should not be shown when "Show all file systems" setting is OFF.

---

### Post by vanadium on 2022-10-01
I see.

---

