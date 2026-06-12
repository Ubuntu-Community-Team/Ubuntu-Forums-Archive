---
title: "How can I change the icon of an application installed via APT?"
date: 2024-04-27
forum: General Help
---

### Post by densitysam on 2024-04-27
Hi, I'm on Ubuntu 24.04 LTS and I've installed comic book reader MComix via APT. 

Everything is working fine, however the default icon appears a little blurred in the dash and it's bugging me. 

How do I go about fixing/changing the icon? I've already downloaded a cleaner and sharper icon to use in case there is no way to fix the default icon.

Thanks!

---

### Post by ajgreeny on 2024-04-27
Edit the MComix .desktop file, probably in /usr/share/applications and replace the pathway in the line pointing to the current icon with the full pathway to your new icon file. 
You may need to reboot for it to take effect but I can't remember.

---

### Post by densitysam on 2024-04-28
Thank you very much, it works perfect! :D 
And I didn't have to reboot either, the icon in my dash automatically updated when I saved the .desktop file. 
Thanks for your help!

---

### Post by Tadaen_Sylvermane on 2024-04-28
Better method is copy the .desktop file from /usr/share/applications to /usr/local/share/applications and edit this one. This will override the default one without worrying about it getting replaced in a package upgrade and you having to fix it again later.

---

