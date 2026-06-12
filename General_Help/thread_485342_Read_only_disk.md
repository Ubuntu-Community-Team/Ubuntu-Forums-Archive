---
title: "Read only disk"
date: 2007-06-26
forum: General Help
---

### Post by sgreener on 2007-06-26
Hi 

I have a 120 gb drive that i was using as a data backup drive when i was running windows that i cannot make any changes to after installing feisty.  every time i try it says the disk is read only.  i think its formated to ntfs.  i have tried going into the prefences/permissions screen but cant change the access field from read only.  the owner and group are both showing as unknown.  
any help would be appreciated

---

### Post by merlinus on 2007-06-26
If it is indeed formatted as ntfs, you need to install ntfs-3g and/or ntfs-config.

```

sudo apt-get install ntfs-3g
sudo apt-get install ntfs-config

```

Then run

```

sudo ntfs-config

```

Follow the instructions, and restart.

-merlin

---

### Post by nate22 on 2007-06-26
hmm when i do that i gett a error message saying 
E;type "ftp//ftp vlc......" i not known in line 26 of source list 
E; the list could not be read....


why?

---

### Post by merlinus on 2007-06-26
It probably means that certain repositories are not enabled in /etc/apt/sources.list.

Try this:

```

sudo apt-get update

```

and then try the other commands to install the ntfs apps.

-merlin

---

### Post by nate22 on 2007-06-26
yea i tried to do that...and heres what i get 
[IMG]http://i41.photobucket.com/albums/e282/lilnate22/Screenshot.png[/IMG]


i tired to edit the file..but it tels me i dont haev the privilages

---

### Post by merlinus on 2007-06-26
You can try to install it via Synaptic.  Select All and then search for

ntfs-config

To edit the file:

```

gksudo gedit /etc/apt/sources.list

```

-merlin

---

