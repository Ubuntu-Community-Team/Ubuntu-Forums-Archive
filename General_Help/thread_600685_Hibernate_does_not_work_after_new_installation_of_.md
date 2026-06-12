---
title: "Hibernate does not work after new installation of Feisty"
date: 2007-11-02
forum: General Help
---

### Post by Cariboo1938 on 2007-11-02
Hi, all:
Turning on, after ending the last session with "Hibernate", my computer does not boot completely.
I only see the BIOS boot and then I see the beginning of the "ubuntu boot splash" and stays that way for ever.
No reaction to the keyboard.
 
I have the package "hibernate 1.94-2" installed.

What I did so far to solve the issue:
I followed the instructions [HERE ]("http://ubuntuforums.org/showthread.php?t=287524")
(knowing that they are recommended for EDGY, but they were the only I found dealing with this issue)

1. edit the resume file located at /etc/initramfs-tools/conf.d/
2. change the RESUME=UUID line to RESUME=/dev/sda8, (partition sda8 is my swap partition) save+exit
3. Then issue the command -- sudo update-initramfs -c -k `uname -r`

How could I give more info to solve the issue? 
Please help!

---

### Post by balak on 2007-11-02
Please post the output of 'dmesg' command

---

### Post by Cariboo1938 on 2007-11-02
Balak, thanks for the reply,
here is the output of dmesg-command attached! (It's a txt-file)

---

### Post by Cariboo1938 on 2007-11-03
I just want to say hi to all,
and keep this thread going........8-[

EDIT:
Has any body an idea where to look  why 'Hibernate' don't work at my computer?

---

### Post by Cariboo1938 on 2007-11-04
I'm wondering who's computer with Feisty-amd64 can Hibernate? 
Maybe I can get some information what could possibly wrong with my installation.:(

---

### Post by Cariboo1938 on 2007-11-08
Bump!?

---

### Post by Cariboo1938 on 2007-11-10
Hello,
I'm waiting for somebody who has "hibernate" working!

---

### Post by Cariboo1938 on 2007-11-14
What kind of additional Info should I post here for this issue?
Please help!:(

---

### Post by Cariboo1938 on 2007-11-21
I just can't get it (hibernate) working.
Maybe there is HELP, some kind of, out there?:confused:

---

### Post by Cariboo1938 on 2007-11-25
No Help for the 'Hibernate' issue????

---

