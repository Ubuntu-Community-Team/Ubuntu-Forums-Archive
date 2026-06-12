---
title: "Need help with Gnumeric program, please"
date: 2015-07-10
forum: General Help
---

### Post by elvis6 on 2015-07-10
I was working on a Gnumeric spreadsheet, and I accidentally typed something over some important data in a cell.
I did not realize I had over-written this data, until after I saved the document.
So, is there an option in Gnumeric, to revert to a version of the document, immediately prior to the most recently saved version of it ?

Thanks

---

### Post by tgalati4 on 2015-07-10
There is an "undo" command (Control-Z) but the buffer that holds the commands gets cleared after saving the file.  There is an autosave feature that can be set to 15 seconds (or whatever value), but there is no version saving, so that you have multiple versions (and backups) of the file that increment each time you save it.

You could try *photorec* and try to recover all *.gnumeric files.  You may get lucky and retrieve an older version that was deleted then you can examine the data and try to repair it.

```
sudo apt-get install testdisk
man photorec
```

---

### Post by elvis6 on 2015-07-11
> **tgalati4 said:**
> You could try *photorec* and try to recover all *.gnumeric files.  You may get lucky and retrieve an older version that was deleted then you can examine the data and try to repair it.

```
sudo apt-get install testdisk
man photorec
```

I try to enter those commands in the terminal, and then it asks for my sudo password. And it keeps telling me the password is incorrect and
I can't figure out why. I'm using the same password I've always used, I'm 100% certain I am carefully and slowly typing it in correctly, and my Caps are not on. I have no trouble signing into my Desktop as a User, with this password. And it should be the same password. I've never had this problem with the Terminal, and I've never changed my password. What could be causing this ?

I searched how to reset my sudo password, and the only instructions I found are for Ubuntu, and not the Xubuntu version I have.
The instructions say to reboot and go into recovery mode, then drop to root shell prompt, etc.
That works with Ubuntu, but I do not get those options when I am in Xubuntu.

---

### Post by tgalati4 on 2015-07-11
Hit the escape key when you boot.  A grub2 menu should come up and that allows you to boot into a root/rescue shell.  It's possible to change your password as a User, but it's also possible that your User does not have root privileges.

It might look something like:

> tgalati4@Mint17 ~ $ groups
tgalati4 adm dialout cdrom **sudo** dip plugdev lpadmin sambashare

---

### Post by elvis6 on 2015-07-14
> **tgalati4 said:**
> Hit the escape key when you boot.  A grub2 menu should come up and that allows you to boot into a root/rescue shell.  It's possible to change your password as a User, but it's also possible that your User does not have root privileges.

Thanks for the follow-up.
When I go into root, I get this prompt
root@(my username)-T3990:~#

Do I just type in those commands you gave, verbatim, and just substitute my username for yours ?
And are they separate commands, since they are on different lines, or do they all get typed in at once ?

---

### Post by tgalati4 on 2015-07-14
Each line is a separate command.

---

### Post by elvis6 on 2015-07-16
> **tgalati4 said:**
> Each line is a separate command.

It is telling me that the following command you suggested is not valid :

tgalati4@Mint17 ~ $ groups

I entered it exactly as you have it there, with the only exception, I replaced "tgalati4" with my own user name.
What about "Mint17". Do I type that exactly as you have it, or is that another term that's exclusive to your computer system's ID ?

---

### Post by tgalati4 on 2015-07-16
Try:

```
groups
```

The other part is my username@machine_name and ~ (home) directory and command prompt ($).

---

### Post by elvis6 on 2015-07-28
Okay, I realized that the initial command you gave
```
sudo apt-get install testdisk
 man photorec"
```

was actually 2 separate commands. So when I was typing in separate commands, I began getting the error messages described after that.
When I typed it as separate commands, the "photorec" program installed correctly.
So now that it's installed, how exactly do I instruct it to recover a previous gnumeric file ?

---

### Post by tgalati4 on 2015-07-28
Try running it and follow the instructions.  Be sure to have a large USB stick or external hard drive to receive the recovered files.

```
photorec -d  /home/yourusername /dev/sda 
```

---

