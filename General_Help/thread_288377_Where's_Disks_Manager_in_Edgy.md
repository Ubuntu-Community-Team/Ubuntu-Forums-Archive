---
title: "Where's Disks Manager in Edgy?"
date: 2006-10-29
forum: General Help
---

### Post by jsladek on 2006-10-29
I upgraded to Edgy (actually did new install because upgrading really blew VMPlayer big-time) and I don't see "Disks" available to enable/disable my FAT32/NTFS drives.  Any decent substitute available?

---

### Post by kent41 on 2006-10-29
> **jsladek said:**
> I upgraded to Edgy (actually did new install because upgrading really blew VMPlayer big-time) and I don't see "Disks" available to enable/disable my FAT32/NTFS drives.  Any decent substitute available?

I am not sure but I think it has been replaced with 

Applications>Accessories>Disk Usage Analyser 

and I might add not a very good one.

---

### Post by rado_london on 2006-10-29
> **kent41 said:**
> I am not sure but I think it has been replaced with 

Applications>Accessories>Disk Usage Analyser 

and I might add not a very good one.

AFAIK this only shows the usage of the HDD.
However I might be wrong.

---

### Post by canadianwriterman on 2006-10-29
The Disk Usage Analyzer is Boabab, which reads the directory structure on a disk and shows the usage. Try installing pyGTK through Synaptic. It installs a program called Storage Device Manager under System > Administration. It actually does more than the old Disks utility.

---

### Post by johnny9794 on 2006-10-29
> **jsladek said:**
> I upgraded to Edgy (actually did new install because upgrading really blew VMPlayer big-time) and I don't see "Disks" available to enable/disable my FAT32/NTFS drives.  Any decent substitute available?



[http://ubuntuforums.org/showthread.php?t=285279](http://ubuntuforums.org/showthread.php?t=285279)

---

### Post by jsladek on 2006-10-30
Many thanks for the responses ... the trail marked by johnny9794 looks like the way to go.  Disk Usage Analyser is definitely not the solution.  <grin>

Consider this issue closed.

---

### Post by nobar on 2006-11-01
> **canadianwriterman said:**
> Try installing pyGTK through Synaptic. It installs a program called Storage Device Manager under System > Administration.
I think he meant to say "pysdm".

---

### Post by BLTicklemonster on 2006-11-01
pysdm is in synaptic, you run it with sudo, and it's better than disks was in dapper if you ask me. you just mount a partition and be done with it. paths it for you and everything.

---

### Post by nobar on 2006-11-02
> **jsladek said:**
> Any decent substitute available?

A quick summary of the threads I have found on this issue:

**System->Administration->Disks** was removed by the GNOME people (this change was inherited by Ubuntu) (AFAICT).  Basically, the reason it was removed was because it hasn't been kept up-to-date with the latest GNOME development libraries/practices.  There were some other rumblings that the utility wasn't very important and also that it was buggy.  This utility was called **disks-admin** from the command-line.

Programs that might replace the functionality of **disks-admin**:

- **gparted** also called **GNOME Partition Editor**: This appears to be a very nice utility for managing disks, partitions, and formatting.  However, it lacks the ability to mount (it can, however, unmount).

- **pysdm** also called **Graphical Storage Device Manager**: I'm not sure that the overall quality of this application was up to Ubuntu levels but this utility does allow you to mount your existing partitions.

Both of these applications install themselves in the **System->Administration** menu when installed via Synaptic.

Final note: There were quite a few mentions of this issue on the web -- A lot of people have missed the **Disks Manager**.  I don't think the issue can be considered "resolved" until the application is officially restored/replaced (if not as a default component, at least as an optional package).

---

### Post by vyruss on 2006-11-02
> **nobar said:**
> Final note: There were quite a few mentions of this issue on the web -- A lot of people have missed the **Disks Manager**.  I don't think the issue can be considered "resolved" until the application is officially restored/replaced (if not as a default component, at least as an optional package).

I just brought it up on the ubuntu-devel list. Let's hope somebody listens.

---

### Post by fragos on 2006-11-02
Install pysdm, its a GUI which superceeds the features of the now lost disk-admin.  To see the partitions it must be run as root as in "sudo pysdm"

---

### Post by vyruss on 2006-11-02
> **fragos said:**
> Install pysdm, its a GUI which superceeds the features of the now lost disk-admin.  To see the partitions it must be run as root as in "sudo pysdm"

I think the point of this thread is that something like that must be on the default install, right?

---

### Post by BLTicklemonster on 2006-11-02
> **vyruss said:**
> I think the point of this thread is that something like that must be on the default install, right?

Indeed, astute observation. PUT IT BACK!!! OR IN!!!

---

### Post by fragos on 2006-11-03
> **vyruss said:**
> I think the point of this thread is that something like that must be on the default install, right?

Right you are but having an stop gap answer before that happens gets the job done for now.

---

