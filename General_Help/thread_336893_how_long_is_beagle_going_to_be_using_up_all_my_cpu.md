---
title: "how long is beagle going to be using up all my cpu for?"
date: 2007-01-12
forum: General Help
---

### Post by Choad on 2007-01-12
im growing tired of it making my laptop fan change speeds all the time....

---

### Post by mvaniersel on 2007-01-12
run this from the command line to get an idea:

beagle-info  --status

---

### Post by mega on 2007-01-12
mine runs 24/7 I think it's broken

---

### Post by Choad on 2007-01-12
what the hell is going on now?

the cpu graph shows my cpu at ~20% each (dual core), yet in the process list (showing all processes) nothing is taking up much. grrrr

stupid bloaty software. i hate it

---

### Post by Choad on 2007-01-12
richard@richard-laptop:~$ sudo apt-get remove beagle*


job done

---

### Post by Choad on 2007-01-12
LOL

that was foolish

for some reason nautilus depends on some beagle packages, so i accidentally killed nautilus. ho hum.

---

### Post by mvaniersel on 2007-01-13
Yeah, it would have been safer to just remove beagled from your session startup list.

Beagle is a resource hog, but it is also very powerful app if your computer can spare the extra resources. I have it enabled on my desktop, but not on my laptop for that reason.

---

### Post by Choad on 2007-01-13
to be honest its just a perfect example of modular linux being teh awesomes

i mean no stability was lost by removing arguably one of the most core components to the desktop. i could re-insert it by installing the ubuntu-desktop meta package.

its all cool.

---

### Post by cfriedt on 2007-11-21
Ack... yeah, i hate beagle for being a CPU hog.... I run it on my laptop, and it completely ignores the option 'do not index while running on batteries' so I always have to manually kill it.

In my opinion, any app that doesn't do any real-time signal processing (audio,video,Xinput,etc), like beagle's indexer, should never use upwards of 20% of the CPU time slices. 

I hope they read some of these posts (gawd knows there are probably thousands on this topic) and do something about it.

---

### Post by dbera on 2007-11-21
> **cfriedt said:**
> Ack... yeah, i hate beagle for being a CPU hog.... I run it on my laptop, and it completely ignores the option 'do not index while running on batteries' so I always have to manually kill it.

What makes you think the option is ignored ? AFAIK, beagle pauses indexing as soon as the ac power goes down. You can do the following to check if beagle detected the switch:

$ grep "AC power to battery" ~/.beagle/Log/*

Also, beagle runs with as low as possible CPU priority. Unfortunately, if there is nothing else running, then the kernel is free to allocate more CPU cycles to beagle.

---

