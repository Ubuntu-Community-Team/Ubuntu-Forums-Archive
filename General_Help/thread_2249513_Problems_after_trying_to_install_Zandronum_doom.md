---
title: "Problems after trying to install Zandronum doom"
date: 2014-10-22
forum: General Help
---

### Post by mahydraal on 2014-10-22
Hello to everyone here in the Linux community!):P I recently used the zandronum wiki command list for the package install of the zandronum engine . After running the first two commands, I attempted to "sudo apt-get update" and found the following error: 
"E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)E: The list of sources could not be read."
these are the lines from 53-58
-------------------------------------------------------------------------------------
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb [http://debian.drteam.org/stable](http://debian.drteam.org/stable) multiverse
# deb-src [http://debian.drteam.org/stable](http://debian.drteam.org/stable) multiverse
-----------------------------------------------------------------------------------------
I am uncertain where to go from here, and am fairly new to ubuntu (zorin in my case)(less than 2 years experience with linux in general)
please assist or point me towards a thread of the same topic...i have seen many line error correction threads, but none for my specific isntance.
also, any zandronum users here, I used the Linux install link on the zandronum website and was uncertain what to do with the files it gave after i extracted them....if any of you might offer assistance, i would deeply appreciate it. 

link to zandronum site:
[http://zandronum.com/download](http://zandronum.com/download)




Thanks in advance! I am really loving linux so far, there is simply much learning i have left to do.;)

---

### Post by yancek on 2014-10-22
The Zandronum site shows the following to be added to the /etc/apt/sources.list

> deb [http://debian.drdteam.org/](http://debian.drdteam.org/) stable multiverse

You don't have a space before stable, is that a typo in your post?  That would be line 57 per your post.

---

### Post by mahydraal on 2014-10-23
Thanks for the quick response time!
Those lines are directly copied and pasted from the error log.
I have fixed my synaptic package manager now, by commenting out line 57, but I am uncertain if that will bite me later, when I start adding the extra packages you mentioned in your post.

---

### Post by yancek on 2014-10-23
> when I start adding the extra packages you mentioned in your post. 

I didn't mention any extra package, just indicated that you needed a space in your sources.list where you had none. On the website, the entry is as in my post above and there is a space before the word stable.   Are you referring to packages from their web site?

---

### Post by mahydraal on 2014-10-28
yes sir, i was indeed.
apologies for the long response time.

Anywho, i have corrected the issue by removing that line entirely, as it was a repeat of line 34 in the sources.list file. Zandronum now works just as intended, and my synaptic package manager is running smoothly as before, thanks for the quick response, but i was able to fix the issue with a bit more fiddling.

:)

once more, thank you and apologies for taking so long to update.

With a deranged smile, Mahydraal

---

