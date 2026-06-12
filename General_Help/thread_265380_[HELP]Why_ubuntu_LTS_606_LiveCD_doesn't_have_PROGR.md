---
title: "[HELP]Why ubuntu LTS 606 LiveCD doesn't have PROGRAME relate app?"
date: 2006-09-25
forum: General Help
---

### Post by meteora on 2006-09-25
I am a Chinese Programer. Yesterday, I had received the ubuntu LiveCD from shipit.ubuntu.com. After installing it on my computer, I found that this is a wonderful copy of linux. Thank all of your's good work on it.

But now, I have something question about this copy of ubuntu LiveCD.
First, I can't login into ubuntu linux as root account. I have read the help document. There is no usfull information about this issue. Yes, this is a security for normal people who use linux, but no for US, Programers.

Second, I have found that it don't have any programe relate software in ubuntu LiveCD. This is a terrible thing!! Maybe ubuntu Linux is NOT suit for programers? Or Pls tell me how can I get full edition about ubuntu linux.

Thanks a lot!

---

### Post by inkybutton on 2006-09-25
> **meteora said:**
> I am a Chinese Programer. Yesterday, I had received the ubuntu LiveCD from shipit.ubuntu.com. After installing it on my computer, I found that this is a wonderful copy of linux. Thank all of your's good work on it.
...

Second, I have found that it don't have any programe relate software in ubuntu LiveCD. This is a terrible thing!! Maybe ubuntu Linux is NOT suit for programers? Or Pls tell me how can I get full edition about ubuntu linux.

Thanks a lot!

Hey.
Programming applications can be obtained using Synaptic or APT. There are plenty of programming apps in the repositories of Ubuntu.

Regarding your first question... I have seen it somewhere... I will try to find it.

---

### Post by enopepsoo on 2006-09-25
It denies root access for security reasons.  You use sudo to get root priviliges for individual commands.  For example:
```
sudo gedit /etc/apt/sources.list
```
will let you edit your apt sources file.

If you really feel you need more root than that, you can try ```
sudo bash
``` or ```
sudo nautilus
```to get a root command line or file browser respectively.  You will find that you don't need root all the time!:mrgreen:

---

### Post by inkybutton on 2006-09-25
> **enopepsoo said:**
> It denies root access for security reasons.  You use sudo to get root priviliges for individual commands.  For example:
```
sudo gedit /etc/apt/sources.list
```
will let you edit your apt sources file.

If you really feel you need more root than that, you can try ```
sudo bash
``` or ```
sudo nautilus
```to get a root command line or file browser respectively.  You will find that you don't need root all the time!:mrgreen:

If you want to run as ROOT and ignore our suggestions, then do the following:

Going back to a traditional root account

<!> This is not recommended!

If all you need is to be able to work on a root console you'd better use the command:

sudo -i

Enabling the root account

To enable the root account (i.e. set a password) use:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root

This is from [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
For more information and how to disable root, visit the above website

---

### Post by meteora on 2006-09-25
Oops~! I will try sudo when I back home.

Using **Synaptic **or **APT**?
What are they? How can I find them? Actually, I can see ubuntu liveCD has the programe tools likes GCC etc. But, I cann't use them in terminal. Bash replies Gcc not found or bad command. Oh, my god. And I also try it out as root(login as root by 'su') but failed.:-?

---

### Post by inkybutton on 2006-09-25
Synaptic and APT are package managers.

To open Synaptic, click on System > Administration > Synaptic Package Manager.

If you are trying to find tools like GCC, they are in a package "build-essential" which can be downloaded and installed in Synaptic Package Manager.

To install build-essential, open Synaptic Package Manager, click on "Search", and type in "build-essential", then click on Search. The package will show up in the list. Click on the white radio button beside the list, and select "Mark for installation". Click on the "Apply" button on the toolbar, and you are done!

NB. Any packages you installed on a Live CD will be deleted after the session has ended.

---

### Post by kpkeerthi on 2006-09-26
meteora.. i would suggest you to read [https://help.ubuntu.com/](https://help.ubuntu.com/) so you know your way around in ubuntu.

---

