---
title: "Problem with external hd, no fix has worked, any advice?"
date: 2008-06-14
forum: General Help
---

### Post by Open-SuSe-A-Me on 2008-06-14
greetings,

i have a 160gb western digital external hd which is formatted as fat32. i went on a 'buntu spree experimenting with the different flavors and i cannot write to the disk in any of them. i get an error "can not write to disk /blah/so-on/so-forth permission denied" i have tried numerous suggestions from the forums but nothing works. i also tried right-click preferences and tried to change the permissions but i get denied even when i open the folder as root in dolphin. i can transfer the files to my hd but cant write to the external, any ideas?

i'm running kubuntu hardy kde3.5 

try to be gentle if you have any konsole commands for me.

thanks!

---

### Post by ianbrown75 on 2008-07-01
I am running into the same problem, I am sure there is an answer, but I have not found one yet.

---

### Post by soccerboy on 2008-07-02
can you ```
chown -R username:username <mountpointofdrive>
``` replacing username with your username?

---

### Post by ianbrown75 on 2008-07-02
not sure what to put for <point of drive>

---

### Post by soccerboy on 2008-07-02
what is the output of ```
sudo fdisk -l
``` on your machine with the external hd plugged in?

---

