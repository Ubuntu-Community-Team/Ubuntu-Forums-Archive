---
title: "k3b wont launch"
date: 2007-05-05
forum: General Help
---

### Post by Digitallysick on 2007-05-05
I cant get k3b to run, unless i go into the terminal and type sudo k3b

if i type k3b in the term i get this error

trying to create local folder /home/adam/.kde/share: Permission denied
trying to create local folder /home/adam/.kde/share: Permission denied
trying to create local folder /home/adam/.kde/share: Permission denied
trying to create local folder /home/adam/.kde/socket-adam-desktop: Permission denied
trying to create local folder /home/adam/.kde/socket-adam-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/adam/.kde/socket-adam-desktop/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.


how do i fix this?

---

### Post by jack_teagarden on 2007-05-05
I guess you are using GNOME?

Try making the missing directories- "sudo mkdir /home/adam/.kde/share" or whatever you need...

---

### Post by Digitallysick on 2007-05-05
I tried to create them, but it says they already exist, im in gnome

---

### Post by kodoku on 2007-05-06
Try typing
> kdeinit
in the terminal, and then try to run k3b

---

### Post by Digitallysick on 2007-05-06
still doesn't work when i type that, i get the same error as above

---

### Post by SirShaggy on 2007-05-06
> **Digitallysick said:**
> still doesn't work when i type that, i get the same error as above

I too am having this same exact issue. I can get it to launch as sudo, but not as a normal user. I tried clicking the icon and typing k3b in the terminal. I tried to make the directory and kdeinit, nothing yet.....
SirShaggy

---

### Post by SirShaggy on 2007-05-15
I spent 2 days on this, never got it to work. I just uninstalled K3b and reinstalled it. It has worked for 4 days now without any issue. Weird, but that's the way it goes......
SirShaggy

---

### Post by groovomata on 2007-11-10
I as well, could only launch k3b as sudo. Here's my solution to the problem. I completely removed k3b using synaptic. I launched nautilus as sudo and removed the .kde folder from my home directory. I then typed 'kdeinit' into a terminal. Then I reinstalled kd3 and I found that it was able to launch as a normal user.
I hope it works for you!
Erik.

---

