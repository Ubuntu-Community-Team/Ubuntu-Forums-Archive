---
title: "How to Update Browsers in Linux without Downloading a New FILE?"
date: 2016-02-02
forum: General Help
---

### Post by kkk5 on 2016-02-02
I tried to update my browsers in Firefox and Chrome, but I still get these messages (check attached photos).

How can I update them in **Terminal** without downloading a file from their websites, and install them manually?

---

### Post by deadflowr on 2016-02-02
Huh?
Just run an update through Ubuntu's software updater.
Both Firefox and Chrome use Ubuntu's update system.
It's one stop shopping.

But probably more to the point is,
"Where did you get flash player 8?"

---

### Post by mastablasta on 2016-02-02
flash player should be installed from software center (restricted extras package). it is stuck at ver. 11 or something like that.

---

### Post by buzzingrobot on 2016-02-02
Those popups exhorting you to install or update Flash are intended for Windows, not Linux. Yes, you can do a manual install of Flash that way. No, the packaging tools won't be aware of it, which leaves you to update it manually (and to *know*) when to update it.

The appropriate way to install Flash on Ubuntu is from the Ubuntu repos.  It's in the "flashplugin-installer" package.  It's also included in the "ubuntu-restricted-extras" package. Canonical is excellent at packaging and delivering Flash update very soon after Adobe releases them.  If you've installed Flash manually, remove it first.

Adobe stopped adding new features to Flash for Linux a few years ago.  Since then, updates have consisted of security patches.

Meanwhile, Google did a deal with Adobe to deliver a separate version of Flash for use with Chrome.  This version of Flash sees both feature and security updates.  it may be useful on sites designed for the latest version of Flash for Windows. If you install Chrome, it is installed automatically.  It's also available, as "pepperflash", for Chromium.

---

### Post by ajgreeny on 2016-02-02
You need to understand that Ubuntu and all other Linux distros, ie, operating systems, do not work the same way as Windows (I'm assuming that is your major OS experience) and you do not update applications in the windows way.

Make sure you run the update-manager application regularly and everything will be done for you.  Normally it runs automatically for you either daily or weekly; I can't remember which.

There is no need to go searching for applications on the developer's web site, and if you do, you may find that it is not easy to install it, and it may not run anyway, as some dependency packages may not be available in the version needed for your version of Ubuntu.

PS: What numerical version of Ubuntu are you using and which flavour; ie Ubuntu, Xubuntu, Lubuntu. etc etc.

---

### Post by Dennis N on 2016-02-02
Check your flash player version here to see if yours is current:

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

You may sometimes show one release behind, as packaging and distribution takes a few days through the repositories. Be sure you have installed an appropriate package to provide the flash player updates. 

_Firefox_:
flashplugin-installer or adobe-flashplugin

_Chrome_:
Automatically updates itself through the source set up by Chrome during install.

_Chromium_:
adobe-flashplugin

The **adobe-flashplugin** package will update the flash player in both Firefox and Chromium browsers. To install it, you need to enable "Canonical Partners" in Settings > Software Sources > Other Software > checkbox for "Canonical Partners". Then, update your sources to make it available for installation. In Ubuntu Software Center, put "adobe-flashplugin" into the search box to locate it (one match appears in results).

---

