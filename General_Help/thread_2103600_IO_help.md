---
title: "I/O help?"
date: 2013-01-10
forum: General Help
---

### Post by TriplevTripleH on 2013-01-10
I'm gonna go ahead and apologize in advance for whatever silly thing I'm doing wrong, since I'm new to this, and am probably missing something.

I'm doing a little project for school which involves using ubuntu to run a small i/o board and make the lights flash a little. This is normally done by typing 'ioboard' in the terminal. 'ioboard' is the name of a file provided to me by my teacher, normally we put it in a specific folder, then use the 'cd' command in the terminal to get to the folder, then type in ioboard. For some reason, I can't get it to work on Ubuntu (where it has previously worked on Kubuntu). 

I have placed the 'ioboard' file in /usr/local/bin, and used the cd command in the terminal to go to the directory, but when I type in 'ioboard' or './ioboard', it says "No such file or directory'. I've also tried doing the same thing after using the su command.

There is probably something small I am missing here, since I am new to the whole Linux system. Does anyone have any ideas of what I'm doing wrong?

Thanks in advance! ):P

---

### Post by steeldriver on 2013-01-10
is 'ioboard' a binary executable file? are you sure it is compiled for the same architecture as your machine?

[http://ubuntuforums.org/showthread.php?t=2086646](http://ubuntuforums.org/showthread.php?t=2086646)

---

### Post by TriplevTripleH on 2013-01-10
I'm positive it is. Well it was originally called 'ousb', but I changed it because it had a similar name to one of my documents. I have followed my professors manual here: [http://pjradcliffe.files.wordpress.com/2009/04/open-usb-io_reference_1v08.pdf](http://pjradcliffe.files.wordpress.com/2009/04/open-usb-io_reference_1v08.pdf)
perfectly.

EDIT: and I've also changed the permissions. I'm not sure what I'm doing wrong, even when I type in 'ls' it lists the file right there in the terminal :@
EDIT 2: Just tried changing the name to ousb, and still the same thing. bawww.

---

### Post by Muratturat on 2013-01-10
> **TriplevTripleH said:**
> I'm gonna go ahead and apologize in advance for whatever silly thing I'm doing wrong, since I'm new to this, and am probably missing something.

I'm doing a little project for school which involves using ubuntu to run a small i/o board and make the lights flash a little. This is normally done by typing 'ioboard' in the terminal. 'ioboard' is the name of a file provided to me by my teacher, normally we put it in a specific folder, then use the 'cd' command in the terminal to get to the folder, then type in ioboard. For some reason, I can't get it to work on Ubuntu (where it has previously worked on Kubuntu). 

I have placed the 'ioboard' file in /usr/local/bin, and used the cd command in the terminal to go to the directory, but when I type in 'ioboard' or './ioboard', it says "No such file or directory'. I've also tried doing the same thing after using the su command.

There is probably something small I am missing here, since I am new to the whole Linux system. Does anyone have any ideas of what I'm doing wrong?

Thanks in advance! ):P

And your ubuntu version is 32-bit at this moment and your original computer system was 64-bit(before ubuntu)?

---

### Post by TriplevTripleH on 2013-01-10
> **Muratturat said:**
> And your ubuntu version is 32-bit at this moment and your original computer system was 64-bit(before ubuntu)?

When I go to System Settings > Details > Overview, it says OS type 64-bit. Is this what you meant?
Can the 32bit or 64bit be the cause of this error?

---

### Post by BicyclerBoy on 2013-01-10
Have you set the executable bit ?

---

### Post by TriplevTripleH on 2013-01-10
> **BicyclerBoy said:**
> Have you set the executable bit ?

I believe I have. I did it by just right clicking>properties> tick the box that says Allow executing file as program.
I've also tried chmod +x ousb.

I'm starting to think that it may be an issue that I have caused, that can't really be resolved on this forum, because I have no idea what I've done wrong.

So thanks to everyone for your help!

---

### Post by Cheesemill on 2013-01-10
What's the output of...
```
file ousb
```To run 32-bit executables on a 64-bit machine you will need to install the package ia32-libs.

---

### Post by Muratturat on 2013-01-10
> **Cheesemill said:**
> What's the output of...
```
file ousb
```To run 32-bit executables on a 64-bit machine you will need to install the package ia32-libs.

I was just thinking same issue.

---

### Post by BicyclerBoy on 2013-01-10
So if that file (ousb) was in path /usr/local/bin/ or /usr/bin/ then you would have need to use 
sudo chmod ....

Note that linux is case sensitive..

You can check your USB device is recognised with:
lsusb

and then check for any driver by looking at output from:
lsmod
dmesg

I would guess the USB device uses the usb-cdc or usb-hid driver..

---

### Post by TriplevTripleH on 2013-01-10
> **Cheesemill said:**
> What's the output of...
```
file ousb
```To run 32-bit executables on a 64-bit machine you will need to install the package ia32-libs.

I get:

```
ousb: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), 
dynamically linked (uses shared libs), for GNU/Linux 2.6.9, not stripped
```

Methinks we have a solution

EDIT: So how does one go about getting this elusive ia32-libs? From what I understand you can install things through the terminal with an install command, is this how you'd do it? Again, sorry for my naivety, I am but a humble Windows user.

---

### Post by Muratturat on 2013-01-10
> **TriplevTripleH said:**
> I get:

```
ousb: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), 
dynamically linked (uses shared libs), for GNU/Linux 2.6.9, not stripped
```

Methinks we have a solution

EDIT: So how does one go about getting this elusive ia32-libs? From what I understand you can install things through the terminal with an install command, is this how you'd do it? Again, sorry for my naivety, I am but a humble Windows user.

```
sudo apt-get install ia32-libs
```

---

### Post by TriplevTripleH on 2013-01-10
Bah! I get a funny message here:

```
user@ubuntu:~$ sudo apt-get install ia32-libs
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch but it is not installable
E: Unable to correct problems, you have held broken packages.
user@ubuntu:~$ cd /usr/local/bin
user@ubuntu:/usr/local/bin$ ousb
bash: /usr/local/bin/ousb: No such file or directory
user@ubuntu:/usr/local/bin$ ./ousb
bash: ./ousb: No such file or directory
```

---

### Post by BicyclerBoy on 2013-01-10
apt-get install -s ia32-libs-multiarch ??

(-s is simulation only)

---

### Post by Muratturat on 2013-01-10
```
apt-get install libc6-i386 lib32gcc1 lib32z1 lib32stdc++6 ia32-libs
```

---

### Post by TriplevTripleH on 2013-01-10
Tried both, and am now giving up.

Thanks you very much to all the good people who attempted to help! 
):P

---

### Post by TriplevTripleH on 2013-01-10
So I tried again just now, and I think I may have found something. I moved the 'ousb' to my documents and used cd in terminal to go there. When I tried running ./ousb it said "Permission denied", so I changed the permissions to allow execution, and now when I run the same command, it says "no such file or directory". Does this mean anything to anyone?

---

### Post by Cheesemill on 2013-01-11
It means you still have exactly the same problem.

To run a 32-bit executable on a 64-bit system you need to install the ia32-libs package. Without this it will never work.

If you search the forums there are plenty of people who have had issues installing this package, but most of them resolved this problem.

---

