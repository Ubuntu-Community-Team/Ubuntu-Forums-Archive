---
title: "Total newbie question"
date: 2008-07-07
forum: General Help
---

### Post by sean_f on 2008-07-07
Hello,

I just started using Ubuntu a few days ago, and I am trying to get the hang of it. 

When I was updating the software etc I noticed that there was a BitTorrent program, which I downloaded. But how do I get this to run from the terminal window? I know with some programs (such as firefox, korganizer) you can just type in the name of the program in the window, and it starts. But this doesn't seem to be the case with BitTorrent.

Any help would be great.

Thanks 

Sean

PS - Sorry if this has already been asked, I took a quick look about and didn't see anything

---

### Post by stich0602 on 2008-07-07
> **sean_f said:**
> When I was updating the software etc I noticed that there was a BitTorrent program, which I downloaded. But how do I get this to run from the terminal window? I know with some programs (such as firefox, korganizer) you can just type in the name of the program in the window, and it starts. But this doesn't seem to be the case with BitTorrent.

Ubuntu comes with the Transmission BitTorrent Client installed by default (under Applications->Internet->Transmission BitTorrent Client). When you were running updates, you most likely installed an update to this program. This can be run from the terminal with the command "transmission" (no quotes).

If you would still like to use anther BT program, can you say which program it is?

And, Welcome to Ubuntu :)

---

### Post by adam_kimber on 2008-07-07
Hi! Welcome to the world of Ubuntu. Two quick questions... Which bitorrent client is the one you downloaded? There are several. Most have nice GUIs and do not require command line interaction. Which brings me onto my next question. Why do you want to start it from the command line?

---

### Post by sujoy on 2008-07-07
to start transmission from the command line just type in "transmission"
if, however, you are looking for a terminal torrent client, try out "rtorrent" or "transmission-cli"

---

### Post by sean_f on 2008-07-07
> **stich0602 said:**
> ...(under Applications->Internet->Transmission BitTorrent Client)..

Hmm, Transmission BitTorrent Client wasn't on that menu..don't know if that important.

As for a torrent program, I used uTorrent on Windows, but i'm not really bothered about which one I use. 

Would just like to get it going here if I can

---

### Post by sean_f on 2008-07-07
> **sujoy said:**
> to start transmission from the command line just type in "transmission"
if, however, you are looking for a terminal torrent client, try out "rtorrent" or "transmission-cli"

Okay, cool. Thank you.

---

### Post by stich0602 on 2008-07-07
> **sean_f said:**
> Hmm, Transmission BitTorrent Client wasn't on that menu..don't know if that important.

As for a torrent program, I used uTorrent on Windows, but i'm not really bothered about which one I use. 

Would just like to get it going here if I can

Right click your menu, select "Edit Menus". On the left, click the "Internet" tab, and check the box next to "Transmission BitTorrent Client".

If it is not there, open up Synaptic (System->Administration->Synaptic Package Manager) and search for "transmission-common". Right click the item with that name, and select "Mark for Installation". If Synaptic asks you to install other required items, agree to. Then click "Apply" on the top panel. This should install Transmission.

---

### Post by dog6 on 2008-07-07
I am new to programming and am stumbling through the process of getting started in the use of Fortran for some school studies I will begin in the fall...

I tried to install gcc using the apt...build-essential line as recommended and I get a line back in the terminal prompting me for my password.... and my keyboard will not type when this prompt comes up...any recommendations ..?

---

### Post by avtolle on 2008-07-07
Interpreting what you said, when entering a password at the terminal, there is no visual feedback. Type in the password and then press the Enter key, and you should be able to proceed.

---

