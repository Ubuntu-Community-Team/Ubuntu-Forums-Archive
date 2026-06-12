---
title: "permissions..."
date: 2008-04-15
forum: General Help
---

### Post by Dracar on 2008-04-15
I cannot do anything, it says that i dont have the correct permission, like editing my index.php file in /opt/lampp/htdocs/ anything that isnt right on my desktop, i cannot mod at all, I set my account to root lvl or w/e, but it does the same thing. I can't even delete empty folders if they aren't on my desktop =/

And as a side note, is there a way to get my old mysql databases from windows to ubuntu? i tried just copying the data folders contents over to the var/mysql folder but it didn't work, it has some odd error.

---

### Post by tgm4883 on 2008-04-15
You shouldn't put yourself in the root user group.  It's  a bad idea.


What you do need to do though is type 'sudo' before you do a command that needs root power

---

### Post by bodhi.zazen on 2008-04-15
> **Dracar said:**
> I cannot do anything, it says that i dont have the correct permission, like editing my index.php file in /opt/lampp/htdocs/ anything that isnt right on my desktop, i cannot mod at all, I set my account to root lvl or w/e, but it does the same thing. I can't even delete empty folders if they aren't on my desktop =/

And as a side note, is there a way to get my old mysql databases from windows to ubuntu? i tried just copying the data folders contents over to the var/mysql folder but it didn't work, it has some odd error.

Linux permissions take some adjustment, but they maintain security :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

to become root use sudo or sudo -i ; gksu for graphixal applications

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Transferring a database is not so simple as copying the data, you still need to install and set up mysql.

I am not an expert on mysql so unless someone else pipes in you may need to use google.

Typically this involves exporting the database from windows and importing it to Ubuntu.

---

### Post by Dracar on 2008-04-15
Well i can't save files or anything, unless i am root, and adding myself to the root user group did nothing at all =/ well yea, i switched myself back to my own group, but i still can't mod anything that isnt right on my desktop, and i dislike using terminal so i do most stuff without it

---

### Post by ibutho on 2008-04-15
Just run "gksu nautilus" and that will start nautilus with root privileges and you can then edit any files you desire.

---

### Post by Dracar on 2008-04-15
That works, not quite what I was looking for but its good, thanks very much.

---

### Post by ryanhaigh on 2008-04-15
```
sudo chown yourusername:yourusername /home/yourusername -R
```

---

### Post by Sidewinder1 on 2008-04-15
I'm a noob, but I believe that the "-R" should be between 'chown' and 'yourusername', not at the end; but it may work that way as well... HTH

---

