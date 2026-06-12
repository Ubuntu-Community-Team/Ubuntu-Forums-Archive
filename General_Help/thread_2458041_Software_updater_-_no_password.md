---
title: "Software updater - no password"
date: 2021-02-14
forum: General Help
---

### Post by 3dmatrix on 2021-02-14
I have noticed, since some days (may be weeks) my software updater in Lubuntu does not asks for password for installing updates.
Have I done any thing wrong ? How can I rectify the problem ?

---

### Post by Impavidus on 2021-02-15
The GUI software updater hasn't asked passwords for ages when only upgrading packages that are already installed. It does ask for your password when installing new packages or removing packages. Unless this is something specific for Lubuntu.

---

### Post by grahammechanical on 2021-02-15
With my install of Ubuntu 20.04 Software Updater will ask for authentication when a Linux kernel is to be upgraded. I do not see why Lubuntu should be any different as the Lubuntu developers rely on Ubuntu developers for Lubuntu's underlying kernel and operating system.

Regards

---

### Post by deadflowr on 2021-02-15
> **Impavidus said:**
> The GUI software updater hasn't asked passwords for ages when only upgrading packages that are already installed. It does ask for your password when installing new packages or removing packages. Unless this is something specific for Lubuntu.

Indeed, as far I remember it's a policykit rule where if the admin (or admin level) user is the one running the updater it will install updates to existing packages without the need for authentication.
(If the user accessing the updater is not an admin then it'll ask for a password.)

---

### Post by 3dmatrix on 2021-02-15
I do not know about admin or ordinary user. I have the just one login ID and password. 
With that earlier when I used to login and wanted to update, it used to ask for password which now it does not does.

---

### Post by ajgreeny on 2021-02-16
Interesting discussion!

I do not use a GUI application for updates and upgrades, using terminal commands (actually aliases to save time) with ***ud*** for "sudo apt update && apt list --upgradable" and ***ug*** for "sudo apt ful&#314;-upgrade" and my password is needed for that; always has been needed.

Presumably the use of terminal in this way in Lubuntu does still require a password? Just asking as I do not know the Lxqt version of Lubuntu and have not used earlier LXDE versions for a very long time.

---

### Post by Impavidus on 2021-02-16
Maybe there's some obscure setting to control this, but the default has been for years to only require a password for the GUI tool if you want to install new packages or remove some packages. Kernel upgrades always involve new packages and are the only upgrades that routinely do so, so effectively you have to enter your password whenever there's a kernel upgrade. Your current behaviour is the default, your old behaviour was not, so there appears nothing wrong now.

Kernel upgrades come about once every two weeks (not very regular), so if you only install upgrades every two weeks (the lowest setting in Software & Updates, unless you set it to never), chances are you get a kernel upgrade most of the time.

---

### Post by 3dmatrix on 2021-02-18
I will keep a watch on the new updates. 
Will check the content of the updates and if it asks for password.

---

