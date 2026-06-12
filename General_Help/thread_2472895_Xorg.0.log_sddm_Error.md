---
title: "Xorg.0.log sddm Error"
date: 2022-03-16
forum: General Help
---

### Post by wyattwhiteeagle on 2022-03-16
> [    37.976] (EE) Failed to open authorization file "/var/run/sddm/{3a850b44-2ec5-4046-8c70-f26b6b9548ad}": No such file or directory

If that file or directory actually does exist, as per the quote below...
Why is Xorg.0.log reporting that it doesn't exist?
How do I correct this?

This file and directory does exist...
> /var/run/sddm/{3a850b44-2ec5-4046-8c70-f26b6b9548ad}

---

### Post by guiverc on 2022-03-16
I would likely check the ownership & permissions first.

Here is mine

```

guiverc@d960-ubu2:~/uwn/issues/726$   stat /var/run/sddm/\{fcd2f13a-ef58-4260-8a54-f435c2ff07e7\} 
  File: /var/run/sddm/{fcd2f13a-ef58-4260-8a54-f435c2ff07e7}
  Size: 54              Blocks: 8          IO Block: 4096   regular file
Device: 18h/24d Inode: 2397        Links: 1
Access: (0600/-rw-------)  Uid: (  131/    sddm)   Gid: (  139/    sddm)
Access: 2022-03-06 10:46:21.653173703 +1100
Modify: 2022-03-06 10:45:59.569234298 +1100
Change: 2022-03-06 10:46:17.441148169 +1100
 Birth: -

```

I've a QA-test install occurring now, if I have time (*tonight*), I'll have a play and use that box to look and see if I can see if I can work out your issue.

---

### Post by wyattwhiteeagle on 2022-03-16
> **guiverc said:**
> I would likely check the ownership & permissions first.

Here is mine

```

guiverc@d960-ubu2:~/uwn/issues/726$   stat /var/run/sddm/\{fcd2f13a-ef58-4260-8a54-f435c2ff07e7\} 
  File: /var/run/sddm/{fcd2f13a-ef58-4260-8a54-f435c2ff07e7}
  Size: 54              Blocks: 8          IO Block: 4096   regular file
Device: 18h/24d Inode: 2397        Links: 1
Access: (0600/-rw-------)  Uid: (  131/    sddm)   Gid: (  139/    sddm)
Access: 2022-03-06 10:46:21.653173703 +1100
Modify: 2022-03-06 10:45:59.569234298 +1100
Change: 2022-03-06 10:46:17.441148169 +1100
 Birth: -

```

I've a QA-test install occurring now, if I have time (*tonight*), I'll have a play and use that box to look and see if I can see if I can work out your issue.

Ownership is "Owner and Group...sddm"
Owner is Read and write
Forbidden to all else
Not an executable file

May I please have the terminal command line you used to get your output?

```
wyatt@wyatt-latitudee5400:~$    stat /var/run/sddm/\{fcd2f13a-ef58-4260-8a54-f435c2ff07e7\}
stat: cannot stat '/var/run/sddm/{fcd2f13a-ef58-4260-8a54-f435c2ff07e7}': No such file or directory
wyatt@wyatt-latitudee5400:~$   stat /var/run/sddm/\{fcd2f13a-ef58-4260-8a54-f435c2ff07e7\}
stat: cannot stat '/var/run/sddm/{fcd2f13a-ef58-4260-8a54-f435c2ff07e7}': No such file or directory
wyatt@wyatt-latitudee5400:~$  stat /var/run/sddm/\{fcd2f13a-ef58-4260-8a54-f435c2ff07e7\}
stat: cannot stat '/var/run/sddm/{fcd2f13a-ef58-4260-8a54-f435c2ff07e7}': No such file or directory
wyatt@wyatt-latitudee5400:~$ stat /var/run/sddm/\{fcd2f13a-ef58-4260-8a54-f435c2ff07e7\}
stat: cannot stat '/var/run/sddm/{fcd2f13a-ef58-4260-8a54-f435c2ff07e7}': No such file or directory
wyatt@wyatt-latitudee5400:~$ 

```

---

### Post by guiverc on 2022-03-16
You got the correct command; 

```
stat /var/run/sddm/
```

then I used TAB to *autocomplete* the rest of the name... *I sure wasn't going to type it*.

The filename is just a random filename created at install time & is of no consequence, except to your|my box. Your random file will of course differ to mine (*just use TAB to autocomplete as I did*)

---

### Post by wyattwhiteeagle on 2022-03-16
> **guiverc said:**
> You got the correct command; 

```
stat /var/run/sddm/
```

then I used TAB to *autocomplete* the rest of the name... *I sure wasn't going to type it*.

The filename is just a random filename created at install time & is of no consequence, except to your|my box. Your random file will of course differ to mine (*just use TAB to autocomplete as I did*)

Ah...i got it
the way I had it before is there were 2 extra \ in the file name which returned "no such file or directory...

```
wyatt@wyatt-latitudee5400:~$ stat /var/run/sddm/{d5b2af9e-0be4-4524-b5c4-2454d8060fa0}
  File: /var/run/sddm/{d5b2af9e-0be4-4524-b5c4-2454d8060fa0}
  Size: 64              Blocks: 8          IO Block: 4096   regular file
Device: 18h/24d Inode: 1386        Links: 1
Access: (0600/-rw-------)  Uid: (  119/    sddm)   Gid: (  125/    sddm)
Access: 2022-03-16 12:34:47.155201125 -0400
Modify: 2022-03-16 12:34:45.323192040 -0400
Change: 2022-03-16 12:34:45.323192040 -0400
 Birth: -
wyatt@wyatt-latitudee5400:~$ 

```

---

