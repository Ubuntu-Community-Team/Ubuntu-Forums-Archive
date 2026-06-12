---
title: "[SOLVED] Synaptic not opening, &amp;quot;line 81&amp;quot;."
date: 2008-04-10
forum: General Help
---

### Post by DJRhubarb on 2008-04-10
When I open Synaptic Package Manager or Add/Remove Programs I get this strange error message:

E: Type '\\' is not known on line 81 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E:_cache->( ) failed, please report.

And I can't run, sudo apt-get update.

Thanks, Rhubarb

---

### Post by hyperair on 2008-04-10
Open your /etc/apt/sources.list file, go to line 81, and post that line here please.

---

### Post by DJRhubarb on 2008-04-12
Hyperair: Open "/etc/apt/sources.list" in Terminal yeah??
Which I did and it says permission denied.
Is that what you meant?

---

### Post by hyperair on 2008-04-12
No just double click on it in Nautilus.

---

### Post by plucky on 2008-04-12
To display it ```
cat /etc/apt/sources.list
``` 
To edit it ```
gksudo gedit /etc/apt/sources.list
```

Be careful as you are in super user mode.You should make a copy first if you are not sure what you are doing.To do so ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

Good Luck

---

### Post by mikewhatever on 2008-04-12
Run <gksudo gedit /etc/apt/sources.list>, find the line that starts with \\ and delete the two backslashes, then save and exit. Now run <sudo apt-get update>.

---

### Post by DJRhubarb on 2008-04-12
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'  |  sudo tee -a /etc/apt/sources.list

---

### Post by DJRhubarb on 2008-04-17
I just had to delete the line that said wasn't working, alls good now, thanks.

---

