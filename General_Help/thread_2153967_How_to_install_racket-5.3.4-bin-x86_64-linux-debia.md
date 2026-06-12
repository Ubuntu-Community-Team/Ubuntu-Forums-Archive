---
title: "How to install racket-5.3.4-bin-x86_64-linux-debian-squeeze.sh"
date: 2013-06-13
forum: General Help
---

### Post by FMFCorpsman on 2013-06-13
I downloaded this as part of a free course in programming racket-5.3.4-bin-x86_64-linux-debian-squeeze.sh. How would I install it? Do I need to use a command line?

---

### Post by FMFCorpsman on 2013-06-13
Well I didn't use command line, but I went into the properties of the download and made it executable in permissions. I then had it install in /home since thats my biggest partition. I still don't get how I am actually supposed to launch the program. Would the launch executable be in the bin folder?

---

### Post by Bucky Ball on 2013-06-13
***Posts moved to own thread.***

Hello again. I have moved these as you will have much better chance of getting help with a descriptive title and a new thread rather than posting on an old thread 80+ posts deep and with a title that has nothing to do with what you're asking. Cheers. ;)

---

### Post by HiImTye on 2013-06-13
racket is in the repos, to install it```
 sudo apt-get install racket
```
if you need the newer version for some reason, you can add the ppa
```
sudo add-apt-repository ppa:plt/racket
sudo apt-get update
# -- if you didn't yet install --
sudo apt-get install racket
# -- if you already installed --
sudo apt-get dist-upgrade -y

```
PPA info can be found here
[https://launchpad.net/~plt/+archive/racket](https://launchpad.net/~plt/+archive/racket)

if you're going to install a new program, always try, in order,
repos » ppa » .deb » source
don't start at the last step ;)

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Bucky Ball on 2013-06-13
> **HiImTye said:**
> 

if you're going to install a new program, always try, in order,
repos » ppa » .deb » source
don't start at the last step ;)

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

+1

---

