---
title: "Cant log in the initial login screen"
date: 2007-04-11
forum: General Help
---

### Post by tom1979 on 2007-04-11
Today i got fed up with GAIM's continual logging me out whilst downloading torrents in ktorrent, so i booted into windows. my dual boot has been working great untill now, occasionally forcing a disk check after mounting the linux drives.

however today, i enter my name and password on the login screen, the scrren goes blank, and then the login screen returns. ive tried rebooting, rebooting to failsafe mode (but i havent a clue how to work from a prompt), and rebooting the previous install of ubuntu. Luckily xp still works!

Any ideas? im running 6.06, and have done all the updates and not updated for about a week now. ive been using KUBUNTU kde thingy(sorry still only getting the hang of the whole linux thing).

only other issues ive had leading to this is that aMSN wont allow me to sign in to hotmail account, gaim randomly logs me out of hotmail, (ill blame hotmail and microsoft for now for this:P ). everything else is fine, firefox and evolution mail work fine and i dont use much else tbh.

thanx in advance, as i have every faith in somebody knowing how to fix this!

---

### Post by solar george on 2007-04-11
Press ctrl+alt+F1 to get to a CLI login, See if you can login there.

---

### Post by tom1979 on 2007-04-11
yes that lets me log in... but i dont know how to operate from a command prompt being a windows user!! so where do i go from here to fix the problem?

i also noticed several other threads with the same problem and no cure yet, but i posted too soon before i saw them! sorry!

---

### Post by zvacet on 2007-04-12
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by firebadger on 2007-04-12
Worth checking your partition isn't full.  GDM doesn't like this and I have observed exactly this behaviour.

---

### Post by tom1979 on 2007-04-12
the linux partition, and in fact al partitions have plenty of free space, it was only 2 weeks ago in windows i had a low space warning, so u used g parted to re distribute 3gb to both windows and linux partitions from the 12gb shared partition.

ive looked at that website, but ubuntu and kubuntu have been on my system a while now, so i can only assume linux 'did something funky'.

seriously stuck with all these commands and things i need to type in, havent a clue what half of them do and why :(

ill have another go now and see what happens, but i dont have a backup pc to check and report errors as they happen :(

---

### Post by tom1979 on 2007-04-12
following instruction from that link, when i type 

sudo /ect/init.g/gdm start

or gdm=kdm, i get an unknown command error. the previous commands appeared to install something.

knowing my luck windows will die very shortly too...

---

### Post by tom1979 on 2007-04-12
RESOLVED!

turns out ktorrent was working over time and i had no disc space! well, 800mb left, but no warnings in the system! is this normal or can i set up a low disc space warning for the future?!

repartitioned with g-parted and im up and running again!

 cheers for the help.

---

