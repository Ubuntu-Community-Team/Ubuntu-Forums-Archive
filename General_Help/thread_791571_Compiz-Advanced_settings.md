---
title: "Compiz-Advanced settings"
date: 2008-05-12
forum: General Help
---

### Post by haran_hockey on 2008-05-12
I have ubuntu 8.04 and installed it with wubi- so I don't have the cd. I also don't have internet on ubuntu but I do on my windows. So is there any way to download compiz(advanced desktop settings) on windows and then transfer it on my usb to ubuntu and install it there. By the way, i any of you know how to fix my internet problem, go here: [http://ubuntuforums.org/showthread.php?p=4925983#post4925983]("http://ubuntuforums.org/showthread.php?p=4925983#post4925983")

---

### Post by wadelewis4 on 2008-05-12
I offered a possible solution for you on your other thread - go check that out. 
Once you're connected: Compiz Advanced Settings manager is listed in the repos - just use Synaptic to install it.

---

### Post by haran_hockey on 2008-05-12
I'm still not connected so isn't there any other way to install it(download it off windows and bring it to ubuntu on usb) ???????

---

### Post by wadelewis4 on 2008-05-13
Go Here: [http://packages.ubuntu.com/hardy/all/compizconfig-settings-manager/download]("http://packages.ubuntu.com/hardy/all/compizconfig-settings-manager/download") and select a mirror to download the deb package. Save it to a usb drive and bring it to your PC. Right click it and install.

---

### Post by haran_hockey on 2008-05-13
I get an error:

Error: Dependency is not satisfied: python-compizconfig

I think this is because I am using ubuntu 8.04 and the file is 7.4

Any links for 8.04?

Or is it because I don't have synaptic or aptitude. If I do need to use one of these, can someone explain how.

---

### Post by wadelewis4 on 2008-05-14
> **haran_hockey said:**
> 
Or is it because I don't have synaptic or aptitude.

Everyone who installs Ubuntu has aptitude & synaptic is installed by default in System > Administration > Synaptic. But you need internet access to utilize it. 

It would be best for you to use Synaptic to install that package to satisfy the dependencies. If you have a cat5 network cable, connect it between your computer and the wireless router to get a wired internet connection - that way you can take care of all of the installations you need and also begin using your wireless adapter.

---

### Post by ago on 2008-05-14
If you have no internet, for each deb package you need to install you also need the full tree of dependencies. It is much more convenient to use a connected system, so all dependencies are taken care of for you...

---

### Post by Malac on 2008-05-14
[http://archive.ubuntu.com/ubuntu/pool](http://archive.ubuntu.com/ubuntu/pool)
Has all the packages that you want under headings:
hardy, hardy backports, hardy-security, hardy-proposed and hardy-updates.
You can use google to search a specific site for any .deb file you want using the [Advanced Search] button to the right of the search box.
 
Or just browse the repo getting each one in Windows and copy it to your Ubuntu install, double click on it if you have gdebi it should install.

---

### Post by haran_hockey on 2008-05-14
What do I download if all I want is to have the ubuntu Advanced desktop settings.(so i want all the cool special effects and stuff)

---

### Post by ago on 2008-05-15
This should be on the general forum, since it is not strictly a Wubi question.

---

