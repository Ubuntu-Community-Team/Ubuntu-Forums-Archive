---
title: "Uninstall unncessary junk."
date: 2018-11-20
forum: General Help
---

### Post by nerv-agent on 2018-11-20
Hello. I am using Ubuntu 16.04 LTS included on the Dell Precision 7520 laptop.

I have a bunch of stuff I want to remove that I'm not using, like files relating to BitDefender even though I use ClamTK now.

Unfortunately, when I use Synaptic Package Manager to attempt to remove it, everything that is like "Mark for Removal" is grayed out. I'd take a screenshot if I could, but I can't get PrtScr to work when I am right-clicking something.

How do I remove all this junk that is taking up space?

Also, is there a way to determine which libraries or programs haven't been used in awhile so I can remove those, too?

---

### Post by monkeybrain20122 on 2018-11-20
Well if you installed these things yourself through third party methods other than .deb or repositories they won't show up in synaptic. How did you install BD? It is definitely a third party program. BTW, normally you don't need AV in Linux and clamAV checks for Windows virus and is crap anyway.

---

### Post by Autodave on 2018-11-20
That brings up another good reason not to upgrade from one version to another and to always do clean installs: you get rid of a lot of accumulated junk that you no longer need/want/use.  Might be time to backup everything and switch to 18.04.

---

### Post by TheFu on 2018-11-20
I'm guessing the OP bought a Dell with Ubuntu pre-installed and Dell, perhaps, decided to do like they do with Windows and preinstalled stuff commonly known as "crapware."  I don't know that answer, but contacting Dell Support should be helpful.  There is probably a meta-package with Dell in the name that you can force uninstall from a shell command.

However a program is installed, that is how it must be removed, to ensure a consistent APT database.

Debian has a tool called "popularity contest" which keeps track of the programs used.  It is just the programs, not the libraries.

And of course, you can use the normal Linux 'find' command to look for any files that haven't been accessed in X days.  It would look at the accessed time stamp, assuming that your setup tracks those.  It is a mount-time option for all linux file system storage, but it is very popular to turn that off, to improve performance and reduce write counts on SSD storage.

There is another option - download the normal Ubuntu you want and install it yourself.  That would end much of the crapware from being installed.  If you really want a thin install, use the alternate Ubuntu Install disk and install the minimal stuff.  If you are really new to Linux, this is probably way too minimal, but you can do it.  The choice is there.

For the record, the GUI tools are usually 20/80 solutions.  They provide 20% of the capabilities which allow 80% of the needs to be accomplished.  If you want or need full control, use the CLI tools.

We are talking in abstract ideas because no details have been provided.  To get better help, list the exact package name, not the display name.

Lastly, I seriously doubt that these extra packages are using all that much storage. Linux packages just don't take that much storage.  My primary desktop has been running with 17G of space for years.  The OS is more like 9G, which is next to nothing these days where Win7 and later demand 60+G just for the OS.

---

### Post by nerv-agent on 2018-11-20
I recently found something called "GtkOrphan" on the Ubuntu Software Center and tried to remove the leftover Bitdefender junk. Unfortunately, I got this error:

```
Starting...
(Reading database ... 418979 files and directories currently installed.)
Removing bitdefender-scanner:i386 (7.7.1-1809) ...
Purging configuration files for bitdefender-scanner:i386 (7.7.1-1809) ...
find: &#8216;/opt/BitDefender-scanner/share/locale&#8217;: No such file or directory
dpkg: error processing package bitdefender-scanner:i386 (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 bitdefender-scanner:i386
Done.
```

---

### Post by HermanAB on 2018-11-20
You want to unscramble an egg...

Over the years, I have learned to install a server version, in order to get a minimum system, then I install my wanted desktop and utilities myself.  That way, the system starts life lean and mean.  

I never uninstall anything, since that sometimes doesn't go well and I don't want to waste time fixing a messed up system, since nobody pays me to fix my own computer.  Every year or three, I re-install from scratch, to decruftify the machine.

---

