---
title: "Skype problem."
date: 2012-11-09
forum: General Help
---

### Post by Wazza20 on 2012-11-09
First of all, hello everyone, now...i have a problem installing skype on my laptop running ubuntu 12.10. I've tried to install it using these comands :
```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update
sudo apt-get install skype
```
but no luck...
Then i tried installing from a deb on their website, still no luck...probably because the version on their site is outdated.What do you guys think should i do ?
Oh yea...i forgot to show you the error i get:
```
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages
```

Thanks in advance.

---

### Post by Amithiel on 2012-11-09
i installed mine from here:

[http://www.skype.com/intl/en/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/)

just choose the x86 or x64 accordingly

fix broken packages: 
sudo apt-get install -f

---

### Post by Wazza20 on 2012-11-09
I already said in my post that the installer from their site is outdated...

EDIT1 : The main error is :
```
The following packages have unmet dependencies:

skype: Depends: lib32stdc++6 (>= 4.1.1-21) but 4.7.2-2ubuntu1 is installed
       Depends: ia32-libs but it is not installed
       Depends: lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19) but 1:4.7.2-2ubuntu1 is installed
```

=> .deb installer outdated.

---

### Post by papibe on 2012-11-09
Hi Wazza20.

There's a much simpler way to install it. Take a look at this instructions: [Install Skype]("http://askubuntu.com/questions/7498/how-do-i-install-skype").

Let us know how it goes.
Regards.

---

### Post by Wazza20 on 2012-11-09
I've got those repos added...and now somehow...skype shows up in the software search but this shows up too :
```
http://www.mediafire.com/view/?ns5pnosr0pikscn
```
EDIT1 : Looks like all i have to do...is...to install ia32-libs...i need some good repos...in 12.10 i don't have that...or could u guys give me a good tutorial to install ia32-libs in 12.10 ?

---

### Post by Wazza20 on 2012-11-19
Topic is kinda solved...in ubuntu 12.10 32bit works right away from the skype website. Anyways now i'm back on w8 and soon i will dual-boot with ubuntu :D.
Back then when i had that problem, i was using a usb memory stick with ubuntu on it .

Cheers and thanks for the help so far :) .

---

