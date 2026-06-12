---
title: "seahorse unable to encrypt folder"
date: 2012-12-28
forum: General Help
---

### Post by jmlynn on 2012-12-28
Hi,

I had installed seahorse from s/w centre and was able o encrypt/decrypt file one at a time after reboot.  However, nothing happens when I select a folder to encrypt, fully expecting a pop-up windows to ask for multiple file encryption option right after the pgp key selection.

Any idea what need to be done to make it works?  I am running the latest Ubuntu 12.04.1 LTS with latest patches.

Thanks for any info regarding this.

Jeff

---

### Post by haqking on 2012-12-28
> **jmlynn said:**
> Hi,

I had installed seahorse from s/w centre and was able o encrypt/decrypt file one at a time after reboot.  However, nothing happens when I select a folder to encrypt, fully expecting a pop-up windows to ask for multiple file encryption option right after the pgp key selection.

Any idea what need to be done to make it works?  I am running the latest Ubuntu 12.04.1 LTS with latest patches.

Thanks for any info regarding this.

Jeff

do you have the plugins installed ?

```
sudo apt-get install seahorse-plugins
```You may need to stop and start nautilus afterwards or logout and backin

---

### Post by jmlynn on 2012-12-28
Yes I did, at least I believe so, as I was able to encrypt/decrypt individual file form desktop file manager.  I even reboot Ubuntu but still the same, nothing happen for folder encryption.

Jeff

---

### Post by haqking on 2012-12-28
> **jmlynn said:**
> Yes I did, at least I believe so, as I was able to encrypt/decrypt individual file form desktop file manager.  I even reboot Ubuntu but still the same, nothing happen for folder encryption.

Jeff

So the encrypt option is not there when you right click on the folder or it is there but nothing happens when you choose it ?

---

### Post by haqking on 2012-12-28
I remember seeing a bug similar to this a while ago but cant find it now.

I think the solution was to create a tarball for the folder first as a workaround ?

I will post back if i find it

---

### Post by jmlynn on 2012-12-28
Encrypt is there, as I can encrypt/decrypt a single selected file.  But when the same encrypt action is selected on a selected folder, it asks for encryption key (PGP) and pass phrase, then nothing happens when I click the ok button.  As seem from Seahorse web site, I should get a pop-up windows asking to chose multi-file encryption or not kind of option.  But none happens.

Tarball is not the option I want, as I would like to backup my files on cloud storage and I want very much these files are encrypted individually.  The current work around will be to encrypt each file one by one.  I would very much like to encrypt/decrypt the whole directory instead

---

