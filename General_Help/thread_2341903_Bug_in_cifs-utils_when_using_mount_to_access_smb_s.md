---
title: "Bug in cifs-utils when using mount to access smb shares"
date: 2016-11-01
forum: General Help
---

### Post by jamesisin on 2016-11-01
Ok.  I've been working at sussing out this problem for a while now, and I think I'm finally getting close to the source of the matter.

In short, I have an Ubuntu server which is serving a number of shares using Samba.  When I access any of those shares with, say, a 12.04 machines I have no problem with certain characters in file or folder names.  However, newer versions of Ubuntu are not playing so nicely.

There are at least two characters at odds with these newer versions of Ubuntu: the colon (:) and the question mark (?).  I have mangled file names disabled, and remember Ubuntu 12.04 is accessing these files and folders without any trouble.  Newer versions may error (can't find object) on either or both a file or folder name.  I have created a complete testing matrix here.

[http://jamesisin.com/a_high-tech_blech/index.php/2016/10/notes-from-possible-cifs-utils-bug/](http://jamesisin.com/a_high-tech_blech/index.php/2016/10/notes-from-possible-cifs-utils-bug/)

There you will find Ubuntu versions, cifs-utils versions, and comparisons of the behaviors for each character and comparisons with mounts created with Nautilus.

Next steps?  Is there more testing I need to be doing?  Where can I file a bug for cifs-utils?

(I've also identified an issue with Nautilus but I can sit on that for now.)

---

### Post by cariboo on 2016-11-01
You can create a bug report at [bugs.launchpad.net]("https://bugs.launchpad.net/") (you need to have an account). To make sure your bug reort is valid, have a look [here]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by jamesisin on 2016-11-01
I filed a bug over at Launchpad.  Thanks.

[https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1638448](https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1638448)

---

