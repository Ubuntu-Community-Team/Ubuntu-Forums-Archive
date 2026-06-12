---
title: "Manually install xmms"
date: 2005-06-11
forum: General Help
---

### Post by wytzehoekstra on 2005-06-11
i installed the latest version Ubuntu 5.04 on mine and on my neighbours computer (i386).
At the moment I have all my sound and video's applications working (xmms and mplayer).
My Question is I did it like this: 

But my neighbour doens't have internet but his usb drive is working.
What do I need to install them manually and how do i do that?

Ok hope anyone can help me out.

---

### Post by az on 2005-06-11
Copy everything in /var/cache/apt/archives to the pen drive and then

sudo dpkg -i *.deb

everything in that directory on your other machine.

---

### Post by wytzehoekstra on 2005-06-11
oke i wonder what is a debian file then?

I suppose you will needed:
1.Liberaries for the compiler to handel the special commands
2.A compier to make a  binairy file (= .exe?)

But where does a .deb file constist of and wouldn't i need mp3/mpc codecs,,or are they also in this folder /var/cache/apt/archives?

---

### Post by wytzehoekstra on 2005-06-11
I checked the folder and it doesnt contain the xmms.deb

Anyhow  i still would like to know the following:
1. How to install xmms/mpc/mp3 or any software by compiling and installing the needed liberaries.
2. Is there already a complete C/C++ compiler standard available in 5.04 Ubuntu
3. A .deb package is an already precompiled package. I suppose it wouldnt need the liberaries any more would it?

Oke you would really help me with this...otherwise im just doing the trick without understanding.

---

### Post by wytzehoekstra on 2005-06-11
btw there are some "lib*".deb files in the archive folder.
for instance  lib***gcc.deb 
But after having greated a binairy the needed liberaries to compile the source aren't needed any further or are they?

I also tried to install mpc (see google first link) and i could download some binairies and a a tarred folder which contained several config and make files. i wonder why i need these binairies and I suppose the tarred folder contains files to build or make a library?

Well these are the question a come up with on this our....

ps: with binairies i mean the files that are stored in for instance   "--$:  /bin"

---

