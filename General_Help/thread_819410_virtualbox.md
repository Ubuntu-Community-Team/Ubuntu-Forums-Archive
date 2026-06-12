---
title: "virtualbox"
date: 2008-06-05
forum: General Help
---

### Post by SpenceMakesSense on 2008-06-05
When I start virtual box I get the following error

```
spence@spence-desktop:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.
spence@spence-desktop:~$ sudo apt-get install virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtk-mozembed-ruby libgtk-mozembed-ruby1.8 libatk1-ruby1.8 ruby1.8
  libopengl-ruby1.8 ruby libxul0d libopengl-ruby libglib2-ruby1.8
  libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8 libmozjs0d libgtk2-ruby1.8
  libgtk2-ruby libxul-common libruby1.8 libgtkglext1 libpango1-ruby1.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

This happened after I upgraded the kernel.
Any help would be appreciated

---

### Post by destructchaos on 2008-06-05
virtualbox needs to recompile its kernel modules after every kernel update.  either wait for them to posted in the repos or unistall that version and get the installer from the virtualbox website and do it yourself.  personally, i use the non-free version because i need the usb 2.0 support and reinstall about once a week.  it takes about 10 seconds.

---

### Post by sdennie on 2008-06-05
You should also make sure you are running the -generic kernel.  Check the output of:

```

uname -a

```

---

### Post by mrMango on 2008-06-05
You may also want to forget the OSE and use the regular edition. You can download a .deb for it from the VirtualBox site. I used that and haven't had any problems.

---

### Post by pointone on 2008-06-05
Try:

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by SpenceMakesSense on 2008-06-05
Got it from the site, had to manually uninstall previous install to install 1.6, but none the less worked. Thanks!

---

