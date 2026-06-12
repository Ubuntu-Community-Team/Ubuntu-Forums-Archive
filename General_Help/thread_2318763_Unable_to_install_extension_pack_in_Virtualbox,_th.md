---
title: "Unable to install extension pack in Virtualbox, thus no USB access in guest"
date: 2016-03-29
forum: General Help
---

### Post by Akshay_Jain on 2016-03-29
I had been using VirtualBox for last two months, and do not know much in detail. I somehow installed it in Ubuntu 14.04 LTS. 
I installed Winodws7 in the Virtual box.

Now I required to use the USB ports, so was trying to install the extension pack.
While extension packs installation I was getting following error

```
failed to load the main module ('/usr/lib/virtualbox/extensionpacks/oracle_vm_virtualbox_extension_pack/linux.amd64/vboxpuelmain.so')
 verr_file_not_found - /usr/lib/virtualbox/extensionpacks/oracle_vm_virtualbox_extension_pack/linux.amd64/vboxpuelmain.so undefined symbol rtlogrelgetdefaultinstanceex
```

I googled it, and found, it had something to do with root permissions.
So, I checked that /usr/lib/virtualbox was set to root permissions, and thus I was not able to install the extension pack.

Then I did a blunder by doing the following:
```
chown -R akki /usr/lib/virtualbox/
```

Now, when I open the virtualbox it shows me the following error.
```
Effective UID is not root (euid=1001 egid=1001 uid=1001 gid=1001) (rc=-10)
Please try reinstalling VirtualBox.

where: SUPR3HardenedMain
what:  2
VERR_PERMISSION_DENIED (-10) - Permission denied.

```

I was looking for a way to solve the problem. I came across a solution and did the following, 
```
chmod 4711 /usr/lib/virtualbox/Virtualbox
```
It worked. Now I am able to open VirtualBox with Windows7 in it.
But, still I am not able to install the extension pack. I need to connect my ATLYS board with the Windows7 for my project.
PLEASE HELP. :(

---

### Post by SeijiSensei on 2016-03-29
A "undefined symbol" error like you report usually means there's some mismatch between a program and the libraries which it uses.  Make sure you have downloaded the version of the extension pack that matches your VirtualBox version.

Since you say you "somehow" installed VB, I'm guessing you're using the version from the Ubuntu repositories. I recommend you follow the instructions on the Oracle site to add its repository to your system and download everything from there.  Read this: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).

That said, even with the extension pack USB support can be flaky.  I recently failed to get a Win7 VM running on top of Kubuntu 14.04 to see a USB-connected scanner that doesn't work with Linux but does work with Windows.

---

### Post by HermanAB on 2016-03-29
Worse.  USB access is only available in the Virtualbox version downloaded from the Oracle web site.  The version that ships with Ubuntu doesn't do USB.  So you got to uninstall it, then download from Oracle and re-install.  Then it will all work.

---

