---
title: "rpm to deb"
date: 2005-09-29
forum: General Help
---

### Post by jdg on 2005-09-29
i'm having problems converting limewirelinux.rpm to deb i already tried "sudo alien limewirelinux.rpm" command but i get the error "File "limewirelinux.rpm" not found."

---

### Post by mcmuffy on 2005-09-29
You missed the -d 'sudo alien -d filename.rpm', though -d is the default so it may not be needed but I never tried without it.
Also 2 silly questions :
1.Are you working in the same directory as the file you are trying to convert?
2.Are you sure you typed in the filename correctly? Linux is case sensitive so limewire and Limewire would be different files.

---

### Post by aysiu on 2005-09-29
Have you seen this?

[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

---

### Post by jdg on 2005-09-29
[QUOTE=aysiu]Have you seen this?
[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)[/QUOTE]

no i haven't. thanks!

---

### Post by Perfect Storm on 2005-09-30
[QUOTE=jdg]i'm having problems converting limewirelinux.rpm to deb i already tried "sudo alien limewirelinux.rpm" command but i get the error "File "limewirelinux.rpm" not found."[/QUOTE]

Looks like you execute the command in the wrong directory.

> You missed the -d 'sudo alien -d filename.rpm', though -d is the default so it may not be needed but I never tried without it.
-d is not nesessary sudo alien filename.rpm is sufficient.

---

### Post by mumushi on 2005-09-30
[QUOTE]root@gccservice:/home/gccservices/Desktop# ls
curly-002a764a55.desktop  Gyach Enhanced            LimeWireLinux.rpm
Distros                   larry-00b8a84599.desktop  moe-0028c0ccb8.desktop
root@gccservice:/home/gccservices/Desktop# sudo alien LimeWireLinux.rpm
sudo: alien: command not found
root@gccservice:/home/gccservices/Desktop#[QUOTE]

this is what i got when i tried alien command in the terminal im in the right directory where the rpm file is but it doesn't work. What seems to be wrong? 

Any help would be gretly appreciated. Thanks!

:D Please be patient with me :D

---

### Post by heimo on 2005-09-30
[quote=mumushi]
this is what i got when i tried alien command in the terminal im in the right directory where the rpm file is but it doesn't work. What seems to be wrong? 
  [/quote] 
You don't have alien installed. Use synaptic package manager or:
```
sudo apt-get install alien

```

---

### Post by jdg on 2005-09-30
what do you mean if i'm in the right directory?

---

### Post by mumushi on 2005-09-30
:D ok thanks heimo. i will be doing that.

---

