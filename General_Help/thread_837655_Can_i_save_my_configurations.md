---
title: "Can i save my configurations?"
date: 2008-06-22
forum: General Help
---

### Post by chriskin on 2008-06-22
is there any way to save my configurations so that when i format my disk, they will stay intact?

for example
save my list of programms , my repositories, my changed grub menu so that when i reinstall ubuntu in some days, i will be able to make them all the same by a simple download?

the most possible answer is "no" but, come on now, everybody needs some hope :D

---

### Post by brian_p on 2008-06-22
> **chriskin said:**
> is there any way to save my configurations so that when i format my disk, they will stay intact?

for example
save my list of programms , . . . 

You'll like this:

[http://wiki.debian.org/Packaging/Listing_Installed_Packages](http://wiki.debian.org/Packaging/Listing_Installed_Packages)

>  . . . . my repositories, my changed grub menu so that when i reinstall ubuntu in some days, i will be able to make them all the same by a simple download?

Back up /etc and /var/cache/apt using rsync. Or just copy them somewhere safe. 

> the most possible answer is "no" but, come on now, everybody needs some hope :D

Pessimist.

---

### Post by chriskin on 2008-06-22
if this works as you said, and i think that it does, i will make a gold statue of you :D heheh
THANKS :D :D :D

---

### Post by brian_p on 2008-06-22
> **chriskin said:**
> if this works as you said, and i think that it does, i will make a gold statue of you :D heheh
THANKS :D :D :D

I've used the technique on the wiki successfully to reinstall packages to a base Debian system and then copy back saved files (saved with cp -a) to /etc and /var from another disk. Don't forget to save $HOME.

---

### Post by chriskin on 2008-06-22
i think i will be able to make it happen
:D

thank you once more :D

---

### Post by Vivaldi Gloria on 2008-06-22
Also have a look at

[http://ubuntuforums.org/showthread.php?t=792639](http://ubuntuforums.org/showthread.php?t=792639)

---

### Post by chriskin on 2008-06-22
seems good as well :D

some pop corn as a gift :P :popcorn:

---

### Post by drs305 on 2008-06-22
I think the following does the same thing as mentioned earlier but in a different way. It provides a list of installed packages and duplicates them on a new machine/fresh install. Note: It only installs the packages but not the current configuration files, which I think is what you really want.

Create a list of installed packages on your Desktop:
```

sudo dpkg --get-selections >~/Desktop/installed-pkgs

```

To install these packages on the new setup from a file on Desktop:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/installed-pkgs
sudo apt-get dselect-upgrade 

```

---

### Post by chriskin on 2008-06-22
you have all been very helpful
i will see to the whole thing first thing tomorrow morning :D
:guitar:

---

### Post by chriskin on 2008-06-23
> **drs305 said:**
> I think the following does the same thing as mentioned earlier but in a different way. It provides a list of installed packages and duplicates them on a new machine/fresh install. Note: It only installs the packages but not the current configuration files, which I think is what you really want.

Create a list of installed packages on your Desktop:
```

sudo dpkg --get-selections >~/Desktop/installed-pkgs

```

To install these packages on the new setup from a file on Desktop:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/installed-pkgs
sudo aptitude install dselect-upgrade

```

i had to make some changes to these commands but everything worked perfect, it downloaded about 3 gbs of applications and now my computer is full like before.

thank you

for the working commands, one has to do nothing else than search google
(editing after one year : sudo dpkg --set-selections < /tmp/dpkglist.txt  <--or whatever you named it in the command of get-selections
sudo apt-get -y update
sudo apt-get dselect-upgrade are the right commands, or at least were for me back then)

---

