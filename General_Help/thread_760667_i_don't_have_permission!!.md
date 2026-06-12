---
title: "i don't have permission?!!?"
date: 2008-04-20
forum: General Help
---

### Post by wildman4god on 2008-04-20
could someone please tell me why when ever i try to do something more advanced on my ubuntu 7.10 laptop why it keeps saying i don't have permission when i own the thing and installed the os myself, what do i need to do to give me full permissions to everything. and i have read other post with this same issue, but i don't want to do some crazy stuff with the command line i just what to have full permissions so i can do what i need to do, or at the very least be able to log in under a root account so i can change what ever i need some one please help.

---

### Post by PmDematagoda on 2008-04-20
You are given limited permissions both as a way of preventing faults by the user and to improve security in the face of malicious programs. This is because running as root all the time means that the OS is more susceptible for harm not only by malicious programs since they can easily access the entire system but also by the user him/herself where the user may do a particularly damaging edit or change which can break the entire system. 

Use root whenever it's necessary(i.e to install a package) and not when it's not necessary.

If you really have to take up root privileges then you may do so by entering:-
```
sudo -i
```
or by running Ubuntu in Recovery Mode.

---

### Post by ugm6hr on 2008-04-20
One of the simplest ways to resolve this for GUI users is to use nautilus with sudo permission.

You can add a launcher to the panel with the custom command:
```
gksudo nautilus /home/*username*
```

It will still ask for a password when opened, and will still provide the protection afforded by sudo whenever using Ubuntu under other circumastances.

---

### Post by conscious on 2008-04-20
You may be interested in this:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by konungursvia on 2008-04-20
You don't "have permission" to start your car without putting the key in. Linux is the same. MS Windows is more like a car whose doors and trunk cannot be locked and which you can start just by pressing a button where the ignition key should be. Or like an office building without RFID security passes and where anybody off the street could walk right in at any time.

Linux doesn't allow normal applications to alter the system significantly without getting your approval first. This is a good thing.

---

