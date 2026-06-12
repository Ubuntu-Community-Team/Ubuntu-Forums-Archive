---
title: "Latest &quot;Ubuntu Base&quot; package push won't install"
date: 2021-06-09
forum: General Help
---

### Post by stevecoh1 on 2021-06-09
grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) but 2.04-1ubuntu26.12 is to be installed
grub2-common: Depends: grub-common (= 2.04-1ubuntu26.12) but 2.04-1ubuntu26.12 is to be installed
              Depends: libc6 (>= 2.28) but 2.31-0ubuntu9.3 is to be installed
              Depends: libdevmapper1.02.1 (>= 2:1.02.36) but 2:1.02.167-1ubuntu1 is to be installed
              Depends: libefiboot1 (>= 37) but 37-2ubuntu2.2 is to be installed
              Depends: libefivar1 (>= 37) but 37-2ubuntu2.2 is to be installed
              Depends: liblzma5 (>= 5.1.1alpha+20120614) but 5.2.4-1ubuntu1 is to be installed

Current system is"

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal

$ uname -r
5.8.0-55-generic

What's the way around this?

---

### Post by ajgreeny on 2021-06-09
I don't understand what you are trying to do; what exactly are you attempting to install, and what is Ubuntu Base?

If what you show above is the output of an install command please run it again but this time show us everything, including that command.

---

### Post by QIII on 2021-06-09
Moved to General Help, as this is a request for support and not a chat subject.

Please note the tagline in the Chat forum: >  Hello <username>, this sub-forum is for chat, not support – hence the name. If you need technical help, please post in an appropriate support sub-forum.

---

### Post by dddman on 2021-06-09
I find it confusing

[https://wiki.ubuntu.com/Base](https://wiki.ubuntu.com/Base)

[https://wiki.ubuntu.com/Minimal](https://wiki.ubuntu.com/Minimal)

---

### Post by ajgreeny on 2021-06-09
> **dddman said:**
> I find it confusing

[https://wiki.ubuntu.com/Base](https://wiki.ubuntu.com/Base)

[https://wiki.ubuntu.com/Minimal](https://wiki.ubuntu.com/Minimal)

Interesting!

I have come across the Minimal system but not Ubuntu-Base so I can't add any more to this query.

---

### Post by stevecoh1 on 2021-06-09
"Ubuntu Base" is the name of one of the automatic updates that pop up under Ubuntu 20.04 when Ubuntu pushes them out.  There, OS updates are packaged and referred to as "Ubuntu Base".  I'm just trying to install the updates that they pushed to me. Not sure why they would push updates that cannot be installed.  Still, I have pasted the error messages that occurred.  Maybe someone can tell me what's wrong.

---

### Post by dddman on 2021-06-09
LoL
[https://askubuntu.com/a/895521](https://askubuntu.com/a/895521)

---

### Post by grahammechanical on 2021-06-09
It seems to me that the messages are nonsense. They say that to install a package it needs to have a dependency installed that is equal to ( = ) in one case. And greater than or equal to ( >= ) in all the other cases. As far as I can see these conditions are being met.

I am guessing that there is a need (security?) to upgrade grub-efi-amd64-signed and its installation is causing a cascade of dependences. Packages that do not need to be upgraded are going to be upgraded in order for grub-efi-amd64-signed to be upgraded. I guess the user needs to be informed in these situations. Call it "Informed Consent."

I seem to remember reading something about a security flaw on UEFI systems that required a fix to grub-efi. It did not apply to BIOS systems. I cannot find where I read it.

Regards

---

