---
title: "delete obsolotes entries on dpkg/apt-get database"
date: 2008-04-16
forum: General Help
---

### Post by Fenix-TX on 2008-04-16
I upgrade to hardy today, and i can see entries on adept that they are not anymore installables, so is there any way to clean database?

---

### Post by nicedude on 2008-04-16
hope this works for you and clears some obsolete junk off your system.

Two Commands For Cleanup Of Old Packages No Longer Needed
sudo apt-get clean              - cleans old .deb package files that were cached after installing them
sudo apt-get autoremove    - cleans old packages that are no longer needed due to the original                                                                                                                           
                                               program that required them being removed.

If you want to try to clean more you can install the following program to clean even more junk.

GTK-Orphan - A program you can install with the following command the use the next command to execute it after you have installed it. this cleans some more orphaned stuff to clear space.
sudo apt-get install gtkorphan            - to install
sudo gtkorphan                                   - to run it

If those don't clean what you wanted at least it will cleanup something for you :-)

---

### Post by Fenix-TX on 2008-04-17
I know those commands, but the problem is that i can see packages on database that are not installable, like kernel from gutsy, so i want to know how to delete those obsolotes entries. There are some others installed by me with checkinstall that i wanted to deleted too.

---

### Post by nicedude on 2008-04-17
If its old kernels you want to get rid of you can open Synaptic package manager and then search by name for "linux" the list that generates will have all your kernel's and kernel headers that have been installed over time so just mark the old ones for removal and press the green check mark that says apply and synaptic should take care of removing them for you, it's how I got rid of my old kernel and kernel headers so it wouldn't show up in the grub boot menu. Hope that does it.

---

### Post by Fenix-TX on 2008-04-18
I think that i have not explain well. There are some entries that i can't install because they are not installables now, so i can check those packages to install, because they are not installable over repositories, but they are on database (this is the reason why i see them). Take a look at these screenshot to know what i mean:

[[IMG]http://img168.imageshack.us/img168/2205/captura170dg3.th.png[/IMG]](http://img168.imageshack.us/my.php?image=captura170dg3.png)

[[IMG]http://img528.imageshack.us/img528/2336/captura171hr7.th.png[/IMG]](http://img528.imageshack.us/my.php?image=captura171hr7.png)


You can see what i mean, fglrx packages are not installables (they were installed on gutsy), and the same ocurrs with kernel-backports (in the screenshot). I want delete those entries from database, because they are not installables anymore! They are not installed and i can't neither install them. So is there any way to delete entries from database????

---

### Post by dcstar on 2008-04-18
> **Fenix-TX said:**
> 
..........
You can see what i mean, fglrx packages are not installables (they were installed on gutsy), and the same ocurrs with kernel-backports (in the screenshot). I want delete those entries from database, because they are not installables anymore! They are not installed and i can't neither install them. So is there any way to delete entries from database????

You may need to manually check your /etc/apt/sources.list file and remove any old Gutsy entries - then refresh your list.

---

### Post by Whoopie on 2008-04-18
The packages database is in /var/lib/dpkg/status.
You could edit it and remove the obsolete packages.

Best regards,
Whoopie

---

### Post by Fenix-TX on 2008-04-18
> **Whoopie said:**
> The packages database is in /var/lib/dpkg/status.
You could edit it and remove the obsolete packages.

Best regards,
Whoopie

Thanks! That's what i need!!!

---

