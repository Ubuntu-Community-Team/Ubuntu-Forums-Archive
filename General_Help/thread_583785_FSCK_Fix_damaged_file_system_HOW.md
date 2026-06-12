---
title: "FSCK Fix damaged file system HOW???"
date: 2007-10-20
forum: General Help
---

### Post by Guardian-Mage on 2007-10-20
Everytime I start up Ubuntu 7.10, it stops half way throught, FSCK comes up with a damaged file system, please fix manually message and puts me in a maintence shell. Then I have to press <Control> + D to continue booting normally. How can I fix this error. It is in /dev/sda2 my external USB hard drive which is configured with the mount-point /home

---

### Post by dcstar on 2007-10-20
> **Guardian-Mage said:**
> Everytime I start up Ubuntu 7.10, it stops half way throught, FSCK comes up with a damaged file system, please fix manually message and puts me in a maintence shell. Then I have to press <Control> + D to continue booting normally. How can I fix this error. It is in /dev/sda2 my external USB hard drive which is configured with the mount-point /home

```
sudo umount /dev/sda2
sudo fsck -y /dev/sda2
sudo init 6
```

---

### Post by Guardian-Mage on 2007-10-20
unmounting the drive fails, the drive is mounted as /home and home is busy. That is when I try it after the desktop boots up. Should I try that in the maintenance shell??

---

### Post by mdurham on 2007-10-20
Is it wise to unmount a home partition whilst it's in use?

---

### Post by mdurham on 2007-10-20
> **Guardian-Mage said:**
> unmounting the drive fails, the drive is mounted as /home and home is busy. That is when I try it after the desktop boots up. Should I try that in the maintenance shell??

Log in as 'root' and do it from there.

---

### Post by jrharvey on 2007-10-20
I am having this same problem in fiesty after installing gutsy on a seperate partition. I have no clue what is wrong.

---

### Post by dbdbrooks on 2007-10-20
Uh, that happened to me immediately after I upgraded too.  If you read the fsck prompt there, it says to enter your root password and then run fsck manually or press control-D to continue.  If you do control-d it doesn't do the fsck.  

So enter your root password and do the other stuff it says to do.

Misleading prompt, kinda.

---

### Post by jrharvey on 2007-10-20
the thing is it doesnt tell me to do anything after entering my root password. It only says 

"The program apt-get "is currently not installed. You can install it by typing apt-get install apt"

---

### Post by dcstar on 2007-10-20
> **jrharvey said:**
> the thing is it doesnt tell me to do anything after entering my root password. It only says 

"The program apt-get "is currently not installed. You can install it by typing apt-get install apt"

Hit <Enter> and see if you get a "#" prompt, if so then follow the instructions.

---

### Post by jrharvey on 2007-10-20
ok i went back and hit enter and it did the same thing

---

### Post by dcstar on 2007-10-20
> **jrharvey said:**
> ok i went back and hit enter and it did the same thing

Try booting "normally" and checking that it is installed, this is a very weird message!

---

### Post by Guardian-Mage on 2007-10-21
I got it.
Boot up ubuntu until you get the fsck message and it goes in to the maintenance shell. I didn't have to enter a password, it should come up like this
root@brandon-desktop~#

now type 'umount /dev/sda2' (No Quotes) and replace sda2 with the damaged partition(EX:hda1). For me this was useless but do in just in case

now type 'fsck -y /dev/sda2'  (No Quotes) and replace sda2 with the damaged partition(EX:hda1).

then wait for it to finish and return to the prompt. After that press <Control> + D and your done

---

### Post by ravanwin on 2007-12-23
saw this because I think I am having a similar problem but am unsure how similar. I am quite a beginer so any help would be best in plain plain speak.


SO - tried to make a folder on my desktop and my computer told me it was "read only." that was odd.

so, i restarted it:

Not sure what is going on here. i recently put some new photos on the computer and may have over stretched the hard drive space but i thought i had 4 - 5 gigs and added no more than two.

Anyone have thoughts or ideas? please help.

below are the transcribed details.
happy holidays!

amongst other things here is what it says:

UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

fsck died with exit status 4

An automatic file system check of the root filesystem failed. A manual fsck check must be preformed and then the system restarted. The dsck should be performed in maintenance mode with the root filesystem mounted in read only mode.

* the root filesystem is currently mounted in read only mode.
A maintenance shell will now be started.

bash: no job control in this shell
bash: groups: command not found
bash: the: command not found.

The program 'apt-get' is currently not installed. you can install it by typing: apt-get install apt

bash: apt-get: command not found
bash: dircolors: command not found
bash: the: command not found.

The program 'apt-get' is currently not installed. you can install it by typing: apt-get install apt

bash: apt-get: command not found

<and>

Not sure what is going on here. i recently put some new photos on the computer and may have over streatched the hard drive space but i thought i had 4 - 5 gigs and added no more than two.

Anyone have thoughts or ideas? please help.

---

### Post by nzadLithium on 2007-12-23
your root partition isnt mounted which is why it cant find apt-get.

find out what your root disk is then do
the fsck command they have been talking about on previous posts in this thread.

---

### Post by ravanwin on 2007-12-23
thanks nzad! i've been really stressed about this for the past hour! 

can i ask you to clarify before i mess something up:

I get this:

root@bang: 

does that mean my root is bang?

or  is it sda1 - from what i'm reading it seems that is where the error is but, like i said, i don't really speak the lingo.

Do you think i could do:

umount /dev/sda1

any way you could tell me how to find my root disk / damaged partition - i am unfortunately very helpless.

thanks a billion
ryan

---

### Post by ravanwin on 2007-12-23
I get this message quite a few times as Ubuntu attempts to start up which is why I guess sda1 is the problem ---

:::

buffer i/o error on device sda1, logical blox

---

### Post by malangaman on 2008-01-14
What  happened?
Did you correct the problem?

---

