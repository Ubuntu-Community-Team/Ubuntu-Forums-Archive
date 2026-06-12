---
title: "[kubuntu 18.04][eclipse ide] - add files to snap folder"
date: 2018-10-18
forum: General Help
---

### Post by sid11935 on 2018-10-18
Hi all,

New to linux. sorry if I have posted in the wrong forum but I need to install a plugin in eclipse ide (for school work). It is an outdated/obsolete plugin, which can only be installed by adding it to the plugins/dropins folder inside eclipse.(no online repository that links to eclipse)

I initially tried installing eclipse and java regularly from the package manager but for some reason java v10 could not install. so i decided to install the snap version of eclipse, which included everything it needs to run. 

So basically, I just need to paste the contents of two folders in my home directory to /snap/eclipse/current/dropins or /snap/eclipse/current/plugins.

Unfortunately, there is no way for me to add files to a snap folder. Terminal says read file system only. I realize, from my limited reading, that snaps are designed so that it cannot be tampered with. But is there a workaround to put the aforementioned files in the snap folder?



Any help would be appreciated.
Thanks

---

### Post by mpeccorini on 2018-10-23
Hi,

In your home folder, there should be a "**.eclipse**" folder. Inside you will find several other folders and one of them has a name like **360744347_linux_gtk_x86_64** (The name in your case may be different). Inside that folder you will find the **plugins** folder where you can drop your jar file.

I hope this helps,

Mauricio

---

