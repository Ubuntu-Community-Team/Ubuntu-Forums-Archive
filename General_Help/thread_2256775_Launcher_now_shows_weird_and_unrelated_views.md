---
title: "Launcher now shows weird and unrelated views"
date: 2014-12-14
forum: General Help
---

### Post by Gnusboy on 2014-12-14
Hi

What happened to launcher?
 For the past 2 days when I open the launcher I get all kinds of programs, apps, and random games & garbage. It used to open showing the installed extensions, plug-ins and available add ons.
I'm supposedly using the latest version of Firefox 34.0 for Ubuntu, but the last couple of days I keep getting notices that my current version is out of date and that I need to update Firefox.
Ok. So I go to the launcher and using the search bar cannot find the Flash Player that I am supposed to install. 
What shows up are a bunch of things under different categories labeled as "Reference, Info, Suggestions and Weather. On a column to the right side of the screen is a 
huge assortment of different categories with different programs. This is new. I have never seen this before. 
And I still can't find the correct version of Firefox. How do I fix this? 



[ATTACH=CONFIG]258579[/ATTACH]

P.S. I have an RPM version of the Flash Player that I downloaded and  do  not know how to install it. I've tried many times, but it doesn't seem  to work for me.

Thanks.

---

### Post by buzzingrobot on 2014-12-14
The image shows the standard Dash view of your system's contents in Unity. You've filtered the display by searching on the word "flash'.  Don't try to fix it. It's what you should see.

The current Firefox version is shown within Firefox at Help->About_Firefox.

It's unclear if Flash is installed or not. (You won't see it in the Dash if it is not installed.)  If it is installed and Firefox is displaying notices that Flash is outdated, then -- assuming you originally installed Flash via the package in the Ubuntu repos -- all you need to do is run the usual routine update procedure and Flash will be updated, along with anything else that needs updating.

If you originally installed Flash from somewhere other than the Ubuntu repos, then Ubuntu's updating software won't be aware that Flash has been installed and won't update it.  

Installing the "flashplugin-installer" package from the repos is the correct approach. Or, you can install "ubuntu-restricted-extras", which installs Flash plus some codecs, Microsoft fonts, etc.

After Flash is installed, quit Firefox and relaunch it, and check in Tools->Addons->Plugins to verify the browser is using the plugin.

RPM files are similar to Ubuntu and Debian .deb files:  They are used to install software on RPM-based systems like Red Hat, Fedora, and Opensuse.  They cannot be installed on Ubuntu, although the files in them can be extracted. (Again, you *don't* want to extract the Flash files from the RPM and try to install them because, even if you manage to do that correctly, the updater software won't know Flash is on the system and won't update Flash when Canonical packages and pushes out Flash updates released by Adobe, which happens frequently.)

---

### Post by Gnusboy on 2014-12-14
Oh wow! Thank you.
You have been extremely helpful.I appreciate it.
I tend not to do things on Ubuntu if I don't need them for my tasks.
.

---

