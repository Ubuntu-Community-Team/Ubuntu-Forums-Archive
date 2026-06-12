---
title: "How to use Evolution address book on Laptop and Desktop"
date: 2006-11-24
forum: General Help
---

### Post by fbn on 2006-11-24
Hi,

how can I use my Evolution address book on my Laptop and Desktop? Is there a way to synchronize?

Frank

---

### Post by dcstar on 2006-11-24
> **fbn said:**
> Hi,

how can I use my Evolution address book on my Laptop and Desktop? Is there a way to synchronize?

Frank

All Evolution files are in the (hidden) .evolution directory in your Home directory.

If you copy these from one machine to the other then they will have identical data.

---

### Post by turbojugend_gr on 2006-11-24
Adding to the above post, if you wish this to be done automatically, you can create a script. 

First of all, I just thought of that, and I don't own a second pc to test it, though I can't see no reason it won't. Anyway make a backup of your evolution hidden folder (~/.evolution), Simply copy it and then paste, a new folder named ".evolution (copy)" or sth similar should appear. Note that the dot(.) there indicates this is a hidden folder, so press CTRL+H to show hidden files/folders first.

Open Applications>>Accessories>>Text editor (**this should be done on the desktop pc**)

There paste the following (note you have to put your username and the appropriate location where I say so instead):
```

#!/bin/bash

cp -u /home/PUT_YOUR_USERNAME_HERE/.evolution PUT_THE_LAPTOP_NETWORK_LOCATION_HERE/home/THE_USERNAME_YOU_HAVE_ON_YOUR_LAPTOP_HERE/.evolution
```

Save the file in a folder, named "scripts" let's say,in your home folder, under the name "evolution-sync". open nautilus navigate to ~/scripts and right click the file. Select properties and under Permissions tab, make the file executable (allow execute as a program).

Now, make a panel launcher (right click on a panel>>add to panel>>custom launcher (or sth like that) button) or a desktop shortcut. There choose an icon that suits you, name the icon/launcher as you like it and in the command box click the navigate button next to it and select the evolution-sync file there, the command box should be filled automatically this way. In the comment box type "Thank you TJ!" lol ;).

Now whenever you click that icon/launcher, the evolution would be LITERALLY synced, the files will be replaced only if there's a change, or they are not present yet on the laptop. A real sync! See how easy and yet powerful Linux is? 

I guess I deserve that launcher comment after all..hehe! :-)

Let me know how it worked.

Cheers, TJ.

---

