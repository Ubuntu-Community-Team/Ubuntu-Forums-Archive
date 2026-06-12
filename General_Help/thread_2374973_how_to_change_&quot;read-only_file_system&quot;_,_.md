---
title: "how to change &quot;read-only file system&quot; , taking ownership"
date: 2017-10-20
forum: General Help
---

### Post by mgudarzi on 2017-10-20
I just installed Vuze(utorrent client). it tries to install its updates in  /snap/vuze-vs/2/opt/vuze , but it's not possible and it shows me a message that "The location '/snap/vuze-vs/2/opt/vuze' isn't writable, this update will probably fail. Check permissions and retry the update". so ... i tried to fix the directorie's ownership using "chmod" and thats stuff but the problem is it gives me the "read- only file system" error. in fact, i don't have w/r permissions to anything in /snap. i would really appreciate if someone can help me with this or at least shows me the right direction.

thank you

---

### Post by SeijiSensei on 2017-10-20
If you have a "read-only file system" error, it means the entire filesystem needs to be checked for consistency.  Reboot and see if the problem goes away; Ubuntu should detect the problem during bootup and run a filesystem check.  If you still have the problem, come back here and report on your progress.

---

### Post by mgudarzi on 2017-10-21
[ATTACH=CONFIG]277195[/ATTACH][ATTACH=CONFIG]277196[/ATTACH]

Hello again , 

Thanks for your reply. Unfortunately the promlem persists . i restarted , i also forced a fsck using the recovery mode and it came out with no errors. i dont know what to do. tbh , i dont even care about the update, but it seems like that if this is giving me a hard time now, it will again later, so i really wanna fix it . also i'm running a 16.04. I appreciate 
any possible help. 

Thank you.

---

### Post by efflandt on 2017-10-21
Typically you need to use **sudo** prefix when installing things that need to be installed by root, or alternately **gksu** prefix if using a gui app in X to install something as root that does not already request your password. But I am not at all familiar with snap apps or vuze.

---

### Post by SeijiSensei on 2017-10-22
Before running the installer, enter the "mount" command and look at the permissions on each mounted filesystem.  Does the filesystem where /snap is located have the "rw" option, or just "ro"?  For instance, the primary filesystem should look something like this:

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
```

Other mounted filesystems will usually not have the "errors=remount-ro" option enabled and look like this:

```
/dev/sda2 on /home type ext4 (rw)
```

---

