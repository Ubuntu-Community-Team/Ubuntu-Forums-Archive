---
title: "Installing VLC Media playery version 0.8.6a"
date: 2007-01-20
forum: General Help
---

### Post by Souljah on 2007-01-20
Hi,

Well doing a search in synaptic doesn't show the most updated VLC media player. So I downloaded a .tar.gz version of it. I extracted it onto a folder on the desktop and followed the install instructions which are **./configure**, **make**, and **make install**. It installs fine, it runs fine.

My question is, I want it to install system wide. Under general circumstances, applications should be installed to the /usr/local directory, am I right? Therefore, hypothetically speaking if my filename was vlc0.8.6a.tar.gz and it was on my desktop, how would I install it system wide?

Correct me if if I'm wrong but would I do ```
tar -xzvf vlc0.8.6a.tar.gz -C //usr/local
``` Or is there something else to it. 

As a sidenote, I tried to do a sudo checkinstall on it but it came up with errors. How can I fix that as well or is that common. Thanks.

Ryan

---

### Post by bionnaki on 2007-01-20
0.8.6 is in the repos

---

### Post by Souljah on 2007-01-21
Where, I have enabled all multiverse and universe repositories. It still shows as 0.8.4.

---

### Post by TrinitronX on 2007-01-21
Shouldn't they have updated the 0.8.6 in the repos to 0.8.6a by now?  0.8.6.a was a security update... and we all know how us linux users like security :D

---

### Post by po0f on 2007-01-21
TrinitronX and bionnaki,

Notice Souljah is using 6.06.


Souljah,

The suggestion to extract the source to /usr/local/src was just that, a suggestion.  I just like to keep all my source programs in one directory.  When you `sudo make install` or `sudo checkinstall`, it should still install it system-wide.  From a terminal, execute:
```
[FONT="Courier New"]$ which vlc[/FONT]
```
(or whatever the vlc command is called) to confirm that it has been installed in /usr/local/bin.  (Provided you ran a default "./configure".)

---

### Post by Souljah on 2007-01-21
By default it installs it in usr/loval/bin. Ok. I'm going to do this right now. The program recommend I do ```
./configure --prefix=/usr --enable-wxwindows
``` so I did that. I will let you guys know how it goes.

---

### Post by Souljah on 2007-01-21
The shortcuts for the program now works, only thing is that it doesn't want to save my default equalizer settings, I don't really understand why.

---

