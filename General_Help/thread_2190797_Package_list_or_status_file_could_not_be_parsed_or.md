---
title: "Package list or status file could not be parsed or opened."
date: 2013-11-29
forum: General Help
---

### Post by fjnieto15 on 2013-11-29
Hi, 
I installed ubuntu 13.04 after trying 13.10 and now I got an error message I don't know how to fix, it says something like:
_
> 
<<Error: opening caché (E: Unable to parse package file/var/apt/list/es.archive,ubuntu.com_ubuntu_dists_raring_universe_i18n_Translation-en(1), E: The package list or status file could not be parsed or opened.)>>


What can i do?? :S

---

### Post by ibjsb4 on 2013-11-29
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

```
sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```

And welcome to the forums :)

---

### Post by fjnieto15 on 2013-11-29
It seems like it worked! Just a question, I've just changed the name of the lists file in order to create a new one, didn't I? Can I erase it? Also, what's the partial folder for?

Thank you man

---

### Post by ibjsb4 on 2013-11-29
>  I've just changed the name of the lists file in order to create a new one, didn't I?

Yes you did with the command:  sudo mv lists lists.old 
And it can be deleted if the new list is working.

> Also, what's the partial folder for?
sudo mkdir -p lists/partial
That partial list is in your "list" folder and it is not always recreated when you make your new list.  This will insure it is recreated.

Any other questions?

Edit:

Going off line; here's a handy list for apt-get commands.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

And don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Bye for now.

---

### Post by fjnieto15 on 2013-11-29
Well, thanks for the help :D

Bye

---

### Post by kelly4 on 2014-07-20
Required a reboot for me...

---

