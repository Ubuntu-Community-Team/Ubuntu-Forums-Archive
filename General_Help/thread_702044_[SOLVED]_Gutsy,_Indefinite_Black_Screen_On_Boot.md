---
title: "[SOLVED] Gutsy, Indefinite Black Screen On Boot"
date: 2008-02-19
forum: General Help
---

### Post by Scotier on 2008-02-19
After searching for some time for a way to solve this error I've come here.

I am running a Dell Inspiron 6400 Laptop with an Intel CPU and a Radeon 1400 graphics card.

I am running only Gutsy on it and up until recently had no problem like this, when I boot up the computer I get the grub screen that says. GRUB Loading stage 1.5. Grub Loadin, please wait... if I wait past this screen the computer goes to a black screen where nothing happens. If I hit Esc there it gives me the option of loading the kernel in recovery mode. Recovery mode stops at /dev/sda1 after a couple minutes.
It gives me this...


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
                (i.e., without -a or -p options)
fsck died with exit status 4
                                                                                                                   [fail]
*An automatic file systems check (fsck) of the root filesystem failed.
Amanual fsck must be performed, then the system restarted.
The fsck should be performed in a maintenance mode with the
root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL -D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found


I imagine there is some way to repair this seemingly corrupted file and chances are this is what is causing the computer to never boot up. Any help is greatly appreciated.

---

### Post by fowie on 2008-02-19
Boot off a live CD, go to Applications -> Accessories -> Terminal
```

sudo fdisk -l

```
find the partition in question (it should be the same as that error showed, we'll call it /dev/sda2
```

fsck /dev/sda2

```
post what happens if it doesn't work.

---

### Post by Scotier on 2008-02-20
That did it perfectly, thank you very much.

---

