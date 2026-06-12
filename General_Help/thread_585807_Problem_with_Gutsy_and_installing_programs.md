---
title: "Problem with Gutsy and installing programs"
date: 2007-10-21
forum: General Help
---

### Post by Elf on horseback on 2007-10-21
I downloaded Gutsy and did a fresh install yesterday.  Thought I would not have upgrade problems that way.  Turns out I have the following problems, I think they are due to the same issue what ever that may be.

I start Add/Remove fine, the problem comes from when I click on a program to install.  

```
The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 
```

When I click reload I download a new list and then it happens all over again.  

When I go over to Synaptic Manager the problem there is that it will only list the packages I have installed already.  A search for a installable program will come up blank.

How can I fix this or do I just sit around with a crippled version of Ubuntu till they issue a update?

---

### Post by reddeth on 2007-10-21
I've been having the exact same problem, I attempted to re-install Synaptic via the packages.ubuntu.com site, but it didn't work. If anyone knows of a fix it would be greatly appreciated!!!

As a temporary fix you can update and install programs via the packages.ubuntu.com site, but thats a little annoying to have to go through.

On another note, I'm having trouble with apt-get as well, any time I try to download something it always returns "Couldn't find package <package name>" (replacing <package name> with the name of what I want to install), Thunderbird, Amarok, none of the apps that have worked in previous Ubuntu installations is working, possibly related? Maybe the sources file is off or something of that nature?

<edit>
Ok, I think I fixed the problem, it appears none of the repositories were enabled (not sure why), via Synaptic:
Click Settings, then Repositories
Go through the tabs and check the boxes you want enabled (I pretty much did all of them)
Hit close when done
Hit the reload button, or via the terminal type in "sudo apt-get update"

That fixed it for me, now apt-get works, synaptic works, Adept works, etc etc.

---

