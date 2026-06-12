---
title: "Zfs tpm2"
date: 2022-04-23
forum: General Help
---

### Post by conromia on 2022-04-23
Hey,

I was after some help to setup my TPM2 chip to auto unlock my ZFS root directory automatically on boot?
I've done some light googling and can't seem to find anything straight forward for Ubuntu and ZFS.

Does anyone know how to do this?
I have a key file (Created during installation) and a password

---

### Post by challdns on 2022-04-23
What version of ubuntu are you running, if it's 22.04 you're better off waiting until they compile systemd with TPM2 functionality turned on and using the systemd native stuff

If its an older version, your only option is clevis

---

### Post by conromia on 2022-04-24
Yea running 22.04, i wasn't aware TPM2 functionality was being worked on. That's good news i suppose. Unless it requires a reinstall of Ubuntu :cry:

Thanks for your reply.

---

### Post by challdns on 2022-04-24
The functionality is already there but off. It's just that canonical or whoever is compiling their systemd is doing so without the TPM2 flag, and it would be trivial to fix

It works on systemd version 248.3 or higher, and Ubuntu 2204 ships with systemd 249

I've tested this working on multiple other distros with systemd 249, it's just something the people who do package management need to fix for ubuntu

systemd-cryptenroll --tpm2-device=list

Should list the tpm devices but instead aystemd replies tpm2 support not enabled for this build.

> find a systemd version that enables this feature or compile it yourself with the option "-Dtpm2=true"

---

### Post by #&amp;thj^% on 2022-04-24
Bug: [https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg6018790.html](https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg6018790.html)

---

