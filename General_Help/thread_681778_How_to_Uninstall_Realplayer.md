---
title: "How to Uninstall Realplayer"
date: 2008-01-29
forum: General Help
---

### Post by mapes12 on 2008-01-29
Hi

I followed the instructions from this link:

[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods]("https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods")

and followed the step 2 instructions to "Install RealPlayer for Linux from the RealNetworks web site" using the RealPlayer10GOLD.bin binary file.

During the install I was asked:

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]:

I repsonded "Y" but don't know what I've done?

So, I want to uninstall everything that the install process went through and roll back to where I was before just in case my system has been corrupted.

BTW there is now an icon in Applications / Sound & Vision for Realplayer but it doesn't work. I get an Error window pop up which says "Failed to execute child process "realplay" (No such file or directory)"

There is also now a folder on my Desktop with a padlock on it. The folder is called "Realplayer" and has the Realplayer files in it.

I could just send it to the trash can but I'm sure that wouldn't remove the application properly.

Can anyone help me out please?

Mark

---

### Post by zvacet on 2008-01-29
Try to find it in synaptic and mark for complete removal.

---

### Post by mapes12 on 2008-01-29
I tried that but it is not listed. I suspect that it is not listed because I installed it from a native binary file and not a deb package file.

My main concern is getting rid of any "symbolic links " I may have created.

I also need to get rid off the non functioning Realplayer icon in Applications / Sound & Video.

Thanks in advance to anyone who can help out on this.

Mark

---

### Post by zvacet on 2008-01-30
Look in that folder you have on Desktop.Search for **install** or** read me** files.Maybe there are instructions for uninstalling.

---

### Post by apienk01 on 2008-04-21
Sorry to bump an old thread, but here's a simple solution to completely uninstall RealPlayer installed with the BIN file (Real Installer). Someone might still want to use it.

First, download the RealPlayer for Linux installer (the BIN file) from [the Real Networks website]("http://www.real.com/linux"). Then give the file execution rights:

```
chmod +x RealPlayer11GOLD.bin
```

and re-install RealPlayer as root, or as user, depending on what you did before. This one's for root:

```
sudo ./RealPlayer11GOLD.bin
```

After installation you should be left with a folder named **hxsetup**. For me it is in *~/Desktop*. Inside *hxsetup/postinst* you'll find installation scripts, as well as some uninstall scripts. Now, there's no way to call these scripts from within the installer - it just doesn't have a *--uninstall* option - but you can run them manually. Luckily, there's one script that calls them all. To execute:

```
cd hxsetup/postinst
sudo ./postuninst.sh
```

The script will remove all the RealPlayer system integration: Gnome entries, mime types, file links, icon definitions (yes, icons 'get ubuntu' again), browser plugin, etc. It will not, however, remove any files. So the last step is needed:

```
sudo rm -R /opt/real
```

And to get rid of the padlocked folder on Desktop, you obviously have to remove it as root:

```
sudo rm ~/Desktop/hxsetup
```

Welcome to your RealPlayer-free Ubuntu!

---

### Post by nickzeff on 2008-05-17
Thank you!

I felt dirty with that thing on my machine...!

---

