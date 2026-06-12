---
title: "How to install tpm tools on Ubuntu 17.10?"
date: 2017-12-16
forum: General Help
---

### Post by ULAMSS5 on 2017-12-16
On a Dell XPS 13 9350, received software updates that require a restart.

During the restart, there's something about being unable to update TPM because it's owned.

I can't boot back into Windows, and none of the restoration tools work. I think the failed update might be to blame.

For now, I can only boot into Ubuntu 17.10, the only talk about clearing TPM is with a tpm_tool, which seems to be on ver 1.3.8, here [https://packages.ubuntu.com/trusty/admin/tpm-tools](https://packages.ubuntu.com/trusty/admin/tpm-tools)

The Readme file says: 

 BUILDING tpm-tools
 -------- ---------
 $ sh ./bootstrap.sh
 $ ./configure
 $ make
 # make install

but on entering the first line in terminal (including "Open terminal here"), I get "sh: 0: Can't open ./bootstrap.sh"

I'm pretty inexperienced with installation/execution on ubuntu, and have never touched building/compiling or anything like that before. How should I proceed with this? Or are there easier ways to clear TPM to allow the update?

---

### Post by Kirk Schnable on 2017-12-17
> **ULAMSS5 said:**
> but on entering the first line in terminal (including "Open terminal here"), I get "sh: 0: Can't open ./bootstrap.sh"

It sounds like the file doesn't exist.  "bootstrap.sh" should be some kind of script that they are having you run.  Make sure you're running that first command (sh ./bootstrap.sh) from within the folder where you downloaded the installation stuff.

When you first launch a terminal, it will generally be in your user's home folder.  You may need to change to the folder where you downloaded the files to (eg:  cd ~/Downloads/tpm-stuff).

---

### Post by Yellow Pasque on 2017-12-17
You may want to clear the TPM in BIOS/EFI as shown in screenshot: [http://www.dell.com/support/article/us/en/19/how12395/how-to-troubleshoot-and-resolve-common-issues-with-tpm-and-bitlocker?lang=en](http://www.dell.com/support/article/us/en/19/how12395/how-to-troubleshoot-and-resolve-common-issues-with-tpm-and-bitlocker?lang=en)

---

