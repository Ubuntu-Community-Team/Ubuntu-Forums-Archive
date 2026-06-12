---
title: "Virtualbox problems"
date: 2007-10-10
forum: General Help
---

### Post by chadrlz on 2007-10-10
When I try to run the Virtualbox machine I get the following error.


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

  I have no clue what to do next and I really need this to work ASAP. If I can't get this to work I will have to dual boot or something else.

---

### Post by kyphi on 2007-10-10
In a terminal type:

```
sudo chmod 666 /dev/vboxdrv
```

then Ctrl+Alt+Backspace to restart X.

---

### Post by maybeway36 on 2007-10-10
Add yourself to the vboxusers group.

---

### Post by bodhi.zazen on 2007-10-10
> **maybeway36 said:**
> Add yourself to the vboxusers group.

+1

---

### Post by chadrlz on 2007-10-10
Ok I got that part down. I can now load my machine but I have a new problem. When XP setup runs  
I get a page fault in non paged area error. What could be the cause of this? More importantly how do I fix it?

---

### Post by chadrlz on 2007-10-12
I keep getting the above mentioned error. Guys I really need to fix this. Any help would be appreciated.

---

### Post by kyphi on 2007-10-12
I would allocate a bit more memory to your XP install.

Page faults are a sign of insufficient memory.

---

### Post by chadrlz on 2007-10-15
I tried allocating more memory. However the error persists. By the way my base system has 512.
I am almost ready to give dual-boot a try.

---

### Post by bodhi.zazen on 2007-10-15
> **chadrlz said:**
> I tried allocating more memory. However the error persists. By the way my base system has 512.
I am almost ready to give dual-boot a try.

Sounds like too little ram ... Dual booting is the way to go

---

### Post by de_valentin on 2007-10-20
I installed virtualbox as shown in this howto [http://ubuntuforums.org/showthread.php?t=433359&highlight=chmod+666+vbox](http://ubuntuforums.org/showthread.php?t=433359&highlight=chmod+666+vbox)
  
But everytime i want to start windows (XP) after a Ubuntu reboot i have to first open a terminal and type this line

sudo chmod 666 /dev/vboxdrv

Is there a way i can do this once and for all. Without this i will never get my wife to migrate to Ubuntu (not to difficult but to much work) 

I tried to add it to 'Sessions' but that doesn't seem to work.

By the way i use Gutsy

---

### Post by bodhi.zazen on 2007-10-20
> **de_valentin said:**
> I installed virtualbox as shown in this howto [http://ubuntuforums.org/showthread.php?t=433359&highlight=chmod+666+vbox](http://ubuntuforums.org/showthread.php?t=433359&highlight=chmod+666+vbox)
  
But everytime i want to start windows (XP) after a Ubuntu reboot i have to first open a terminal and type this line

sudo chmod 666 /dev/vboxdrv

Is there a way i can do this once and for all. Without this i will never get my wife to migrate to Ubuntu (not to difficult but to much work) 

I tried to add it to 'Sessions' but that doesn't seem to work.

By the way i use Gutsy

See this link : [http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices](http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices)

---

### Post by de_valentin on 2007-10-30
Sorry for the slow response but thanks that worked and i even learned a little

---

