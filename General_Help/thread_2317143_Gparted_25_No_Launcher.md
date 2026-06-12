---
title: "Gparted 25 No Launcher"
date: 2016-03-13
forum: General Help
---

### Post by Redalien0304 on 2016-03-13
Ubuntu 14.04 W/ Cinnamon DE. Installed Gparted 25 from Source, no Launcher was created. I made one with the Cinnamon Menu Editor, but does not Start Gparted. Only way i can Started Gparted 25 is to go to the Installed Dir usr/local/share/applications & Double Click & Gparted 25 Runs. Will not with my Launcher, it is pointed to the Dir. "gksudo /usr/local/share/applications/gparted.desktop" is what im using for the command. Gparted 24 is also installed.

Thanks in advance for any Help Thanks.

---

### Post by montag dp on 2016-03-13
I'm sorry, your post is kind of confusing.  When you used Cinnamon menu editor, did it create the launcher that is in /usr/local/share/applications (the one that works)?  If so, what is this command "gksudo /usr/local/share/applications/gparted.desktop"?  Are you entering it in the terminal, or something else?

---

### Post by Bucky Ball on 2016-03-13
Why compile from source? It's in the Software Centre. Install that version. You will not see any massive differences, if any at all. Do you have a (very) specific reason for installing this version rather than the tested and approved version in the 14.04 repositories (0.22.0)?

---

### Post by Redalien0304 on 2016-03-13
I created the Launcher in Cinnamon menu Editor. "gksudo" i copied from the gparted 24 Launcher Command & Created a  new Launcher & put in the path to gparted 25 /usr/local/share/applications/gparted.desktop 

I want the Latest Version of Gparted installed, which is stable Gparted 25 for Exenial. I have been able to update Gparted  22 - 24 via "sudo apt-get update gparted".

Thanks

---

### Post by montag dp on 2016-03-13
When you say you put in the path, I'm assuming you mean you put it in the Exec= line of the launcher? If so, your error is that the path is wrong. gparted.desktop is only the launcher, not the executable itself. Why don't you post the contents of the launcher you created here, as well as the location of the gparted executable you compiled, and someone will be able to help you fix it.

I agree with Bucky Ball though, unless you have a specific reason to use the latest version (i.e., some feature that you know you need and is not present in the version in the repositories), you should just use the version in the repositories. That is, unless you are just doing this as a learning experience. And if you do use the version you compiled yourself, you should not install it in the root directory, just run it from somewhere in your /home directory. This will prevent conflicts with the package manager.

---

### Post by Bucky Ball on 2016-03-13
> **Redalien0304 said:**
> 
I want the Latest Version of Gparted installed, which is stable Gparted 25 for Exenial.

My question was why. What benefits/advantages are you expecting from a newer Gparted? It really isn't going to make a squidge of difference in the overall scheme of things considering what gparted does. 

Is your machine stable? Does gparted in the repos work? Then what's the issue and why the burning desire for the latest? Something to tinker with?

Why not go all the way and install Xenial on another partition. Then you can have the newest everything, but be prepared for the breakage that is normal using a development version. 

Good luck, in any case.

---

### Post by Redalien0304 on 2016-03-14
Found a Solution, changed Path to usr/local/sbin. now have gparted 25 running.

---

### Post by Bucky Ball on 2016-03-14
Good news. Please see the first link in my signature and mark thread as solved. :)

---

