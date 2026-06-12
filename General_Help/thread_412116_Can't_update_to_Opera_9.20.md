---
title: "Can't update to Opera 9.20"
date: 2007-04-17
forum: General Help
---

### Post by Buzzygirl on 2007-04-17
Hi, I'm running Dapper 6.06 and using Opera 9.02 as my browser. There's a new version of Opera available, 9.20. I downloaded the .deb package and tried to run it, but when I do, I get a message, "Error: conflicts with the installed package 'opera'." Does this mean I have to uninstall the old version? Will my bookmarks still exist if I uninstall the old version?

Thanks!

---

### Post by Chappy7777 on 2007-04-17
Maybe this is the reason there is so little tallk on the Ubuntu forum about Opera. I was using Xandros for a little while and many XN users are using Opera as their preferred browser. I like Opera also, but Firefox is my fav.
I can't say about your error, or what the cause of it is. Is 9.20 an upgrade of 9.02, or is it a new version on it's own? If it's new, it won't likely go on top of an older VERSION. If it's an UPGRADE it should. As for the bookmarks in Opera, they are in a file called Opera6.adr  Save that file and install it later. 

Good luck,
Chappy

---

### Post by Qew on 2007-04-17
> **Buzzygirl said:**
> Hi, I'm running Dapper 6.06 and using Opera 9.02 as my browser. There's a new version of Opera available, 9.20. I downloaded the .deb package and tried to run it, but when I do, I get a message, "Error: conflicts with the installed package 'opera'." Does this mean I have to uninstall the old version? Will my bookmarks still exist if I uninstall the old version?

Thanks!

I'm running Dapper and have no problem installing the Opera deb that I got from Opera.com. Maybe you tried to install the static build over the shared .6 one. Try uninstalling the opera you currently have (use "sudo dpkg --purge opera" {no quotes} in a console) and try installing again. Also, yeah, your bookmarks should be safe doing this.

---

### Post by zvacet on 2007-04-17
Just ignore massage and install it.You can delete previous version because your Opera settings are safe in .opera folder.I think conflict is between version in repos and one you want to install.I had similar expiriences and just installed what I want and after that I never have problem.

---

### Post by Buzzygirl on 2007-04-17
Well, that went smoothly. I uninstalled the old version (9.02, opera-static) and then the new .deb file installed just fine. All of my bookmarks, settings and RSS feeds were preserved, so I didn't have to import them anew.

Thanks, folks! Opera rulez. :cool:

---

### Post by Daniel15 on 2007-04-19
For anyone that's getting the  "Error: conflicts with installed package 'opera'." error message in GDebi, upgrading via dpkg seems to work fine. Open a terminal (in Gnome, it's Applications &#8594; Accessories &#8594; Terminal), change to the directory you downloaded the package to (using the **cd** command), and then type:
```

sudo dpkg -i opera_9.20<tab>

```
The <tab> means to press tab - it will automatically fill in the rest of the filename. Press enter, and it should upgrade perfectly :)

> daniel@daniel-laptop:~/downloads$ sudo dpkg -i opera_9.20-20070409.6-shared-qt_en_i386.deb 
(Reading database ... 202845 files and directories currently installed.)
Preparing to replace opera 9.10-20061214.6ubuntu2 (using opera_9.20-20070409.6-shared-qt_en_i386.deb) ...
Unpacking replacement opera ...
Setting up opera (9.20-20070409.6) ...


---

### Post by Cannaregio on 2007-04-20
WATCH IT.
Export bookmarks somewhere and then reimport them after the update.
Else you risk losing them.
I'm glad I did, and that everything now works: I couldn't live without Opera.

sudo dpkg --purge opera
and then simply clicking the downloaded new version did the trick for me

---

