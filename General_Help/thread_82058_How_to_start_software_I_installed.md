---
title: "How to start software I installed?"
date: 2005-10-25
forum: General Help
---

### Post by csscll on 2005-10-25
Hello, I have a machine that's not connected to the net, I installed ubuntu 5.10 on it, and then I wanted some more software so I went to the repositories and manually downloaded some packages. I also checked dependencies manually and I'm satisfied that I had all the packages I needed, whether already in breezy or additionally downloaded. 
I then went into the directory where all the packages were and did this 
dpkg -i *.deb

It took a little time but installed them all. 

Now, an example of some software I got was mc (midnight commander) - I have rebooted a couple of times and still when I type mc at command prompt it tells me mc not found. Same was for lyx - again not found though I know it's already installed as it shows when I do dpkg -l. 

How can I start the software I installed? 

Thanks.

---

### Post by bionnaki on 2005-10-25
why are you downloading like this? seems like a total headache to me.

learn how to use synpatic/apt-get.

---

### Post by csscll on 2005-10-25
[QUOTE=bionnaki]why are you downloading like this? seems like a total headache to me.

learn how to use synpatic/apt-get.[/QUOTE]

The machine is not connected to the net.

---

### Post by Beggar on 2005-10-25
Right, but apt-get doesnt have to download the deb file. you can get them, then copy them to /var/cache/apt/archives/, then run apt-get and it will find the deb files locally and wont try to download them. 


As for your problem, run `locate mc` on the command line to see where it is, then check to make sure that its in your path with `echo $PATH `. if its not the easiest way to add it is just *sudo ln -s /where/youfound/it/mc /usr/bin* .

---

### Post by Samuel on 2005-10-25
isnt the cdrom in the /etc/apt/sources.list file ?

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

if the file is on the cdrom then your should still be able to use synaptic or apt-get

maybe comment out the other repos then you wont get errors telling you that you cant download from them

synaptic will check all the dependencies and fix any broken packages and put the programs into the gnome menus, if they are not in the menu try typing the name into a terminal or into the run app (alt+F2)

there is also no need to reboot the machine, if the launchers dont shot in the menu type:   ```
killall gnome-panel
```  to refresh the panels

hope this is useful for you


** i just tried this to double check and installed alien and dependencies offline**

---

