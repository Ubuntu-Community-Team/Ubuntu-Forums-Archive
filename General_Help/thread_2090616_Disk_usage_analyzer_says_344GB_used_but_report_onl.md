---
title: "Disk usage analyzer says 344GB used but report only lists 10GB"
date: 2012-12-02
forum: General Help
---

### Post by kingpin298 on 2012-12-02
Title says most of my problem.  I was recently running into warnings saying I was low on disk space.  After running the disk usage analyzer I removed some old backups and cleared out some extra space.  However it is reporting that my 488GB hard drive is using 344GB but the detailed report only lists the '/' directory as having 10GB used.  So my question is where is the other 350+GB being used? I have attached an image of the report as well.


[IMG]https://dl.dropbox.com/u/1907291/Capture.PNG[/IMG]

---

### Post by oldfred on 2012-12-02
I have never understood disk usage analyzer.

I prefer gparted as a nice graphical view.

And several commands from terminal.

sudo fdisk -lu

df -H

---

### Post by kingpin298 on 2012-12-03
Figured out my problem.  I'm running a WebSphere MQ server for a project and it seems to be reserving hard drive space for every message it could get.  And for some reason that was not showing as an actual file.

---

### Post by dcstar on 2012-12-04
> **kingpin298 said:**
> Figured out my problem.  I'm running a WebSphere MQ server for a project and it seems to be reserving hard drive space for every message it could get.  And for some reason that was not showing as an actual file.

The Disk Usage analyser runs in user mode, so you don't see system files. Run it with sudo if you want all the files counted.

Mark the thread if the problem is solved.

---

### Post by The Cog on 2012-12-04
If you run disk usage analyser under your own account rather than as root, it may not find files in other user's directories. My guess is that websphere keeps a directory that is only accessible to itself.

---

