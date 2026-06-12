---
title: "Synaptic Package Manager will not install in 16.04"
date: 2016-04-24
forum: General Help
---

### Post by jamesfbays on 2016-04-24
Synaptic is in the Ubuntu Software repository, but it will not install. At the moment I have a barred-out question mark on the side panel that says "Waiting To Install". Is there a way to install Synaptic in 16.04? Thanks...

---

### Post by oldrocker99 on 2016-04-24
I had no problem installing Synaptic in 16.04. Try```
sudo apt-get install synaptic
``` and let us know if it works and what (if any) error messages you are getting.

---

### Post by cariboo on 2016-04-24
Have you opened a terminal and tried:

```
sudo apt install -f
```

---

### Post by cimpianalin-2 on 2016-04-24
Why software center in 16.04 not working. I click install and it show me Pending, just that, click cancel ... nothing ... after i close the software center it wont open again, for 2 hours i try to find i solution to make it working, it show the apps but you can`t install them.
Damn! there is a bug!

---

### Post by jamesfbays on 2016-04-24
I did try 

```
sudo apt-get install synaptic
```

I got a message in the terminal that said something like "no such package". Maybe it was coincidence, but then Ubuntu Software itself stopped working, it went blank.

As for  

```
sudo apt install -f
```

At this point I am afraid to try it blind. Could you please tell me what it's supposed to do... I don't want to re-install my system... again...

---

### Post by troy-arthur on 2016-10-20
Have you tried to change the "Download form" to Main server in Software & Updates?. Sorry for my bad english

---

### Post by howefield on 2016-10-21
> **jamesfbays said:**
> I got a message in the terminal that said something like "no such package". Maybe it was coincidence, but then Ubuntu Software itself stopped working, it went blank.

That would usually indicate that you need to update your package sources or do not have the relevant repository available, but it is usually much better to copy/paste the whole terminal output so others can see exactly what you attempted and the outcome. Try

```
sudo apt update
```

then

```
sudo apt install synaptic
```

> At this point I am afraid to try it blind. Could you please tell me what it's supposed to do... I don't want to re-install my system... again...

Most commands will have a "man" page that you can consult for learning about options, eg,

```
man apt
``` 

will give you the man page for apt, or you can use the older but very relevant man apt-get..

> -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. If packages are specified, these have to completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations.

---

