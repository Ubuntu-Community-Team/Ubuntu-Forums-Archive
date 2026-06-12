---
title: "Getting started..."
date: 2008-04-29
forum: General Help
---

### Post by The Ruckus on 2008-04-29
Well I finally gout WUBI to work and I can tell you, I sure am discouraged. Everyone gave me the idea that Ubuntu was very simple. I myself have wrote HTML, built my own PC's, repaired PC's I thought I knew enough to run Linux but apparently not :confused:

When I attempt to download something like GAIM, or Flash player it sends me to the extraction menu. I can either hit open which doesn't work, or extract it some where. So when I extract it to the desktop, and then click the set up, it asks for a directory ](*,)

So, I know this is a blatantly simple question to you guys, but it's really the only thing I'm having a hard time with (I'm on ubuntu at this moment) how in the world do I install flash on firefox, and GAIM (pidgin now apparently)

---

### Post by eriqjaffe on 2008-04-29
In a terminal

```
sudo apt-get install flashplugin-nonfree pidgin
```

Or just install them through Synaptic if you prefer a GUI.

---

### Post by tamoneya on 2008-04-29
you should take a look at system -> Administration -> synaptic package manager.  This will give you a GUI for installing programs.  Pidgin is located in the repository and you can just search for it.  You should also look for flashplugin-nonfree
you can also accomplish the same tasks by typing the following into terminal```
sudo apt-get install pidgin flashplugin-nonfree
``` You will find that many people who use linux prefer the command line version because it is a lot easier to type just that one line instead of doing the searching and all with a GUI.

---

### Post by forrestcupp on 2008-04-29
You have to change your mentality.  It really is a lot easier than Windows to install things, it just works differently.  We don't browse the net and download programs.  We install them from a central repository.  You can either open up Synaptic or Add/Remove Applications and search for Flash and Pidgin, and install them that way, or you can open a terminal and type
```
sudo apt-get install flashplugin-nonfree pidgin

```
It's as simple as that.

Edit:
I see I was beat

---

### Post by The Ruckus on 2008-04-29
Wow I didn't know this Synaptic package existed, it's confusing but browsing it I can tell this will be extremely convenient once I learn it, how cool.

---

### Post by forrestcupp on 2008-04-29
Synaptic includes everything, including system level libraries.  Check out Add/Remove Applications for a more user friendly GUI for installing apps.

---

### Post by Comhra on 2008-04-29
> **The Ruckus said:**
> Well I finally gout WUBI to work and I can tell you, I sure am discouraged. Everyone gave me the idea that Ubuntu was very simple. I myself have wrote HTML, built my own PC's, repaired PC's I thought I knew enough to run Linux but apparently not :confused:

When I attempt to download something like GAIM, or Flash player it sends me to the extraction menu. I can either hit open which doesn't work, or extract it some where. So when I extract it to the desktop, and then click the set up, it asks for a directory ](*,)

So, I know this is a blatantly simple question to you guys, but it's really the only thing I'm having a hard time with (I'm on ubuntu at this moment) how in the world do I install flash on firefox, and GAIM (pidgin now apparently)

Just make sure you stay calm and in a few days you'll begin to feel really comfortable.  

There is a learning curve but there is loads of support, here, in Launchpad and in Google.

---

### Post by The Ruckus on 2008-04-29
Well thanks everyone, I know the Linux community is always here, but I've been a little nervous to post a lot because I worried you guys will become frustrated trying to teach a new guy

---

### Post by The Ruckus on 2008-04-29
Well, I thought installing flash player would fix my problems. After installing it the video boxes like the ones on Youtube, or Pirillo Live just show a black box with a play button. If I click them, the entire box disappears :mad:

---

### Post by KaliVoid on 2008-04-29
Hi

i cant help you with the technical problems im also new
in linux (4.5 months) and im doing great :)
but i can help you in another way...

the best way to get started is to get a fresh mind set.

to do that read this article [Linux is NOT windows]("http://linux.oneandoneis2.org/LNW.htm")

that article put me on the right way ,i hope it will do 
the same to you.

---

