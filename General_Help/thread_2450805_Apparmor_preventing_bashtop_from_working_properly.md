---
title: "Apparmor preventing bashtop from working properly"
date: 2020-09-21
forum: General Help
---

### Post by David_Partridge on 2020-09-21
I just installed bashtop using "snap install bashtop", and I'm getting lots of access denied messages for writing files to my own directories (and other things like access to ps).

I see the following sort of entries in the kernel log.

```
Sep 20 16:03:42 Charon kernel: [108982.625338] audit: type=1400 audit(1600614222.857:123268): apparmor="DENIED" operation="mkdir" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/themes/" pid=28434 comm="mkdir" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.626745] audit: type=1400 audit(1600614222.857:123269): apparmor="DENIED" operation="mkdir" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/user_themes/" pid=28437 comm="mkdir" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.626964] audit: type=1400 audit(1600614222.857:123270): apparmor="DENIED" operation="open" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/bashtop.cfg" pid=28385 comm="bash" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.627754] audit: type=1400 audit(1600614222.861:123271): apparmor="DENIED" operation="open" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/bashtop.cfg" pid=28439 comm="bash" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.629392] audit: type=1400 audit(1600614222.861:123272): apparmor="DENIED" operation="open" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/bashtop.cfg" pid=28385 comm="bash" requested_mask="wc" denied_mask="wc" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.635589] audit: type=1400 audit(1600614222.865:123273): apparmor="DENIED" operation="open" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/bashtop.cfg" pid=28385 comm="bash" requested_mask="ac" denied_mask="ac" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.635681] audit: type=1400 audit(1600614222.869:123274): apparmor="DENIED" operation="open" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/bashtop.cfg" pid=28385 comm="bash" requested_mask="ac" denied_mask="ac" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.635828] audit: type=1400 audit(1600614222.869:123275): apparmor="DENIED" operation="open" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/bashtop.cfg" pid=28385 comm="bash" requested_mask="ac" denied_mask="ac" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.635899] audit: type=1400 audit(1600614222.869:123276): apparmor="DENIED" operation="open" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/bashtop.cfg" pid=28385 comm="bash" requested_mask="ac" denied_mask="ac" fsuid=1000 ouid=1000
Sep 20 16:03:42 Charon kernel: [108982.635983] audit: type=1400 audit(1600614222.869:123277): apparmor="DENIED" operation="open" profile="snap.bashtop.bashtop" name="/home/amonra/.config/bashtop/bashtop.cfg" pid=28385 comm="bash" requested_mask="ac" denied_mask="ac" fsuid=1000 ouid=1000

```

What do I need to do to allow it to run without being denied all sorts of access.

David

---

### Post by deadflowr on 2020-09-21
Did you see the recommendations to run in snap info bashtop?
```
**Once installed, run the following commands so the snap will function as
  intended:**
  
  `sudo snap connect bashtop:mount-observe`
  
  `sudo snap connect bashtop:network-control`
  
  `sudo snap connect bashtop:hardware-observe`
  
  `sudo snap connect bashtop:system-observe`
  
  `sudo snap connect bashtop:process-control`
  
  
  _Make changes to the configuration and add themes:_
  
  `~/snap/bashtop/current/.config/bashtop`
  

```

from
```
snap info bashtop
```

---

### Post by David_Partridge on 2020-09-21
Thanks for the reply.   I don't believe it told me to do that when I did the install. I did the snap connect commands you listed, but then:

```
amonra@Charon:~$ /snap/bashtop/current/.config/bashtop
bash: /snap/bashtop/current/.config/bashtop: No such file or directory
amonra@Charon:~$ ll /snap/bashtop/current
```

I'm sure that command as listed makes no sense which is why I got a complaint.  What SHOULD it read?

```
amonra@Charon:~$ ll /snap/bashtop/current
lrwxrwxrwx 1 root root 1K Sep 20 15:44 /snap/bashtop/current -> 134/
amonra@Charon:~$ ll /snap/bashtop/134
total 0K
drwxr-xr-x  2 root root 1K Sep  1 22:58 bin/
drwxr-xr-x 22 root root 1K Sep  1 22:58 etc/
drwxr-xr-x  4 root root 1K Sep  1 22:58 lib/
drwxr-xr-x  2 root root 1K Sep  1 22:59 meta/
drwxr-xr-x  3 root root 1K Sep  1 22:59 snap/
drwxr-xr-x  7 root root 1K Sep  1 22:58 usr/
drwxr-xr-x  4 root root 1K Sep  1 22:58 var/
amonra@Charon:~$ 
```

I still get loads of errors:

```

amonra@Charon:~$ bashtop
mkdir: cannot create directory '/home/amonra/.config/bashtop/themes': Permission denied
mkdir: cannot create directory '/home/amonra/.config/bashtop/user_themes': Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 4737: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 923: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 698: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 701: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 709: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 5278: /home/amonra/.config/bashtop/error.log: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 651: /home/amonra/.config/bashtop/error.log: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 5270: /home/amonra/.config/bashtop/error.log: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 651: /home/amonra/.config/bashtop/error.log: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 709: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 651: /home/amonra/.config/bashtop/error.log: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 651: /home/amonra/.config/bashtop/error.log: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 651: /home/amonra/.config/bashtop/error.log: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 721: /home/amonra/.config/bashtop/bashtop.cfg: Permission denied
/snap/bashtop/134/usr/local/bin/bashtop: line 651: /home/amonra/.config/bashtop/error.log: Permission denied
amonra@Charon:~$ ls -l .config/bashtop
total 0K
-rw-rw-r-- 1 amonra amonra 0K Sep 20 16:03 bashtop.cfg
amonra@Charon:~$
```

David

---

### Post by deadflowr on 2020-09-21
I'd try removing it and the snap/bashtop directory in home and try starting over.
Also is there anything special about home or your file system layouts, like over NFS or something else?
As things like those can factor in.

---

### Post by David_Partridge on 2020-09-21
I removed it using snap remove and installed using apt-get after adding its repository.  That worked perfectly.

D.

---

