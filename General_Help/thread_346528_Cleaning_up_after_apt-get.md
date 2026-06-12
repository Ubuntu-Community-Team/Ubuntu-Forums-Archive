---
title: "Cleaning up after apt-get"
date: 2007-01-25
forum: General Help
---

### Post by teejay17 on 2007-01-25
Okay, say I screwed up and downloaded more than one version of a piece of software, or that I didn't install something after doing an apt-get (or a wget, etc.) and now I want to get rid of it. 
How do I get rid of, or clean that stuff up so it's not taking up any space?
What is this process?
To be more specific, I did this more than once, accidentally:
> wget [http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb](http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb)
sudo dpkg -i frostwire-4.13.1.i586.deb

---

### Post by aysiu on 2007-01-25
```
sudo apt-get remove frostwire
```

---

### Post by teejay17 on 2007-01-26
> **aysiu said:**
> ```
sudo apt-get remove frostwire
```
Even though I didn't complete the whole installation? And I downloaded it more than once?

---

### Post by Rhubarb on 2007-01-26
You'll also need to do
```
rm frostwire-4.13.1.i586.deb
```
This deletes the file you downloaded by using the "wget" command.
(wget downloads a file from the internet and usually stores it in your home directory).

---

### Post by teejay17 on 2007-01-26
> **Rhubarb said:**
> You'll also need to do
```
rm frostwire-4.13.1.i586.deb
```This deletes the file you downloaded by using the "wget" command.
(wget downloads a file from the internet and usually stores it in your home directory).
Okay thanks. That's what I was wondering. I don't think I actually installed Frostwire, there was a glitch in the command that I copied and pasted or something, so I kept getting error E or whatever. So all I want to now is get rid of the 2 or 3 copies of Frostwire I've temporarily downloaded.

---

