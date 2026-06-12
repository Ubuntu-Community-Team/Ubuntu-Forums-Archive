---
title: "[SOLVED] Help w/ install google earth"
date: 2007-02-19
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2007-02-19
Hi every one! As recommended from forum here, this morning I installed another 256 stick of RAM (total of 384 now) I am having problem installing google earth. Is there not a .deb file for this? Also, how can I make wine desktop window larger? BTW: Google Earth .exe file works excellent with wine :) Thanks, Sally

---

### Post by frodon on 2007-02-19
You can use the Medibuntu repository, it contains google-earth, sorry but it's in french :
[http://blog.racoon97.net/index.php?2006/12/11/70-les-plf-sont-morts-vive-medibuntu](http://blog.racoon97.net/index.php?2006/12/11/70-les-plf-sont-morts-vive-medibuntu)

You just need to add the repository and the key then you can install google-earth through synaptic.

---

### Post by taurus on 2007-02-19
Or just download the GoogleEarth.bin and install it by hand with

```
cd ~/Desktop
chmod 755 GoogleEarth.bin
./GoogleEarth.bin
```

---

### Post by IusedTObeSOMEONEelse on 2007-02-19
> **frodon said:**
> You can use the Medibuntu repository, it contains google-earth, sorry but it's in french :
[http://blog.racoon97.net/index.php?2006/12/11/70-les-plf-sont-morts-vive-medibuntu](http://blog.racoon97.net/index.php?2006/12/11/70-les-plf-sont-morts-vive-medibuntu)

You just need to add the repository and the key then you can install google-earth through synaptic.

Thanks for reply. I have installed that already on my Xbuntu. Where do I find medibutu on my machine. Sorry for the dumb question, Sally

---

### Post by frodon on 2007-02-19
Medibuntu is just a repository, so you just need to add the repository in your source.list file to enable it however your profile says that you are running feisty fawn and i'm not sure that the medibutu repository has a feisty branch so you would better use the taurus's method in this case.

---

### Post by IusedTObeSOMEONEelse on 2007-02-19
> **taurus said:**
> Or just download the GoogleEarth.bin and install it by hand with

```
cd ~/Desktop
chmod GoogleEarth.bin
./GoogleEarth.bin
```

Hello taurus, I am totally dumb::/Desktop$ chmod GoogleEarth.bin
chmod: missing operand after `GoogleEarth.bin'
Try `chmod --help' for more information.

---

### Post by taurus on 2007-02-19
Sorry.  Forgot the numbers.

```
chmod 755 GoogleeEarth.bin
```

---

### Post by jml on 2007-02-19
If all else fails, you can install an application called Automatix2.  Here is a link to their web site:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

This application essentially will run scripts on your system to automatically add capabilities to your computer that are not supportrd by Ubuntu out of thr box.  Things like the ability to play commercial DVD's, Flash and Real player, and Google Earth.

To start, go to the Automatix web site and download the application.  Once it is installed, a new icon will be available in your menu called Automatix, click on it and select the items you want to install.  One caution, Google Earth is really a resource hog, so if you don;t have a very fast computer, you may find that the application is a bit sluggish.  Good lick.

Joe

---

### Post by IusedTObeSOMEONEelse on 2007-02-19
> **taurus said:**
> Sorry.  Forgot the numbers.

```
chmod 755 GoogleeEarth.bin
```

~/Desktop$ chmod 755 GoogleeEarth.bin
chmod: cannot access `GoogleeEarth.bin': No such file or directory:: but when I check thunar file it's in there under desktop

---

### Post by taurus on 2007-02-19
> **jml said:**
> If all else fails, you can install an application called Automatix2.  Here is a link to their web site:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

This application essentially will run scripts on your system to automatically add capabilities to your computer that are not supportrd by Ubuntu out of thr box.  Things like the ability to play commercial DVD's, Flash and Real player, and Google Earth.

To start, go to the Automatix web site and download the application.  Once it is installed, a new icon will be available in your menu called Automatix, click on it and select the items you want to install.  One caution, Google Earth is really a resource hog, so if you don;t have a very fast computer, you may find that the application is a bit sluggish.  Good lick.

Joe

Yeah, but she is running Feisty.

---

### Post by taurus on 2007-02-19
> **MustangSallydd said:**
> ~/Desktop$ chmod 755 GoogleeEarth.bin
chmod: cannot access `GoogleeEarth.bin': No such file or directory:: but when I check thunar file it's in there under desktop

Okay, I really need to learn how to type.  I have an extra **e** in there!  ](*,) 

```
chmod 755 GoogleEarth.bin
```

---

### Post by IusedTObeSOMEONEelse on 2007-02-19
> **taurus said:**
> Okay, I really need to learn how to type.  I have an extra **e** in there!  ](*,) 

```
chmod 755 GoogleEarth.bin
```

Or I should learn how to read!! Any ways again::~/Desktop$ chmod 755 GoogleEarth.bin
chmod: cannot access `GoogleEarth.bin': No such file or directory

---

### Post by taurus on 2007-02-19
So I guess we are on a same boat now, eh!

What's the output of this command?

```
ls -la ~/desktop
```
Maybe you saved it to your $HOME instead of $HOME/Desktop!

---

### Post by LeslieL on 2007-02-19
You can get Google Earth installed easily by Automatix. It takes care of a lot of other stuff, too. Add  [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main to your sources list and you'll find Automatix available for installation via Synaptic. (I know there's a lot of discussion about Automatix's effectiveness on this and other forums, but I've never had any problems with it).

Disable the repository after you've installed what you need using it to avoid problems with conflicting updates later.

---

### Post by taurus on 2007-02-19
> **LeslieL said:**
> You can get Google Earth installed easily by Automatix. It takes care of a lot of other stuff, too. Add  [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main to your sources list and you'll find Automatix available for installation via Synaptic. (I know there's a lot of discussion about Automatix's effectiveness on this and other forums, but I've never had any problems with it).

Disable the repository after you've installed what you need using it to avoid problems with conflicting updates later.

Please look at #9 & #10.

---

### Post by IusedTObeSOMEONEelse on 2007-02-19
> **taurus said:**
> So I guess we are on a same boat now, eh!

What's the output of this command?

```
ls -la ~/desktop
```
Maybe you saved it to your $HOME instead of $HOME/Desktop!

~$ ls -la ~/desktop
ls: /home/sally/desktop: No such file or directory

---

### Post by taurus on 2007-02-19
Okay, I am out of here.  ](*,) 

```
ls -la ~/Desktop
```

---

### Post by IusedTObeSOMEONEelse on 2007-02-19
> **taurus said:**
> Okay, I am out of here.  ](*,) 

```
ls -la ~/Desktop
```

-rw-r--r--  1 sally sally 21607408 2007-02-19 10:57 GoogleEarthLinux(2).bin
-rw-r--r--  1 sally sally 21607408 2007-02-17 22:13 GoogleEarthLinux.bin

---

### Post by taurus on 2007-02-19
```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by IusedTObeSOMEONEelse on 2007-02-19
> **taurus said:**
> ```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```
ooh,  :)  thank you so much. Got it. Now please tell me how do I make wine desk top window larger?

---

