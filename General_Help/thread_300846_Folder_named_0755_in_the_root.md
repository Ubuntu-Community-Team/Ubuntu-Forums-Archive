---
title: "Folder named 0755 in the root"
date: 2006-11-16
forum: General Help
---

### Post by druhboruch on 2006-11-16
I have an empty folder named 0755 in the root.
If I delete it, it comes back on the next reboot.
I have it on 3 computers running edgy.

What is it for?  Does anyone else has it as well?

---

### Post by Tri_X_Troll on 2006-11-16
I would suspect, though I am on a windows machine at work, that it has hidden files in it.

Go into the folder and hit ctrl+h to see the hidden files

---

### Post by druhboruch on 2006-11-16
No.  It is empty.  Octal permission:1600755 Owned by root.

---

### Post by dannyboy79 on 2006-11-16
lets see something, cd to /, then do ls -l. copy and paste the output please. thanks

those are both lowercase L's.

---

### Post by druhboruch on 2006-11-16
Here is the output:

total 112
drwxr-xr-x  2 root root  4096 2006-11-16 08:56 0755
drwxr-xr-x  2 root root  4096 2006-10-26 09:07 bin
drwxr-xr-x  3 root root  4096 2006-10-26 09:07 boot
lrwxrwxrwx  1 root root    11 2006-10-26 08:59 cdrom -> media/cdrom
drwxr-xr-x 13 root root 13440 2006-11-16 08:55 dev
drwxr-xr-x 96 root root  4096 2006-11-16 09:22 etc
drwxr-xr-x  3 root root  4096 2006-10-26 09:07 home
drwxr-xr-x  2 root root  4096 2006-10-26 09:02 initrd
lrwxrwxrwx  1 root root    33 2006-10-26 09:05 initrd.img -> boot/initrd.img-2.6.17-10-generic
drwxr-xr-x 15 root root  4096 2006-10-26 09:44 lib
drwxr-xr-x  2 root root 49152 2006-10-26 08:59 lost+found
drwxr-xr-x  4 root root  4096 2006-11-14 19:21 media
drwxr-xr-x  2 root root  4096 2006-10-19 18:49 mnt
drwxr-xr-x  2 root root  4096 2006-10-26 09:02 opt
dr-xr-xr-x 98 root root     0 2006-11-16 08:55 proc
drwxr-xr-x 14 root root  4096 2006-11-15 18:42 root
drwxr-xr-x  2 root root  4096 2006-10-26 09:44 sbin
drwxr-xr-x  2 root root  4096 2006-10-26 09:02 srv
drwxr-xr-x 11 root root     0 2006-11-16 08:55 sys
drwxrwxrwt 11 root root  4096 2006-11-16 09:15 tmp
drwxr-xr-x 13 root root  4096 2006-11-03 08:15 usr
drwxr-xr-x 13 root root  4096 2006-10-26 09:02 var
lrwxrwxrwx  1 root root    30 2006-10-26 09:05 vmlinuz -> boot/vmlinuz-2.6.17-10-generic

---

### Post by dannyboy79 on 2006-11-16
now cd to the 0755 dir, and do ls -al, then past that output. thanx

---

### Post by druhboruch on 2006-11-16
Here it is:

total 8
drwxr-xr-x  2 root root 4096 2006-11-16 08:56 .
drwxr-xr-x 22 root root 4096 2006-11-16 08:56 ..

---

### Post by dannyboy79 on 2006-11-16
huh? if you tried deletig it and then when you restarted it came back, I don't knwo what the heck is up. I don't run edgy so I can't say whether this is suppose to be there? try and run clamav to check this folder? sounds weird!!!! i can't help ya anymore. Can you chown it? what about moving it? renaming it? i don't know?

---

### Post by druhboruch on 2006-11-16
As long as I sudo I can do anything with it.  It is regular empty folder.

I have it on all my edgy installations including those on vmware.

Of course there is a possibility that I have been hacked, but it is unlikely.

Thanks for trying to help me.


Could anyone using Edgy just tel if you have this folder on your system or not.

Thanks.

---

### Post by druhboruch on 2006-11-16
Anyone?  Please.

---

### Post by Gaweph on 2006-11-16
Im actually updating as we speak, so once i reboot, i shall let you know.

:)

---

### Post by behemot on 2006-11-16
I don't have such folder, but I am running dapper

---

### Post by Ramses de Norre on 2006-11-16
I'm on edgy but I've never seen such a folder here..

---

### Post by Gaweph on 2006-11-16
Fresh install of Edgy just completed, no such folder here!!

---

### Post by druhboruch on 2006-11-16
Thank you.
Looks like I am the only one with this problem. I am a bit scared now so I'll   reinstall tonight.

---

### Post by po0f on 2006-11-16
druhboruch,

It is probably an error in a startup script (since you said it comes back on a reboot).  Instead of `mkdir folder && chmod 0755 folder`, it's just `mkdir 0755`.  Check to see what you have enabled to start up at boot, and try to figure it out.

---

### Post by druhboruch on 2006-11-16
Thanks Po0f,

It is a very logical suggestion.  I didn't change any of the startup scripts.   Since it happens on all of my installations it is maybe I am installing from some daily build before edgy final release.  

I will reinstall today using official iso, Looking for a problem would take too much time.

---

### Post by Seq on 2006-11-16
> **druhboruch said:**
> Thanks Po0f,

It is a very logical suggestion.  I didn't change any of the startup scripts.   Since it happens on all of my installations it is maybe I am installing from some daily build before edgy final release.  

I will reinstall today using official iso, Looking for a problem would take too much time.

If you have added any third-part packages, they may have some start-up script as well.

Try this, and hopefully we'll find a script that is a likely culprit (note that several other scripts create directories):
```
grep mkdir /etc/init.d/*
```

---

### Post by druhboruch on 2006-11-16
Seq,

You save me a lot of trouble:

```
/etc/init.d/bacula-fd:          mkdir -p 0755 /var/run/bacula/
```

Bacula file daemon.  I have it on every box...

Thanks, thanks, thanks.

---

