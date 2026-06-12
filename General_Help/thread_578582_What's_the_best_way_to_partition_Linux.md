---
title: "What's the best way to partition Linux?"
date: 2007-10-17
forum: General Help
---

### Post by Dead_$partan on 2007-10-17
Hi All,

I will be installing 7.10 tomorrow night, dual booting with Vista for now until I can get all my games working under Ubuntu.

I want to know what the best method is for partitioning my Linux install, I want to be able to keep existing data when I upgrade my distribution every 6 months or so but I prefer to do a format/re-install with each update rather than upgrading directly over the top of the existing install.

I was thinking of putting **/home** on it's own partition, I hope that this will retain any theme changes etc that I have made but what about programs or drivers, codecs etc that I install, they won't all necessarily go to my **/home** partition so are there other areas I would be best putting on their own partitions so that whenever I format and re-install in the future i can leave these partitions as they are and do everything else?

I hope I made this clear enough.

Iain

---

### Post by p_quarles on 2007-10-17
Just one question: are you looking to wipe your current Linux partition and use the the 7.10 disk to create the new partitions (easiest)? Or do you want to move your current home directory to the new /home partition (more difficult, but doable)?

---

### Post by LanDan on 2007-10-17
think the idea you already have is the correct one

what i usually do for a desktop is something like below

/SWAP 512MB
/           10 GB
/home   all the rest what is left


the next time you install you choose to mount the same /home partition again but DO NOT FORMAT /home

all your programs and drivers go to / so these will be overwritten with your next install
all your files and personal program setting go into /home (check the .config files in your home)

---

### Post by Dead_$partan on 2007-10-17
p_quarles - Yeah I am going to wipe my hard disk clean and do a fresh install.  I prefer the easy option :lolflag:



LanDan - Thanks for this, cant you also partition the areas where these drivers etc go too?  Dont the go in /usr???

Thanks for the swift replies guys, much appreciated :)

---

### Post by LanDan on 2007-10-17
yes you can and i actually do this when installing a server

you can put /usr/src /boot /etc /anykindoffolder etc....on seperate partitions

but i think this kind of scheme is overdone for a normal desktop ;)

as for your drivers, these depend on your running kernel and i think you will run into trouble trying to preserve these when doing a 6 monthly re-install
most drivers will be on the install cd anyway, you have any special drivers????
if you have to use some drivers not included in the install for example some printer that does not support linux, i would advice you to keep this in a folder in your /home together with a memmo on how to install these quickly again

---

### Post by Dead_$partan on 2007-10-17
No drivers at all now that i think about it..lol but mainly for programs that I would install myself over and above the main instal, its a pain having to add them again and again.

I think all the theme based settings will all be saved in /home so all that should be covered.  TBH the programs thing isnt major as its just a couple of things, its just a little annoying.

---

