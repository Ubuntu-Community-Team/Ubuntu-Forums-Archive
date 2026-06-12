---
title: "can't install pipelight"
date: 2013-10-08
forum: General Help
---

### Post by Kojak Peg on 2013-10-08
Hi Everyone
I've been looking for a solution to silverlight. Moonlight doesn't seem to exist anymore, but if I've understood it correctly Pipelight could offer the solution I'm looking for. So I tried to install pipelight in the terminal but failed, and I don't know what the fix is

I found the command line code online:
 
sudo apt-add-repository ppa:ehoover/compholio
sudo apt-add-repository ppa:mqchael/pipelight
sudo apt-get update
sudo apt-get install pipelight(it's the same code on every website I checked)

I copied and pasted the first line, and got this error message 

> p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryYou are about to add the following PPA to your system:
 
 More info: [https://launchpad.net/~ehoover/+archive/compholio](https://launchpad.net/~ehoover/+archive/compholio)
Press [ENTER] to continue or ctrl-c to cancel adding it

I tried the next line just in case and got the same massage. I've also look on the developers site and achwiki but am too much of a novice to make head or tail of it. So could you spell it out to me as you would a small child

Thanks

---

### Post by oldos2er on 2013-10-09
Try installing the missing package: ```
sudo apt-get update && sudo apt-get install libp11-kit-gnome-keyring
```

---

### Post by Kojak Peg on 2013-10-09
Thanks 
I'm a relative linux novice as I'm sure you've guessed but give me a command line I can copy and paste and I'm an old pro, lol

I'll let you know how it turns out

update 
a lot of stuff just happened and at the end of it I got this message 

> Package libp11-kit-gnome-keyring is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libp11-kit-gnome-keyring' has no installation candidate

and I just tired installing pipelight just in case but still got the other error message

---

### Post by oldos2er on 2013-10-09
Which version of Ubuntu are you running? Can you run the following command and copy/paste all the output here? ```
cat /etc/apt/sources.list
```

---

### Post by Kojak Peg on 2013-10-13
I've just had to reinstall my os. I was using zorin but I've changed to ubuntu 12.04. So I'll start from the beginning and see how I get on with it. Hopefully it'll work this time. Either way thank you for all your help. I'll leave this unsolved for the moment

---

### Post by b6Q8Ats on 2013-10-13
Hi Koak,
goto the multimedia sub forum see post started by Kols (19 july).
It works a treat, no sudo required

Roy:KS

---

### Post by philinux on 2013-10-16
There's a new version out now too with multi plugin support.

[http://www.webupd8.org/2013/10/pipelight-020-released-with-multi.html](http://www.webupd8.org/2013/10/pipelight-020-released-with-multi.html)

---

