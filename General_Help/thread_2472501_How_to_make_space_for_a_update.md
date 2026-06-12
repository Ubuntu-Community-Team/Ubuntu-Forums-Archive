---
title: "How to make space for a update"
date: 2022-03-01
forum: General Help
---

### Post by kumaz on 2022-03-01
I ran the update manager and it said I  did not have enough space to update,Is there some other way to clear up  space on ubuntu without using command line get clean for the update? One that is"safe" to use?
Thanks in advance

---

### Post by coffeecat on 2022-03-01
Support request, not chat.

*Thread moved to **General Help**.*

---

### Post by MAFoElffen on 2022-03-01
A GUI based one? Not that I know of or use... Except in File Manager,emptying Your Trash Can.

Way back a decade ago, there used to be one that was part of Ubuntu Tweak, called Janitor... I went through it's code, and it automated a few basic things together into one GUI tool.

What it boils down to using that methodology, is to delete the caches on all browsers, all temp files, apt clean, apt  autoremove, etc.

Then take a look at what is still taking up space and is not that important to you anymore? Is there something you installed and no longer have used for years? Are there files that can be deleted, moved elsewhere or compressed?

Or, would you like to add more storage from additional drives?

These later mentioned decisions are all your own.

---

### Post by kumaz on 2022-03-01
Thank you so much for the help

---

### Post by Dennis N on 2022-03-01
How much more space did the message say you need? If you've been running your OS for a while, you may be able to recover 1G or more from the systemd journal by specifying the size of the journal files to keep. This is quick and easy. Below is a real example on this computer. The 20M I specified to keep below is arbitrary, but big enough to keep recent journal files. 

```
dmn@Sydney-vm:~$ sudo journalctl --vacuum-size=20M
[sudo] password for dmn:
...omitted progress output...
Vacuuming done,** freed 2.6G of archived journals** from /var/log/journal

```

---

### Post by ActionParsnip on 2022-03-01
what is the output of
```

df -h

```

---

### Post by grahammechanical on 2022-03-01
If you get a Grub menu select Advanced Options for Ubuntu and then select a Linux kernel with Recovery Mode. At the Recovery menu select Clean. That option is a script that will run two commands.

1) apt-get clean = clears out the local repository of retrieved packaged files.

2) apt-get autoremove = removes packages that were automatically installed to satisfy dependencies for other packages and are no longer needed.

Regards

---

### Post by hanna091 on 2022-03-02
Remove Old Kernels (If you do not want to keep them anymore)
Uninstalling the Apps and Games that you do not use.*
Cleaning the APT Cache*.Ubuntu runs a simple command to remove the apt-cache data/sudo apt-get clean/This command deletes all the packages stored in the apt-cache, nevertheless of age or the need.
Use BleachBit cleaner for the system.Bleatbit can delete the cache of more than 70 desktop applications. This includes most web browsers. Clean up old files, browse, and hit history. This prevents you from reading all the simple crash logs.
These are my suggestions and if you want additional information you can check this out, was helpful for me [https://clearcachewiki.com/essential-guide-5-simple-ways-to-free-up-space-on-ubuntu/](https://clearcachewiki.com/essential-guide-5-simple-ways-to-free-up-space-on-ubuntu/)

---

### Post by Impavidus on 2022-03-02
Be careful with bleachbit. The forum is full of threads where it removed too much and you can definitely keep your system clean without it. I've managed to do so for the past 15 years. Not all recommendations in the blog post linked above (if I understand them correctly, given all the spelling errors) appear sound and most of the cleaning mentioned is already done automatically.

In case of OP, if there's not enough space for an update, the problem is usually in a /boot partition The root partition is so large compared to the space needed for an upgrade that it's unlikely you fill all of it during an upgrade. So you have to find out the partition where there's not enough space, then think of a plan. Clearing cache won't help in case of a full /boot partition.

---

### Post by him610 on 2022-03-04
> not have enough space to update
I have seen that advisory message when /boot became to full.

---

### Post by rsteinmetz70112 on 2022-03-05
I second the caution about bleachbit. It is a pretty blunt instrument and can easily cause lots of problems. It is best used by people who understand Linux very well.

I find that /var/log can accumulate a lot of data, clearing out old logs can help. I've never needed to go back that far to resolve a problem. I've also found that sometimes if a file system is not mounted a lot of stuff can accumulate in the mount point and is hidden when the filesystem is mounted. This is especially true if an external drive is mounted on the mount point. I've started creating a file under the mountpoint with the name of "DRIVE IS NOT MOUNTED". Someone here mentioned that trick. I'd never thought of it but it's pretty useful.

---

