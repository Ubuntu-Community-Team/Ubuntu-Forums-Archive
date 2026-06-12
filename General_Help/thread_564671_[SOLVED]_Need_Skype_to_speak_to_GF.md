---
title: "[SOLVED] Need Skype to speak to GF"
date: 2007-10-01
forum: General Help
---

### Post by elidoperezmd on 2007-10-01
Guys i need help really Bad. My GF moved out of the contru and need skype to speak.
I downloaded the Skype package and is sitting on my desktop and cant be installed. when i open it with GDebi Package Installer and wotn run, says that the package must be corrupted or i dont have the permission. i dont think is corrupted beacause the samething is happening with ohters packages.
what should i do.
Im a newbie, please be soft on the answer...how to install it even if is from the terminal, if soo please explain how to install from terminal.
i really need this and will aprecciate help.

---

### Post by Ek0nomik on 2007-10-01
> **elidoperezmd said:**
> Guys i need help really Bad. My GF moved out of the contru and need skype to speak.
I downloaded the Skype package and is sitting on my desktop and cant be installed. when i open it with GDebi Package Installer and wotn run, says that the package must be corrupted or i dont have the permission. i dont think is corrupted beacause the samething is happening with ohters packages.
what should i do.
Im a newbie, please be soft on the answer...how to install it even if is from the terminal, if soo please explain how to install from terminal.
i really need this and will aprecciate help.

Do you have permissions to install software on your computer?  I presume you have root (sudo) access?

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by miteshanand1729 on 2007-10-01
Download it from here [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)
and install...

---

### Post by scruff on 2007-10-01
I'm running Skype on my machine. Add a "universe" repository to "/etc/spt/sources.list (may even be multiverse, not sure).

```

# sudo nano /etc/apt/sources.list

```

Add: 

```

deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

```

Now do:

```

# sudo apt-get install skype

```

All done :)

---

### Post by elidoperezmd on 2007-10-01
hi all, thanks for the help

i do have permissions, 
the page given to me to download it from is where i got it from
when i enter 
elido@elidoperezmd:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
bash: deb: command not found

nothing hapend on multiuniverse either
what should i do?

---

### Post by misfitpierce on 2007-10-01
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

May be of some help

---

### Post by scruff on 2007-10-01
Nice link. That page should get you going elidoperezmd.

---

### Post by scruff on 2007-10-01
For discussion sake, I was pretty damn sure I used apt-get to install  skype on both my machines, but this wiki entry seems to suggest that it doesn't exist in any repository... Perhaps I was mistaken? It was a few months ago....

---

### Post by Ayuthia on 2007-10-01
> **scruff said:**
> For discussion sake, I was pretty damn sure I used apt-get to install  skype on both my machines, but this wiki entry seems to suggest that it doesn't exist in any repository... Perhaps I was mistaken? It was a few months ago....

I think that they are in the medibuntu repositories.  Here is the link on how to add the medibuntu repositories:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by elidoperezmd on 2007-10-01
i tried adding the repository as your great link says, but when i enter deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
i just get the same msg as before: bash: deb: command not found
so i decided to use the.deb package that downloaded and when open the gdebi package manager and hit the install button the computer freezes... is doing it with ither packages also.
/
thanks once agian for all the help. i know that we are coming to a solution. bare with me plz

---

### Post by rsambuca on 2007-10-01
Did you try just [downloading this file]("http://www.skype.com/go/getskype-linux-ubuntu") and double-clicking it?

---

### Post by rsambuca on 2007-10-01
I just noticed from your posts in other threads that you are currently having problems with your package manager.  You will need to get this fixed before you can install anything.

---

### Post by scruff on 2007-10-01
rsambuca - I dont' see that. He's trying to use 'deb' as a command, of which there is none. Those lines I posted should be added to sources.list, not ran in a terminal.

---

### Post by rsambuca on 2007-10-01
Yes I saw that, but from the other thread, the Op's apt isn't working, so nothing will install until it is fixed.

---

### Post by elidoperezmd on 2007-10-01
guess what????? SKYPE IS WORKING

thanks to you all, thanks for your help and mosto of all, your time and dedication.

once again thanks.

---

### Post by rsambuca on 2007-10-01
Great! but what did you do? :)

---

