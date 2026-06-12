---
title: "can you have two ubuntus installed"
date: 2007-06-07
forum: General Help
---

### Post by miketowninc on 2007-06-07
Hello
i have ubuntustudio and i work with a guy for 3 hours trying to get it fix and now it goes slow i wouldlike to install 
xubuntu can i have both installed?

thanks

---

### Post by esavato on 2007-06-07
You can have as many as you want installed.  You can even install different distros of Linux if you like.  The Linux Reality podcast has a great show on this topic...  [http://www.linuxreality.com](http://www.linuxreality.com)

---

### Post by floke on 2007-06-07
Yep, they'll just be added to the grub menu; will also share the same swap file space so no need to make new ones.

---

### Post by NeoLithium on 2007-06-07
```

sudo aptitude install xubuntu-desktop

```

It might take a bit iwth the files, but it will bring Xubuntu to you :)

---

### Post by ago on 2007-06-07
Yep , the best way is to install them from within Ubuntu.

Each desktop is available as a package and can be installed as a normal application. That's much more convenient. Among other things, you can change desktop by logging off and logging on as opposed to reboot each time.

The desktop selector in wubi is intended for people that already know what they want, but for trying/using many desktops at once use the ubuntu packages. You can edit menu.lst but that is a bit complicated and frankly not worth it.

---

### Post by miketowninc on 2007-06-08
> **ago said:**
> Yep , the best way is to install them from within Ubuntu.

Each desktop is available as a package and can be installed as a normal application. That's much more convenient. Among other things, you can change desktop by logging off and logging on as opposed to reboot each time.

The desktop selector in wubi is intended for people that already know what they want, but for trying/using many desktops at once use the ubuntu packages. You can edit menu.lst but that is a bit complicated and frankly not worth it.

so is sudo aptitude install xubuntu-desktop the best way to do it?  or do i download xubuntu and open it from ubuntustudio?

---

### Post by diatribe on 2007-06-08
sudo aptitude install xubuntu-desktop is the best way.

---

### Post by eentonig on 2007-06-08
As long as you stay within the same distro family (Ubuntu), the apt-get solution is the best.

If you want to try another distro (Fedora ie), you need to give it a seperate / mountpoint

---

### Post by donteatthefish on 2007-06-08
if i install it by sudo aptitude install ubuntu-desktop method, does it add it to the wubi boot menu?(using grub, but its not a normal version of grub its slightly different) or will i just be able to choose in the login screen?and since my home is only 10gb(wubi defualt), will i be able to make it bigger or anything? please someone explain this to me. i will only do this if i can make another 10gb file system.(i dont need the swap again)

i ask this because i have usually installed ubuntu 7.04, but this time i installed ubuntustudio 7.04(with wubi test2) and none of the programs got installed....(makes me mad) and i had so much set up and now i have to eaither download all of the programs indivually(even simple ones take a while to download, amorak, open office) i dont get why i dont have any of the programs... maybe it was wubi that didn't go through the usual setup(you can choose what programs to install)

under graphics all i have is "gthumb image viewer" and sound and video i have "movie player" and "sound recorder".... wtf this is supposed to be ubuntu STUDIO not UbuntuNoprograms

and i spent hours setting up other stuff(oblivion, warcraft 3 using wine, beryl, nvidia graphics card, automatixs, and others that take a while)

and by the way i did try to
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

it didn't do much


( *cry* no gimp)

---

### Post by ago on 2007-06-08
> **donteatthefish said:**
> if i install it by sudo aptitude install ubuntu-desktop method, does it add it to the wubi boot menu?
Nope you boot into Ubuntu, and at the login go into option > session and select the desktop you want

If you have a 10GB system virtual disk it will be more than enough for 3 or 4 desktop environments 

> i ask this because i have usually installed ubuntu 7.04, but this time i installed ubuntustudio 7.04(with wubi test2) and none of the programs got installed....
Ubuntu studio uses separate metapackages not just one, I think they are called ubuntustudio-audio, ubuntustudio-video... Plus you need to add it to the list of repositories.

---

### Post by runemaste644 on 2007-09-01
Yeah, thats what i do... with ubuntu, kubuntu, xubuntu, elbuntu, fluxbuntu, blackbox, openbox, afterstep, amiwm,..............................................
BTW, if you sudo aptitude install edubuntu-desktop, it will say edubuntu and KDE kinda takes over your system lol

---

