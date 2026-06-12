---
title: "Problem with 32-bit binary on a 64-bit distro"
date: 2016-02-22
forum: General Help
---

### Post by ross4 on 2016-02-22
I have dual boot Linux Mint 17.3 "Rosa" - Release amd64  & Xubuntu 14.04.3 LTS "Trusty Tahr" - Beta amd64 (according to README.diskdefineson respective iso*)*. One program I want to use, Anki, states that “...you'll need to ensure you can run 32 bit binaries as well”.  At the suggestion of the distributor, I followed the instruction on Ask Ubuntu to run sudo dpkg --add-architecture i386.

 This program now works properly on Mint but not on Xubuntu.  

 When I run the command *dpkg --print-foreign-architectures && dpkg –print-architecture* the output for each distro is the same:  

    i386  

    amd64

 On the basis of this I assume, perhaps incorrectly, that the 32-bit capability is functional on both. What could the problem be? What can I do further to find out the source of this problem?
Is there any possibility that the order of installation is critical? I mean I installed Anki then added the architecture in Xubuntu. Should I have reversed this? Unfortunately, I cannot remember if I actually did add the architecture to the Mint. It may have been that way by default, and therefore functional before I installed Anki.
Regards,
Ross

---

### Post by Dennis N on 2016-02-22
64-bit Xubuntu can run 32-bit software provided the necessary libraries are installed. Just to be clear, **dpkg --add-architecture** does not add any libraries itself. The purpose of that command is to add an architecture to the list of architectures for which packages can be installed without using --force-architecture option with dpkg.

I have a several 32-bit games installed on this 64-bit Xubuntu system. The general procedure to get them working was to install the program and if it did not run, determine the 32-bit libraries it needs and install them. Mint may have some 32-bit libraries installed by default with their 64-bit systems; Ubuntu does not.

If you explain further the problem you are having, someone may be able to help.

---

### Post by ross4 on 2016-02-22
A quick summary of the  problem is that although Anki functions correctly in general, when I use one particular add-on, I get an error message that ends in:   
..."Please ensure your Linux system has 32 bit binary support.")

 Exception: Please ensure your Linux system has 32 bit binary support.

So, I guess the problem is how do I ensure that (or even determine whether) my Linux system has 32 bit binary support.
Ross

---

### Post by Dennis N on 2016-02-22
As my other post stated, 64-bit Xubuntu can run 32-bit software _provided the necessary libraries are installed_. My take on the error message is that all the libraries needed to support your program/add-on are not yet installed. Check the installed packages on Mint for the 32-bit libraries it includes, and install the same ones on Xubuntu.

Edit: Also, the distributor may supply a list of required support libraries for Linux.

---

### Post by Dennis N on 2016-02-22
This article has some suggestions on 32 bit libraries that are commonly needed:

[https://support.humblebundle.com/hc/en-us/articles/202759400-Installing-32-bit-libs-on-a-64-bit-Linux-system](https://support.humblebundle.com/hc/en-us/articles/202759400-Installing-32-bit-libs-on-a-64-bit-Linux-system)

I used it as a starting point, and installed what it suggested. Then, I ran the program from terminal, which often indicates what else is missing:

Example: errors such as: "Cannot open shared library libasound_module_conf_pulse.so&#8221;

Use apt-file to locate the needed package (needed package is in red).

```
dmn@Sydney:~$ sudo apt-file find libasound_module_conf_pulse.so
[sudo] password for dmn: 
[COLOR="#FF0000"]libasound2-plugins[/COLOR]: /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_conf_pulse.so
```

Install the 32-bit version of the package. In Synaptic, ends with :i386. You can use the "architecture" button in Synaptic to display only 32-bit packages.

---

### Post by Dennis N on 2016-02-22
I just looked myself at Linux Mint 17.3 which I happen to have installed as well. It is the 64-bit version, but I see it has a large number of 32-bit libraries installed by default. That is most likely why you program works in Mint, but not Xubuntu.

---

### Post by ross4 on 2016-02-22
Hello Dennis, 
Thank you for your patience and your help. I read your series of messages just as I was composing a google search on the problem and, essentially it was your replies that lead me to an effective search where I found how to handle the problem successfully. I actually missed the link you provided because I saw immediately from a quick read of your responses how to frame my search. I would paste the link I used and the set of commands but I am not sure what the protocol is on putting links and 'code' in a reply... or, for that matter HOW to do other than simply cutting and pasting.
At any rate, the add-on for Anki is now working properly. I really appreciate your help.
Cheers,
Ross

---

### Post by Dennis N on 2016-02-22
Sounds good, and thanks for giving the feedback on how things worked out.

---

