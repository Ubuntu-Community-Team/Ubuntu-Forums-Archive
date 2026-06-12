---
title: "[SOLVED] Repair Ubuntu"
date: 2007-07-19
forum: General Help
---

### Post by wannadumpwindows on 2007-07-19
I was trying to install automatix, and I apparently copied and pasted something wrong. Now I can't get any updates at all. Every time I try to add, remove, update or do anything to any package, I get this:
 
"E: Type '"deb' is not known on line 45 in source list /etc/apt/sources.list
E: The list of sources could not be read"

And now I have no idea on how to fix it, because I can't add or remove any packages to try and repair it. So I'm at a total loss. It was a fairly fresh install of Feisty so there isn't much saved on the partition, so I tried just reinstalling from the live cd, but that didn't help at all, it said it worked, but the next time I booted, it was still saying exactly the same thing. Any help anyone can offer would be greatly appreciated. Thanks in advance!

---

### Post by dabl on 2007-07-19
You don't need to do anything with packages to repair it, you need to open your sources file with an editor and remove the offending line.

So, in a console window enter ```
gksu gedit /etc/apt/sources.list
``` scroll down to the 45th line, which begins with "deb", and carefully delete just that line.  Then click "save" on your gedit menu, and exit the editor.

Assuming that's the only screwed-up line in your sources file, you should be able to restore the package manager's functionality, and get updated, with the following series of commands:
```

sudo dpkg-configure -a
```
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```
```
sudo apt-get update
```
```
sudo apt-get install
```

HTH :)

---

### Post by tszanon on 2007-07-19
> **wannadumpwindows said:**
> "E: Type '"deb' is not known on line 45 in source list /etc/apt/sources.list
It seems that your sources.list is wrong. I think that, in the line 45, there is a typo (**"deb** instead of just **deb**).
Fix:
1. edit /etc/apt/sources.list: **gksu gedit /etc/apt/sources.list**
2. go to line 45 and delete the quotation mark **"**
3. save and exit
4. run:
**sudo apt-get update**

It should fix the problem.

---

### Post by wannadumpwindows on 2007-07-19
Ok, I think I'm all set now. Looks like everything is back to normal. Thanx for your help.

---

