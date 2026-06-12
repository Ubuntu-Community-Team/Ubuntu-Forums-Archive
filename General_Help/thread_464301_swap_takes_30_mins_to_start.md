---
title: "swap takes 30 mins to start"
date: 2007-06-04
forum: General Help
---

### Post by miketowninc on 2007-06-04
is that normal. I did ubuntu with 500 mb and it took 18 mins or so and then i did ubuntustodio with a 1 gb swap and it takes 30 mins to activate the swap file. is that normail. how much swap should i paritition i have 256 ram

---

### Post by ago on 2007-06-04
No it's not normal.
Copy over any another file of 256 MM. Then from linux: 

sudo mkswap /media/host/wubi/disks/swap.virtual.disk
sudo swapon -a

---

### Post by miketowninc on 2007-06-04
Copy over any another file of 256 MM. Then from linux: 

what does htat mean sorry

---

### Post by ago on 2007-06-04
It's a way to create a brand new swap virtual disk.

---

### Post by miketowninc on 2007-06-04
so should i make my swap file 256?

---

### Post by miketowninc on 2007-06-04
Copy over any another file of 256 MM. what file?

---

### Post by ago on 2007-06-04
Any file. Wubi just need to have a file of 256 mb to convert to swap (it does not have to be an exact size). The easiest way to create that file is to copy on top of it any other file which is large enough. Or you can use qemu-img if you prefer.

---

### Post by miketowninc on 2007-06-04
should i make my swap size 256 ? or larger?

---

### Post by ago on 2007-06-04
make it as large as your memory.

---

### Post by miketowninc on 2007-06-04
just to throw it in i told the podcast maker of sourcetrunk about wubi and he wrote back and said

thanks for the link, I'm including Wubi in the next episode.

I hope you guys get more users!!! So is 256 sound good? im reinstalling because i deinstalled before i ask you this thanks

---

### Post by ago on 2007-06-04
thanks for that

---

### Post by miketowninc on 2007-06-06
hi the swap problem was solved by just reinstalling and making it 256 mb of swap. thanks for the help. i have Although another problem.:( im not sure if it is wubis problem or ubuntusudio. after the installation and such and after the swap is loaded it comes up with graphic problems and says that the server x could not be found. (or not used cant remember) and asks if i want to see the log. If i say no then it just goes to the terminal and waits for me to put an input in. well thanks if you can help

---

### Post by ago on 2007-06-06
> **miketowninc said:**
> hi the swap problem was solved by just reinstalling and making it 256 mb of swap. thanks for the help. i have Although another problem.:( im not sure if it is wubis problem or ubuntusudio. after the installation and such and after the swap is loaded it comes up with graphic problems and says that the server x could not be found. (or not used cant remember) and asks if i want to see the log. If i say no then it just goes to the terminal and waits for me to put an input in. well thanks if you can help

That might be a general issue (new ati?) you are better off to ask on the ubuntu support forum, wubi does not differ from standard ubuntu when it comes to the video card/X.

---

### Post by miketowninc on 2007-06-06
ya i thought so ok i will
 but just in case here is the error message i restarted and wrote it down


Failed to start the X server. It is likely that it is not setup correctly.

thanks

---

