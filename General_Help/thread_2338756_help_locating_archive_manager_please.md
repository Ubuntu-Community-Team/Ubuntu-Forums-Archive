---
title: "help locating archive manager please ?"
date: 2016-10-01
forum: General Help
---

### Post by memaggi on 2016-10-01
i recently disabled my flash , now i have down;loaded newer supported version and saved it to my archive manger???? but i dont know how to find it and open or run it ???what am i doing wrong , im a complete computer novice btw lol , thanks

---

### Post by oldos2er on 2016-10-01
On Ubuntu and Linux in general, one installs programs by using their distro's package manager, not downloading them from websites.

Please tell us which Ubuntu version you're running, why you disabled flash, and why not simply re-enable it? Does "disabled" mean you uninstalled it?

Edit: According to [https://ubuntuforums.org/showthread.php?t=2338754](https://ubuntuforums.org/showthread.php?t=2338754) you disabled flash. Just reverse the steps you took to re-enable it.

---

### Post by memaggi on 2016-10-01
12.04 LTS 32 bit 

old flashplayer had problems

---

### Post by oldos2er on 2016-10-01
```
sudo apt-get install flashplugin-installer --reinstall
```

---

### Post by memaggi on 2016-10-01
i have located archive manager but i still dont know how to run the new stuff ive downloaded i.e new flash and new firefox browser ??? my choices seem to be open or extract but all i get when i click on them are loads of obsure files ? do i need to remove old versions before i can have the option to prceed with launching and running updated versions ?

---

### Post by colmax on 2016-10-01
Suggest opening Firefox browser and see if u can add Flash through add-ons / plug-ins

---

### Post by oldos2er on 2016-10-01
What's the full name of the flash archive you downloaded? I can't assure you it would work on 12.04, which is why I haven't mentioned it.

Firefox can be extracted into a folder inside your home folder; you then double-click the file called "firefox" within it.

---

### Post by memaggi on 2016-10-01
thankyou yes thats right but i wanted to install newer version ??should i re install what i disabled and update ? im sure when i done that in the past nothing seems to change :(

where do i type that into please ?

[h=1][     Add-ons ]("https://addons.mozilla.org/en-GB/firefox/")[/h]                       
[LIST]
[*]     [Extensions]("https://addons.mozilla.org/en-GB/firefox/extensions/")
[*]       [Themes]("https://addons.mozilla.org/en-GB/firefox/themes/")
[*]             [Collections]("https://addons.mozilla.org/en-GB/firefox/collections/")
[*]       [More…]("https://addons.mozilla.org/en-GB/firefox/blocked/p796#")
[/LIST]
                                                                                                                                                                               [h=1]**Flash Player Plugin on Linux 11.2.202.424 and lower (click-to-play)** has been blocked for your protection.[/h]   Why was it blocked?Old versions of the Flash Player plugin have known vulnerabilities (CVE-2014-9163). All users are strongly recommended to [update their Flash plugin]("https://get.adobe.com/flashplayer/").Who is affected?All users who have these versions of the plugin installed in Firefox.What does this mean?           The problematic add-on or plugin will be automatically disabled and no longer usable.
          When Mozilla becomes aware of add-ons, plugins, or other third-party  software that seriously compromises Firefox security, stability, or  performance and meets [certain criteria]("http://wiki.mozilla.org/Blocklisting"), the software may be blocked from general use.  For more information, please read [this support article]("http://support.mozilla.org/kb/add-ons-cause-issues-are-on-blocklist").       Blocked on December 11, 2014. [View block request]("https://bugzilla.mozilla.org/show_bug.cgi?id=1109795").

i have now reinstalled the original flash but trying to update it seems impossible

---

### Post by deadflowr on 2016-10-01
What flash is installed?
(current flash version for linux is 11.2.202.635)

Note that disabling the plugin in firefox, only disables the plugin in firefox.
You still have the flash package installed on the system.

---

### Post by oldos2er on 2016-10-01
Did you read those warnings? Please install flash using the command I gave you in post #4, or use ```
sudo apt-get update

sudo apt-get install flashplugin-downloader
``` to get the correct version of flash with the latest security fixes.

---

### Post by deadflowr on 2016-10-01
> **memaggi said:**
> i have now reinstalled the original flash but trying to update it seems impossible

Seems we posted at the same time.

How flash updates on Ubuntu is that when you install either the adobe-flashplugin package (You need to enable the Canonical Partners repository to get that version) 
or the flashplugin-installer package is that first Ubuntu updates a script and then the script runs and downloads the latest flash package directly from adobe.
The actual download from adobe's website can vary in speed, compared to downloading updates from the Ubuntu repos.
Running a system update automatically pulls in the latest flash version. (for linux)

---

