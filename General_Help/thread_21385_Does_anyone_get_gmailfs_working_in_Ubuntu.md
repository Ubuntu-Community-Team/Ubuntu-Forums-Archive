---
title: "Does anyone get gmailfs working in Ubuntu ?"
date: 2005-03-21
forum: General Help
---

### Post by cyu021 on 2005-03-21
Hi folks,

Does anyone get "Gmailfs" working in ubuntu?
It seems that the "python-fuse" in ubuntu's repository is not quite up-to-date. Gmailfs need at least version 2.2 of python-fuse to work, while ubuntu only provide one with ver 1.3 ...

If there is anyone gets gmailfs rolling, please let me know.


Thanks in advance,
James

---

### Post by Burgundavia on 2005-03-22
There is a general python rebuild happening right now, in time for the hoary release.

Corey

---

### Post by Lord C on 2005-04-11
[QUOTE=cyu021]Hi folks,

Does anyone get "Gmailfs" working in ubuntu?
It seems that the "python-fuse" in ubuntu's repository is not quite up-to-date. Gmailfs need at least version 2.2 of python-fuse to work, while ubuntu only provide one with ver 1.3 ...

If there is anyone gets gmailfs rolling, please let me know.


Thanks in advance,
James[/QUOTE]
 I submitted a bug, and they updated fuse to 2.2

But now gmail will not mount due to a fusermount error :s

---

### Post by lao_V on 2005-04-11
I'm having problems as well..any help would be appreciated

---

### Post by Lord C on 2005-04-11
[QUOTE=lao_V]I'm having problems as well..any help would be appreciated[/QUOTE]
 Are you having [this problem](http://www.ubuntuforums.org/showthread.php?t=24386&highlight=gmailfs)?

---

### Post by lao_V on 2005-04-11
[QUOTE=Lord C]Are you having [this problem]("http://www.ubuntuforums.org/showthread.php?t=24386&highlight=gmailfs")?[/QUOTE]

Yes, getting: fusermount: old style mounting not supported

---

### Post by guardian653 on 2005-05-04
I'm having this same problem as everyone else:

fusermount: old style mounting not supported

anyone know of a solution? (googling it hasn't shown anything useful) I've even compiled the fuse-source package and installed the kernel module--no go. I'm using gmailfs-0.3-2ubuntu1.

---

### Post by Leszek Tarkowski on 2005-05-17
[QUOTE=guardian653]I'm having this same problem as everyone else:

fusermount: old style mounting not supported

anyone know of a solution? (googling it hasn't shown anything useful) I've even compiled the fuse-source package and installed the kernel module--no go. I'm using gmailfs-0.3-2ubuntu1.[/QUOTE]
 Another question:
why python-fuse depends on:
-python2.3-fuse (>= 2.2)

python2.3-fuse ?? why should i install python2.3 if i have 2.4? strange...

---

### Post by magaltavor on 2005-05-22
hi all as i saw th problme i had to to main problem as i really think is python when ever you look in synaptic on the depnedencies of gmailfs you will notice python2.4 sorry to tell you i read a full document in linux-magazine in the issue 55 know-how on gmailfs and it says that gmails fs do not work with python 2.4 it says 2.3 and hoary by default has pythin 2.4 installed ,if you want to work with gmaifs you could download the tar ballz and compile them manually with the kernel issue and it will work fine ,beside that to remove all python 2.4 related and reinstall 2.3 ,it is a long procedure and i am ready to discuss it if any one interested ,gmailfs from scratch ,manually compiled ,but guys personnaly i could wait a fix for that instead of messing off my kernel and my lovely ubuntu

---

### Post by virtualXTC on 2005-10-05
<begin opinion>
Solution: Switch to Debian!!!
Really, all these package re-builds are eventually going to make Ubuntu completly incompatible with the Debian base it's derived from.
If you want a simple install where everything "just works" try simplyMEPIS. It's more robust (more contrib packages), easier to install, and will leave you with a Debian based system at the end!!
Or you could try compiling your own python libraries - but given my experience with the administrative functions of Ubuntu, it'll be quicker and less painful to install Mepis, and at least you'll be able to get a root terminal after the install (sudo -ing every single command, especially when configuring packages, is like having re-insert your ignition key to start your car after each red light you hit...  )
Conceptually, Ubuntu is great, but until it finds a way to bring it self back in line with Debian (either by helping Debian catch-up, or waiting for it), it won't make it's way on to my machines.
</opinion>
<actual work around>
disclaimer: as stated above - I run Debian - not Ubuntu - so I have not tried this my self, but I can't see why it wouldn't work unless the python's dependencies are also out of date and thus drag down your whole system.
1.	Start a Shell session.
2.	Edit your sources list:
```

sudo gedit /etc/apt/sources.list

```
3.	Add Debian repositories (Mirrors): 
```

deb http://http.us.debian.org/debian stable main contrib non-free
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
deb http://security.debian.org stable/updates main contrib non-free 
```
4.	Pin down Debian packages to ensure compatibility:
```

sudo gedit /etc/apt/preferences
```
Add:
```
Package: *
Pin: release o=Debian
Priority: 200
```
5.	Update your sources list:
```
sudo apt-get update
```
6.	Upgrade all packages
```
sudo apt-get dist-upgrade
```
If you don't see the python package updated, try specifically singling it out with it's dependencies: 
```
sudo apt-get -f install python
``` If it's still not installing, you might try unpinning debian packages, singling out python, then re-pinning, but it's risky.
</actual work around>

---

### Post by magaltavor on 2005-10-06
do you think ubuntu has the smae stucture per example of debian sarge ,
ur talking about debian sarge here most stable linux version from all the way but in ubuntu will find the same but if your gonna use latest packages mean universe or multiverse ,or unstable ,ur going to blow up your ubuntu or debian ,so i am not gonna install sarge on my laptop ,by the way did you used ubuntu for server purposes if yes please tell me cause i used it and it is good 


[quote=virtualXTC]<begin opinion>
Solution: Switch to Debian!!!
Really, all these package re-builds are eventually going to make Ubuntu completly incompatible with the Debian base it's derived from.
If you want a simple install where everything "just works" try simplyMEPIS. It's more robust (more contrib packages), easier to install, and will leave you with a Debian based system at the end!!
Or you could try compiling your own python libraries - but given my experience with the administrative functions of Ubuntu, it'll be quicker and less painful to install Mepis, and at least you'll be able to get a root terminal after the install (sudo -ing every single command, especially when configuring packages, is like having re-insert your ignition key to start your car after each red light you hit...  )
Conceptually, Ubuntu is great, but until it finds a way to bring it self back in line with Debian (either by helping Debian catch-up, or waiting for it), it won't make it's way on to my machines.
</opinion>
<actual work around>
disclaimer: as stated above - I run Debian - not Ubuntu - so I have not tried this my self, but I can't see why it wouldn't work unless the python's dependencies are also out of date and thus drag down your whole system.
1.    Start a Shell session.
2.    Edit your sources list:
```

sudo gedit /etc/apt/sources.list

```3.    Add Debian repositories (Mirrors): 
```

deb http://http.us.debian.org/debian stable main contrib non-free
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
deb http://security.debian.org stable/updates main contrib non-free 
```4.    Pin down Debian packages to ensure compatibility:
```

sudo gedit /etc/apt/preferences
```Add:
```
Package: *
Pin: release o=Debian
Priority: 200
```5.    Update your sources list:
```
sudo apt-get update
```6.    Upgrade all packages
```
sudo apt-get dist-upgrade
```If you don't see the python package updated, try specifically singling it out with it's dependencies: 
```
sudo apt-get -f install python
``` If it's still not installing, you might try unpinning debian packages, singling out python, then re-pinning, but it's risky.
</actual work around>[/quote]

---

### Post by Yagisan on 2005-10-06
Why don't you try breezy's gmailf fs instead ? release is very soon - and it's better to not mix and match between Ubuntu and Debian packages.

---

### Post by magaltavor on 2005-10-06
This is what i am talking about i think that breezy will do a big noise in the desktop linux future ,i can see some hps has ubuntu pre-installed on 


[quote=Yagisan]Why don't you try breezy's gmailf fs instead ? release is very soon - and it's better to not mix and match between Ubuntu and Debian packages.[/quote]

---

