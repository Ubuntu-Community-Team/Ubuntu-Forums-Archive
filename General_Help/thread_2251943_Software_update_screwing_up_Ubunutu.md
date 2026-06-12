---
title: "Software update screwing up Ubunutu"
date: 2014-11-07
forum: General Help
---

### Post by element180 on 2014-11-07
I recently did a software update through the update manager and it removed both Gwenview and VLC. Went to reinsall them both through the terminal and I'm getting the "you have unmet dependancies". Trie installing them through Software center and I get the same thing. What the hell? I've never had software updates uninstall software like this before. Any suggestions?

---

### Post by Bucky Ball on 2014-11-07
Which release are you using?

---

### Post by Roasted on 2014-11-08
You could try it via terminal to see what it says, as terminal will give you more information in the text results. That would assist us with helping.

sudo apt-get install vlc gwenview

I also wonder if a "sudo apt-get install -f" would pull in the other dependencies.

Did you by chance reboot/shut down forcefully during the recent software upgrade? If so, "sudo dpkg --configure -a" might result in a fix.

Anyway, just a few ideas. Let us know where you end up! :)

---

### Post by ian-weisser on 2014-11-08
> **element180 said:**
> it removed both Gwenview and VLC. Went to reinsall them both through the terminal and I'm getting the "you have unmet dependancies"

The most common reason for unexpected uninstalls and unmet dependencies is that you installed non-Ubuntu software from a PPA or other non-Ubuntu source.

If so, you will need to:
1) Uninstall all non-Ubuntu software and non-Ubunutu dependencies that the non-Ubuntu source provided
2) Disable the non-Ubuntu source
3) Refresh your package database
4) Install the Ubuntu version of the software

Please open a Terminal and try these two commands. 
Copy-and-paste the complete output here (use ```
 tags).
The exact error messages will tell us what the problem is and where to start.
[code]sudo apt-get update
sudo apt-get upgrade
```

---

