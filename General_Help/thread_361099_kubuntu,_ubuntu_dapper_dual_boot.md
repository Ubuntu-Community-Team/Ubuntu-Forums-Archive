---
title: "kubuntu, ubuntu dapper dual boot"
date: 2007-02-14
forum: General Help
---

### Post by stonerrob420 on 2007-02-14
Hello! I have ubuntu 6.06 installed on my computer and i am using kubuntu 6.06 live cd to type in the forum....my question is how do I setup it to be dual boot between ubuntu and kubuntu.....my primary master HD is a western digital 80 GB and my secondary master is a IBM deskstar 13 GB....how can i install kubuntu without losing ubuntu....i havent had very much success in the past doing it. Do they have to be on the same drive? I have only been using linux for a few months and still have much to learn.....Any help would be much appreciated:)

---

### Post by rsambuca on 2007-02-14
Actually, ubuntu and kubuntu are the same Operating system, but they use different desktop environments.  Ubuntu uses a gnome based desktop, while kubuntu uses a KDE based desktop.

Seeing how you already have ubuntu installed, just use that and install the kubuntu desktop.  Then, whenever you login, in the Options section you can select either ubuntu or kubuntu for your particular session.

To install kubuntu on your system, open a terminal and enter```
sudo aptitude update
```
then ```
sudo aptitude install kubuntu-desktop
```
Now, whenever you login, you can select either/or, and see which desktop environment you prefer!

---

### Post by stonerrob420 on 2007-02-14
Thank you i will give it a try.......:)

---

### Post by stonerrob420 on 2007-02-14
Since they are the same OS can i take it off of the live cd? like using sysnaptic? I'm on a dial up connection and it would take a long time to download all the files.

---

### Post by rsambuca on 2007-02-14
hmmm...  never heard of that.  It can't really hurt anything to try.  If you insert the CD and start synaptic, there is a section in Settings, Repositories.  There is a spot for CD/DVD, but is always grayed out on my system.  I guess it could be because I have never run Synaptic with a disc loaded in the tray.  

If that doesn't work you will probably have to install via your dial-up, which for kubuntu will take quite a while.

Let me know if it works.

---

### Post by stonerrob420 on 2007-02-14
i installed kubuntu on my 13 GB HD and still got ubuntu installed on my 80 GB HD....they are both set to master.....is there any way i can configure the ubuntus as dual boot? i think that would fix my problem.......I like features in ubuntu as well as kubuntu eventhough they are the same OS......The cd idea didnt work through sysnaptic.....but from now on im a linux user ill never go back to winblows XP......:)

---

