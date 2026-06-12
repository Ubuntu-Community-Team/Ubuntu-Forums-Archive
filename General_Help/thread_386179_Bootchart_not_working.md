---
title: "Bootchart not working"
date: 2007-03-16
forum: General Help
---

### Post by 23meg on 2007-03-16
I've installed Bootchart from the repositories. I do have a /var/log/bootchart directory, but even though I've rebooted multiple times, no image files were created there; there's no /var/log/bootchart.tgz either.

I'm using Sun Java 1.5.0. Any ideas?

---

### Post by bravemosquito on 2007-03-30
Images must appear in **/var/log/bootchart** directory. However, bootchar.tgz file may be deleted after creating bootchart image. But I'm not sure for that. Nothing found in documentation about it...

If u wish I'll post my installed java packages

---

### Post by 23meg on 2007-04-02
Nothing ever got created in my case. I'll try it on Feisty with the same Java version.

---

### Post by bravemosquito on 2007-04-02
Did you see this in Synaptic:

> [b]bootchart (version 0.9-0ubuntu7) will be installed
librsvg2-bin (version 2.16.0-0ubuntu2) will be installed[/b]

---

### Post by prostar on 2007-12-15
I've also installed bootchart and it's dependancies, but there's no output to be seen!  How does one "enable" bootchart?  can I just edit the grub menu for one boot instead of always having it "on"?

---

### Post by il-luzhin on 2008-01-08
same problem

---

### Post by _Stevie_ on 2008-02-07
same here, i had sun-java6 installedon gutsy. removing it didnt help.
im running another version of gutsy in virtualbox, no java is installed there.
it works flawlessly there.

---

### Post by il-luzhin on 2008-03-12
a fix 

[https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/185523](https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/185523)

---

