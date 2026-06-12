---
title: "Mounting Hidden Windows Folders Error"
date: 2007-12-24
forum: General Help
---

### Post by plap on 2007-12-24
Hi, when I try to mount a hidden windows folder, the console is okay, but when I try navigate to the folder I get "Access was denied" and "Couldn't display foldername"

I tried mounting as sudo and I tried adding my windows username & password at the end of the line, but neither works. 

I also tried mount -t smbfs, and in console I got "mount: only root can do that", then I tried adding sudo at the beginning and the console just displays the mount syntax

---

### Post by dlegend on 2007-12-24
Try typing in "su root" in the terminal and enter your password. Then try running the mount -t smbfs command.

---

### Post by plap on 2007-12-24
su: Authentication failure

that's strange..

---

### Post by dlegend on 2007-12-24
> **plap said:**
> su: Authentication failure

that's strange..

Did you enter the root password rather then your regular user account? The root password can be set by going to Administration > Users and Groups. Click on "root" and click properties and set password by hand under the default tab then try again.

---

### Post by plap on 2007-12-24
ah okay, i configured the root password and tried the command again but the same error occurs. also, every time the error occurs it deletes the mount point folders and i can't rename folders to those names

---

### Post by ~LoKe on 2007-12-24
Oh God don't set a root password.

sudo su

---

### Post by plap on 2007-12-25
okay, same error with sudo su...

---

