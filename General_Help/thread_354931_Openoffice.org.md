---
title: "Openoffice.org"
date: 2007-02-06
forum: General Help
---

### Post by armoman301 on 2007-02-06
I have a major question.  I have just installed xubuntu on a Notebook w/ 192 MB ram.  I want to install Openoffice.org onto xubuntu b/c unlike the other distros, it doesnt come with the full OO suite.  Please help me on what i should download and how i should install it.

---

### Post by LotsOfPhil on 2007-02-06
Provided you meet the minimum requirements:
GNU/Linux ("Linux")

    * Linux kernel version 2.2.13 or higher, glibc2 version 2.2.0 or higher
    * 128 Mbytes RAM
    * 200 Mbytes available disk space
    * X-Server with 800 x 600 or higher resolution with at least 256 colours

Just type 
```
sudo apt-get install openoffice.org
```

---

### Post by armoman301 on 2007-02-06
Thanks....so what should i download?

---

### Post by meng on 2007-02-06
You make sure your notebook computer is connected to the internet, then open a terminal and type:
sudo aptitude install openoffice.org

and it will download and install for you.
(you could substitute apt-get for aptitude, but aptitude is cleaner when it comes to UNinstalling)

---

### Post by armoman301 on 2007-02-06
Thanks

---

### Post by viper on 2007-02-06
Just a note, Open Office will run slow on 192 mg ram, depending also on your processor speed. If you only need a Word processor you might consider Abiword, which is a nice alternative for an older system.

---

### Post by armoman301 on 2007-02-06
well, i need a word processor, a spreadsheet app., and possibly a presentation program

---

### Post by LotsOfPhil on 2007-02-07
I'd go with the openoffice then. Abiword is just a word processor. I think openoffice will run on your machine.

---

### Post by armoman301 on 2007-02-07
i did the sudo apt-get install openoffice.org

its missing resources!!! i cant install it, please help!

---

### Post by LotsOfPhil on 2007-02-07
Can you post the output from sudo apt-get install openoffice.org ? Do you have an internet connection?

Can you post /etc/apt/sources.list ?

---

### Post by armoman301 on 2007-02-07
well, first i tried it from the command line:

sudo apt-get install openoffice.org

and it says

the following packages have unmet dependancies

and then it lists all of the apps in openoffice.org.

the same w/ snaptic package manager and the command line.

---

### Post by LotsOfPhil on 2007-02-07
Type ```
sudo aptitude install openoffice.org
``` and post the output.

---

### Post by armoman301 on 2007-02-07
sure.  I dont have access to the laptop for another two days though, so please subscribe to this thread.  I will post the output once i do it.  I dont think that it'll work though because the synaptic software manager was not able to install it either, it gave me the same error messages

---

### Post by Topsiho on 2007-02-07
> **armoman301 said:**
> well, first i tried it from the command line:

sudo apt-get install openoffice.org

and it says

the following packages have unmet dependancies

and then it lists all of the apps in openoffice.org.

the same w/ snaptic package manager and the command line.


Dependencies are files that are needed to install, in this case, OpenOffice. If they are not present OpenOffice cannot be installed.
If there are just a few dependencies then you could install those first, and then install OpenOffice. But the fact that apt-get does not do this automatically means, I think, that the dependencies have their dependencies, and so on, which creates a quagmire.

So I think that in Xubuntu, having a lightweight desktop, the very heavyweight OpenOffice can not be installed. Sorry to say so.

You could consider Abiword, and possibly Gnumeric for a spreadsheet, though the latter may need the Gnome desktop, which you don't have.

In synaptic you could search for other, maybe lighterweight spreadsheets, and try that or those if you find some.

Success,

Topsiho

---

### Post by armoman301 on 2007-02-07
O.k thank you.  Well, abiword and gnumeric spreadsheet are already installed.  They work fine, but is there some sort of presentation program that i could use?

---

### Post by Topsiho on 2007-02-08
You could, as I just did, search in Synaptic for presentation programs. I did find some, which maybe you could try yourself.

I do not know Xubuntu, have no experience with it, but maybe you could find some information that you need on their website, if it exists.

The short of what I am saying is, why do you not try and find this information yourself?

A great way, except for this forum, which is indeed very ?ubuntu-specific, is to find more general information using Google, which usually is very effective.

Searching yourself the information you need, and if not successful, then ask for it, is way the best advice I am able to give you.

:)

Topsiho

---

### Post by armoman301 on 2007-02-08
I would really like OOo though, its very useful and more functional than anything else

---

### Post by Topsiho on 2007-02-10
> **armoman301 said:**
> I would really like OOo though, its very useful and more functional than anything else

Well, I understand this.
However: if your computer is too light for Ubuntu (Gnome desktop) or Kubuntu (KDE desktop) it is also too light for OpenOffice.

One thing you could do is extend the memory, preferably to more than 256MiB, and then install Ubuntu or Kubuntu, which come with OpenOffice automatically.

Using a laptop you should (especially) be careful what memory (extension) you buy for it, so you should get this from a good and reliable computer store.

I wish you success,

Topsiho

---

