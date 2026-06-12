---
title: "Locate is broken?"
date: 2008-02-25
forum: General Help
---

### Post by urangela on 2008-02-25
I tried to use the locate command to find a particular file, but even though the file is CLEARLY on the machine, locate doesn't find it. If I go to the directory where the file lives, and type ls, the file is displayed on the screen, along with the rest of the directory's contents. Even if tell locate to search for the EXACT file name, it comes up blank. The file is a binary file, locate works fine for other binary files. I tried case insensitive searches, I tried changine the security level to zero, I tried searching from every directory in the file's path beggining with root. And it still comes up empty. I even tried restarting the machine. Below is an example of my terminal's response:

adam@Tiamat:~$ locate Tui*
adam@Tiamat:~$ cd De*
adam@Tiamat:~/Desktop$ ls
aria-proii-slap-bass-sf2.zip  Microbiology paper  STEWS DRIVERS
bleach                        music               torrent files
chemecology                   old ipod            TRAVELDRIVE.zip
composition                   Oscillator.pd       [COLOR="Red"]TuioClient.pd_linux[/COLOR]
field ecology                 plot_map.ods        videos
foo.c~                        programming         Wireless instructions.txt
Formula_HowTo_1_0.pdf         pulse.py~
hello.c~                      sawwave.py~
adam@Tiamat:~/Desktop$ locate Oscil*
/home/adam/Desktop/Oscillator.pd
adam@Tiamat:~/Desktop$ locate Tui*
adam@Tiamat:~/Desktop$

The file that locate seems to be ignoring is marked in red. Notice, that locate finds another file in this directory without any trouble. Any insight comes highly appreciated. I am going to try rebooting...again....

PS I am running gutsy 7.10 with the latest real-time kernel

-------- Addendum ----------

So out of curiosity, using vi, I created several text files each with a little bit of gibberish, named:
Tuio.txt, Tua.txt, Tui.txt, and I searched for them with Locate.
To my surprise locate couldn't find any of them. If I were to Type in:

locate T

or 

locate Tu

I get a list of files longer than my forearm. As soon as I try to search for the strings "Tui" or "Tua", locate just returns nothing. 
Am I doing something wrong here?

---

### Post by urangela on 2008-02-26
I kindof freaked out, but when I did a little digging, I found out about the
program updatedb; as soon as I ran that, locate found exactly the files I was looking for.

For those who might benefit, the updatedb command runs a program, that updates the data base which locate  works out of. check out GNUfindutils for more info.

---

### Post by soldats on 2008-02-26
hrmm you might want to try "whereis <file>" or "which <file>".
it may be better to do a find ie.
find / -name <file>

edit: but yes updatedb did work for you so i guess your set. have fun.

---

### Post by pointone on 2008-02-26
You'll need to run "sudo updatedb" to update the database used by locate. It's only automatically updated via cron job weekly, if I recall correctly, so it is sometimes out of date.

---

