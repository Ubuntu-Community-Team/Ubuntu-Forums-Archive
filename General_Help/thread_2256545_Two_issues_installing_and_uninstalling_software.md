---
title: "Two issues: installing and uninstalling software"
date: 2014-12-13
forum: General Help
---

### Post by ron177 on 2014-12-13
I have an Ubuntu 14.04 installed on my Toshiba Laptop. I have two unusual problems:

1. I can't install Skype: because when I downloaded the Skype file, I can't then install the downloaded package. I extracted the .deb file but then I can't do much with the files and folders extracted. How can I install Skype? Any help, tips, or advice? 

2. I downloaded a software from the Software Centre. After a few days, then I removed the software since I didn't care much about that software. But the software doesn't go away. Even though the Software Centre tells me it is removed and un-installed, it still appears on my computer and opens up every time I turn on the computer. How can I completely uninstall this software? 

Thanks,

R

---

### Post by pfeiffep on 2014-12-13
> **ron177 said:**
> I have an Ubuntu 14.04 installed on my Toshiba Laptop. I have two unusual problems:

1. I can't install Skype: because when I downloaded the Skype file, I can't then install the downloaded package. I extracted the .deb file but then I can't do much with the files and folders extracted. How can I install Skype? Any help, tips, or advice? When I installed Skype I simply let the software center install after downloading

> 2. I downloaded a software from the Software Centre. After a few days, then I removed the software since I didn't care much about that software. But the software doesn't go away. Even though the Software Centre tells me it is removed and un-installed, it still appears on my computer and opens up every time I turn on the computer. How can I completely uninstall this software? 

Thanks,

R
If you have Synaptic package manager you should be able to mark the application for complete removal ... no Synaptic this command should remove the application
```
sudo apt-get purge [application name]
```

---

### Post by ron177 on 2014-12-13
How does your Software Centre pick up the downloaded Skype file? Can you tell me the steps you take to do that?

---

### Post by Impavidus on 2014-12-13
> **ron177 said:**
> I have an Ubuntu 14.04 installed on my Toshiba Laptop. I have two unusual problems:

1. I can't install Skype: because when I downloaded the Skype file, I can't then install the downloaded package. I extracted the .deb file but then I can't do much with the files and folders extracted. How can I install Skype? Any help, tips, or advice? Enable the Canonical Partner repositories in your software sources. Then skype should be available via the software centre. There is no need to manually download a .deb file.

> 2. I downloaded a software from the Software Centre. After a few days, then I removed the software since I didn't care much about that software. But the software doesn't go away. Even though the Software Centre tells me it is removed and un-installed, it still appears on my computer and opens up every time I turn on the computer. How can I completely uninstall this software? 

Thanks,

R
It may also not have been properly removed from the user config files. Somewhere in your user configuration may still be a reference to this program. It may also be that by uninstalling you only really removed a metapackage for this software. Autoremoving all its dependencies should get rid of the software.```
sudo apt-get autoremove
```

---

### Post by ron177 on 2014-12-31
Dear all,

I was able to install Skype very quickly. But removing this application has become a pain in the neck. The application in question is Cairo-Dock. I have tried both autoremove and the purge command given above. Neither worked on this thing. Once again: I have un-installed or removed Cairo-Dock through the Software Center but it continues to appear on my desktop. I have tried to see if I have Synaptic Package Manager, but couldn't find one. So at this point, I don't know what to do. Any suggestions? 

Thanks,

Ron

---

### Post by schragge on 2014-12-31
Please open a terminal window (see [uhelp]community/UsingTheTerminal[/uhelp] for how to), and type in the following command:
```
sudo apt-get purge ^cairo-dock
```

---

### Post by ron177 on 2014-12-31
Thanks a lot. This has effectively resolved the issue. Very many thanks.

---

