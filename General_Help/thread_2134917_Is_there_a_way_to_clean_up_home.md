---
title: "Is there a way to clean up /home?"
date: 2013-04-12
forum: General Help
---

### Post by xeddog on 2013-04-12
I have another thread about some problems with nautilus, but that has me wondering if there is a way to clean up my home directory.  In short, my home directory resides on a separate disk drive and I have recently installed 12.04 on a new disk.  During trying to resolve my nautilus problems I have gone through my home directory and there is a BUNCH of stuff that is no longer needed.  Mostly a ton of applications that I may have installed, tried out, and then removed but config files and other assorted junk remain behind.  I have seen computer janitor but from the reviews I don't think I want to go that route.  And Ubuntu-tweak I am looking into now, but it doesn't seem to run.  The screen just goes dark and stays dark (at least for about 15 minutes and then I force quit it).

Any other ideas???


Thanks,

X

---

### Post by Vaphell on 2013-04-12
unhide hidden files (ctrl+h), delete any .program or .config/program directory you think is no longer needed. Deleting directory can also be used to reset program settings to defaults.

---

### Post by snowpine on 2013-04-12
This is normal and nothing to worry about (unless you are desperately low on disk space). If you choose to reinstall one of those apps someday,then all of your documents and data will be intact. It would be weird if uninstalling an app deleted personal data/settings in your /home folder. For example "I'm having trouble with Evolution, so I think I'll uninstall and reinstall. Whoops, where are all my emails???" :)

---

### Post by ibjsb4 on 2013-04-12
On the other end of the stick from computer janitor is [BleachBit]("https://apps.ubuntu.com/cat/applications/precise/bleachbit/").  Been using it for years and have found it safe and dependable.

---

### Post by CaptainMark on 2013-04-12
Sometimes I like to start a new install (usually when an LTS comes out) with a more or less fresh slate and de-junk most of my config folders too, to do this I just do a complete re-format install and wipe everything and selectively restore from my back up drive, using ```
cp -r /media/passport/mark/* ~/ 
```will copy all my non-hidden data folders (Music Pictures etc.) back to my newly made home folder then I'll just selectively copy the few config folders for my most used applications like banshee and xchat across too, and let all other apps create their own config files again from fresh. It feels good if like me you're a computer OCD nutcase, like you've had a proper spring clean. This is not so easy to do to an existing install but we are mere days away from a new Ubuntu release so perhaps this is the best time to do it.

PS. I know I sound like a mental, but hey ho, I've had worse.

---

### Post by weq92f on 2013-04-12
Why not just go hunting around in there to find big stuff you don't need:

cd $HOME
du -ks *|sort -n  # This shows the size of each file/directory

cd <a big one from above>
du -ks *|sort -n

repeat...

Hth,

-klb

---

### Post by Zukaro on 2013-04-13
You could just delete the things you don't want manually.  I don't know of an automated way to do it.
However, when you're deleting programs that you've downloaded via packages do```
sudo apt-get purge *packagename*
``` as that will remove EVERYTHING from that package (including config files etc).

---

### Post by ibjsb4 on 2013-04-13
> **Zukaro said:**
> However, when you're deleting programs that you've downloaded via packages do```
sudo apt-get purge *packagename*
``` as that will remove EVERYTHING from that package (including config files etc).

Configuration files residing in ~ (Home) are not usually affected by this command.

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by ofnuts on 2013-04-13
To find if a directory is useful you can see if it contains files accessed recently. To get the most recently accessed file in a directory tree:
```

find $directory -type f -exec stat -c '%x %n' {} \+ | sort -r | head -1

```

---

### Post by pfeiffep on 2013-04-13
+1

> **ibjsb4 said:**
> On the other end of the stick from computer janitor is [BleachBit]("https://apps.ubuntu.com/cat/applications/precise/bleachbit/").  Been using it for years and have found it safe and dependable.

I've been using bleachbit for just a few months and find it extremely useful; one the other hand if you're really interested in learning more about Linux the cli options on this thread are useful

---

### Post by ibjsb4 on 2013-04-13
> **pfeiffep said:**
> I've been using bleachbit for just a few months and find it extremely useful; one the other hand if you're really interested in learning more about Linux the cli options on this thread are useful

This is helpful too

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Edit: There should be a warning with deborphan. It can remove necessary packages, use with caution.

[URL="http://ubuntuforums.org/showthread.php?t=140920"]














[/URL]

---

