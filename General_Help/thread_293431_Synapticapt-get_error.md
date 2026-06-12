---
title: "Synaptic/apt-get error"
date: 2006-11-05
forum: General Help
---

### Post by lemmy999 on 2006-11-05
Tried installing a .deb for the latest flashplayer9 using Gdebi. Halfway thru the install stopped completely. In the terminal i could see that i needed to agree the eula. I couldn't navigate there to agree so I aborted the install ( bad move!!)

Now whenever i try to use Synaptic i get an error message which says " the package flashplayer-nonfree needs to be re-installed but I can't find an archive for it" 

How do I sort this mess out?

---

### Post by Iarwain ben-adar on 2006-11-05
Hi,
could you try to right-click on the deb,
and select 'remove' or something like that?

And then try to install via console..
```
sudo dpkg -i flashplayer9.deb
```

Or whatever your deb is called :D


Iarwain

---

### Post by lemmy999 on 2006-11-05
Right clicking on the .deb package doesn't give me the option of removing the app.

---

### Post by Iarwain ben-adar on 2006-11-05
Could you try to do this:
```
sudo apt-get remove flashplayer9
```

if the "remove" doesn't work, try "purge" ;)


Iarwain

---

### Post by lemmy999 on 2006-11-05
Still no joy

Terminal output is
> chris@chris-desktop:~$ sudo apt-get remove flashplayer9
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package flashplayer-nonfree needs to be reinstalled, but I can't find an archive for it.
chris@chris-desktop:~$ sudo apt-get remove flashplayer-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package flashplayer-nonfree needs to be reinstalled, but I can't find an archive for it.
chris@chris-desktop:~$ 


---

### Post by Iarwain ben-adar on 2006-11-06
Have you enabled the multiverse repo's?


Iarwain

---

### Post by towsonu2003 on 2006-11-06
> **lemmy999 said:**
> Tried installing a .deb for the latest flashplayer9 using Gdebi. Halfway thru the install stopped completely. In the terminal i could see that i needed to agree the eula. I couldn't navigate there to agree so I aborted the install ( bad move!!)

Now whenever i try to use Synaptic i get an error message which says " the package flashplayer-nonfree needs to be re-installed but I can't find an archive for it" 

How do I sort this mess out?

Put the .deb package you tried to install to your desktop. Then ```
cd ~/Desktop
sudo dpkg -i flashplayer-nonfree*
```

if that doesn't work, try ```
sudo dpkg -r flashplayer-nonfree
``` Let us know if it fixes things :)

PS. The OP tried to install a .deb package in a local storage device. S/he did not use any repositories (as far as I can see from her/his post). That's why apt-get is giving the error "I can't find that package". 

PSS. There is also another way to install flashplayer, which consists of just copying and pasting 1 or 2 files. The flash site should have the info on that method.

---

### Post by Iarwain ben-adar on 2006-11-06
Whoops,
thanks for the info :D

I thought apt was trying to install a package from the internet aswell :?


Iarwain

---

### Post by lemmy999 on 2006-11-06
thanks

I'll try that when i get home and report back

---

### Post by lemmy999 on 2006-11-06
Tried ```
sudo dpkg -r flashplayer-nonfree
``` but still getting the following message when I try to use Synaptic

---

### Post by pitkali on 2006-11-06
Perhaps something like ```
sudo apt-get -f remove
``` would help?

---

### Post by lemmy999 on 2006-11-06
Hmm still getting the same message. Seems like I can't do anything to get rid of this issue. maybe time for a re-install?

Output is 
```
chris@chris-desktop:~$ sudo apt-get -f remove flashplayer-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package flashplayer-nonfree needs to be reinstalled, but I can't find an archive for it.
chris@chris-desktop:~$ 

```

---

### Post by towsonu2003 on 2006-11-06
find your .deb package you tried to install. Do *not* rename it. I'll call it x.deb Do:
```

sudo cp /path/to/x.deb /var/cache/apt/archives/
sudo apt-get -f install
```

/var/cache/apt/archives/ is where apt keeps the packages it downloads for installation. This will trick apt to think that it already downloaded the broken package.

---

### Post by lemmy999 on 2006-11-06
Main problem now is that I cannot find the .deb file at all!

 Any suggestions please?

---

### Post by towsonu2003 on 2006-11-06
> **lemmy999 said:**
> Main problem now is that I cannot find the .deb file at all!

 Any suggestions please?

if you didn't delete the deb file:
```

sudo updatedb
locate flashplayer | grep deb
``` this should give you where it is...

Don't use this part
> I found one here, but it's for Dapper: [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu1_i386.deb)

I'm not sure if it will fix things if you're using Breezy, or make things even worse...

---

### Post by lemmy999 on 2006-11-06
Tried that, still a negative

```
chris@chris-desktop:~$ sudo updatedb
Password:
chris@chris-desktop:~$ locate flashplayer | grep deb
chris@chris-desktop:~$ 

```

I don't think I deleted the origianl .deb file.

I know where I downloaded the .deb from. Does that help here?

---

### Post by towsonu2003 on 2006-11-06
this one hopefully:
```
sudo dpkg --force-remove-reinstreq --purge flashplayer-nonfree
```

Reference: [http://www.linuxquestions.org/questions/showthread.php?t=485289](http://www.linuxquestions.org/questions/showthread.php?t=485289)

---

### Post by lemmy999 on 2006-11-06
@ towsonu2003

Thanks mate! That seems to have done the trick!:D

---

### Post by towsonu2003 on 2006-11-06
> **lemmy999 said:**
> @ towsonu2003

Thanks mate! That seems to have done the trick!:D

great to hear. I was getting worried :)

---

### Post by dosed150 on 2006-12-09
i had this problem i did what was recommended in this thread but now i have a different error messege "E: The package index files are corrupted. No Filename: field for package app-install-data-commercial.
E: Unable to lock the download directory"

---

