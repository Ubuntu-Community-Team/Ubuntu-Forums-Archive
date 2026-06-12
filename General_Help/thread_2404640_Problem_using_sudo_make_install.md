---
title: "Problem using sudo make install"
date: 2018-10-26
forum: General Help
---

### Post by huzi95s on 2018-10-26
Hello,
I am using ubuntu 18.04 on my virtual machine.
I am making a project in which I have to perform face-dectection using raspberry pie using the cameras on the servo motor 
To do this I downloaded a software for the raspberry pie which controls mulltiple motors from
[https://github.com/richardghirst/PiBits/tree/master/ServoBlaster](https://github.com/richardghirst/PiBits/tree/master/ServoBlaster)
Now i downloaded the file and installed the dependencies and extracted it to the documents folder. I used cd command to navigate to the folder and with a view to install this software i used  sudo make install. It gave me the following error:

 
make: *** No rule to make target 'install'.  Stop


I also tried to install build-essentis to resolve this file using this link
[https://askubuntu.com/questions/398489/how-to-install-build-essential](https://askubuntu.com/questions/398489/how-to-install-build-essential)

But whe I run the command sudo apt-get install build-essential the output is:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.4ubuntu1).
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-29 linux-headers-4.15.0-29-generic
  linux-image-4.15.0-29-generic linux-modules-4.15.0-29-generic
  linux-modules-extra-4.15.0-29-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

But when I again try to run the command sudo make install it gives me the same error.

How do i resolve this error?
Thanks In advance

---

### Post by Holger_Gehrke on 2018-10-26
That means the Makefile does not define a target 'install'. You just run 'make servod' to compile the code and afterwards run the resulting binaries from the directories where they are. At least the 'README.txt' at the first link you provided says to do it that way.

Holger

---

### Post by huzi95s on 2018-10-26
Hello,
I am sorry I am a newbie. Do you mean to import the file in my code using the appropriate path and then run the whole code? 

And yes for extra knowledge please could you explain why the Makefile does not define the target install? A link to an online discussion forum or a blog or a website would also suffice

Thanks in advance 
Huzefa

---

### Post by SeijiSensei on 2018-10-26
No, Holger said you should use "make servod" not "make install".  He also suggested you read the README.txt file at the top of code tree.  It doesn't look like you did that either.

---

### Post by huzi95s on 2018-10-26
Thank You SeijiSensi[COLOR=#000000][FONT=Ubuntubeta] and Holger_Gehrke[/FONT][/COLOR] I will do it as you said.

---

### Post by huzi95s on 2018-10-26
I did as you suggested but again it i showing the same error why?

---

### Post by SeijiSensei on 2018-10-26
Did you run ./configure if needed?

What if you just type "make" without a target?

---

### Post by huzi95s on 2018-10-27
I did run./configure. It shows no such file or directory. The second alternative also does not work

---

### Post by Holger_Gehrke on 2018-10-27
If you cloned the git repository with 'git clone [https://github.com/richardghirst/PiBits.git](https://github.com/richardghirst/PiBits.git)' you ended up with a directory tree like this:
```

PiBits/
&#9500;&#9472;&#9472; MouseScan
&#9500;&#9472;&#9472; MPU6050-Pi-Demo
&#9500;&#9472;&#9472; PiFmDma
&#9492;&#9472;&#9472; ServoBlaster
    &#9500;&#9472;&#9472; kernel
    &#9474;   &#9492;&#9472;&#9472; udev_scripts
    &#9492;&#9472;&#9472; user

```
The source for the servo blaster userspace demon is in PiBits/Servoblaster/user. Change to that directory and run 'make servod'. It'll start compiling. But unless you're doing it on a Raspberry Pi or have set up a cross-compilation environment it'll abort with an error because the code references a library (bcm_host.h) that doesn't normally exist on a PC.

Holger

---

### Post by huzi95s on 2018-10-28
Thank you people It really helped a lot. Just a last think though where did you find the library bcm_host.h in this software as i was not able to find it anywhere. I mean neither it was imported in the source and header files nor it was explicitly present

---

### Post by Holger_Gehrke on 2018-10-28
I didn't. I googled for it and found out it's a library for interfacing to the Pi's hardware (bcm=Broadcom, maker of the SOC the Pi is built around). That's why I said to either compile the program on a Pi running Linux (where it's probably part of build-essentials or the kernel-headerfiles) or to set up a cross-compilation environment (a compiler running on a PC but generating arm code with libraries and headers for arm).

Holger

---

