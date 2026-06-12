---
title: "Can I Permanently Skip an Update Item?"
date: 2007-01-22
forum: General Help
---

### Post by vgrisham on 2007-01-22
Is there a way to permanently skip an item that Synaptic is trying to update? I don't want to upgrade my python wpxwidgets version (I have 6 and it's trying to go to 8) because PodNova won't function with 8. Alternatively, if I do install version 8, will it replace version 6 or simply add to it?

---

### Post by FyreBrand on 2007-01-22
Yes I believe you can "hold" that package at a version.  How you tell apt to hold the package depends on how you get updates.  I don't use Synaptic, but I believe it's in a menu item.  If you use aptitude or apt-get then you can use a switch and hold the package version.

When I can get back to the terminal I will look it up for you in the man pages.

---

### Post by vgrisham on 2007-01-22
> **FyreBrand said:**
> Yes I believe you can "hold" that package at a version.  How you tell apt to hold the package depends on how you get updates.  I don't use Synaptic, but I believe it's in a menu item.  If you use aptitude or apt-get then you can use a switch and hold the package version.

When I can get back to the terminal I will look it up for you in the man pages.

Cool. Thanks a ton. I'll look forward to your response. 

FWIW, I get my updates from the little asterisk that pops up in the system tray.

And while we're at it, is there a way to undo an update if something goes amiss?

---

### Post by FyreBrand on 2007-01-22
Like I said I normally use the konsole to update so I will try and be as helpful as I can, but I might not be able to tell you exactly where/how to do this using the Synaptic graphic tool.

First I would recommend installing the apt-howto file.  It's just good reading and explains about apt which is Debians package management tool.  It's a front end for dpkg.  I honestly don't know if Synaptic uses apt or dpkg directly.  The apt-howto file is nothing more than an html text file with hypertext links to various apt functions.

You would install it from the command line by:
```
sudo aptitude update && sudo aptitude install apt-howto
```
Then at the terminal type:
```
apt-howto
```
And it will start your default browser and open the apt-howto file.

Here is what that file says about holding packages:
[quote=apt-howto]**4.9 Keeping packages on hold**
 As we saw on the previous section, aptitude will automatically mark packages for upgrade. If you want to keep the current version installed, though, you can ask it to put the package on hold. 
 This is achieved by pressing the "=" key. Packages being held from upgrades will look like this: 
     ```
ih    alien                                                 8.41      8.41
```

 In this example, the alien package will be kept at version 8.41 even if a new version appears on an APT source -- notice the h character at the left. To have it upgraded/upgradable again just mark it for installation. 
 You can put packages on hold using the command line interface, too, by running: 
     ```
# aptitude hold package1 package2 ...
```[/quote]

I don't have Synaptic installed and I don't use Adept.  I do believe there might be a way to hold packages when you select a package for install, removal, complete removal, and such.  Sorry I can't help you with that part.  Hopefully a gnome user will be able to help you out with the graphical part.

---

### Post by vgrisham on 2007-01-27
Thanks FB; I appreciate your help. I'll give it a try.

---

### Post by CowzRule on 2007-01-27
In Synaptic, find the package you don't want updated. Click on it to highlight it, then on the top menu click "Package" then select "Lock Version".

---

