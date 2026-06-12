---
title: "Vmware tools for ubuntu"
date: 2008-05-12
forum: General Help
---

### Post by Briandr on 2008-05-12
Hi,

I am very new to linux. I have Ubuntu 8.04 on VMWare 5.5.6. Here is what I been able to gather. Ubuntu cannot open the vmware tools rpm file. I need to extract the execuatable files from the tar file. Questions arise. Do I need to put the files into a specific folder? Do I need to logon as root when doing this? Do I have to install under a command line interface? Is the command line interface Terminal under accessories?

Here is my deal. I got a good amount of experience with command line prompts from my dos days. I would prefer not to use a command prompt unless I have to. So what are my best options at this point? I am even thinking Kubuntu might be a better fit for me. Does it use the command prompt interface as heavily as Ubuntu.

Thanks guys. Just reminder. Don't sink me with alot of Linux stuff as I just getting my feet wet here.

---

### Post by dansen926 on 2008-05-12
The best way for you to solve this issue would be to use alien, which converts .rpm to installable .deb files. You can install this from the package manager, but this is how I did it:

In terminal, do the following:
```
$sudo apt-get install alien
```

after that go to the directory where you package is and:
```
$sudo alien filename.rpm
```

That should give you a nicely installable .deb package. enjoy!

---

### Post by Briandr on 2008-05-14
I am having alot of headaches trying to convert the .rpm file to .deb file.  Part of the reason is I am having a hard time is my inability to navigate the linux file system. Let's assume for argument's sake I copied the whole package to the 'Documents' folder. Can someone show me how to navigate to the folder and then how to execute Alien. Thanks.

---

