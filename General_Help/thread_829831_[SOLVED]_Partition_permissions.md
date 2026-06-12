---
title: "[SOLVED] Partition permissions"
date: 2008-06-15
forum: General Help
---

### Post by Man_Beach on 2008-06-15
When I installed Ubuntu I created an extra partition (which I called 'data'). I would now like to use it to store some files but don't have the required permissions - owner and group are both 'root'.
Having had a rather frightening experience recently when, using the terminal,  I managed to change the permissions in one of my directories to 'unrecognised permissions' (thankfully I eventually managed to correct it), I don't want the same thing to happen to a whole partition.
Could someone walk me through the exact process I need to go through so that I can easily access this partition without being root?

---

### Post by drs305 on 2008-06-15
Removing post as I misidentified the request. See vandium's post below.

---

### Post by Man_Beach on 2008-06-15
It's mounted OK - I can see it in Nautilus (between CDrom and dev) - I just need to know how to change the permissions so that I don't need to be root to access it.

---

### Post by drs305 on 2008-06-15
> **Man_Beach said:**
> It's mounted OK - I can see it in Nautilus (between CDrom and dev) - I just need to know how to change the permissions so that I don't need to be root to access it.

I'm removing the post as I misinterpreted what the OP wanted. See vanadium's post below for the solution.

---

### Post by vanadium on 2008-06-15
As root, create a directory on the extra partition, then make yourself the owner of that directory. Place a link to that directory in your home directory for easy access.

Command line:

sudo mkdir /media/data/mydata
sudo chown $USER:$USER /media/data/mydata
ln -s /media/data/mydata data

(don't even need to be root for the last command)

Graphical approach: load nautilus with root permissions

gksudo nautilus

1) Create the directory mydata 2) Change its ownership (right-click - permissions tab) 3) Create the link (right-click - Make Link; this creates a link named "Link to mydata". Move that to your own home directory and change the name to "data" or any name you like).

---

### Post by tommcd on 2008-06-15
I have had this problem also. All I do is run 

"sudo chown -R tom:users /data"

 The -R switch is for recursive; i.e., all subdirectories within /data will be owned by you as well. My username is tom. Substitute your username for tom in the command above.

---

### Post by vanadium on 2008-06-15
This will work, but is an inflexible solution if you have more than one user on the system.

---

### Post by Man_Beach on 2008-06-15
Nice and simple and well explained. Thank you both, tommcd and vanadium.

---

