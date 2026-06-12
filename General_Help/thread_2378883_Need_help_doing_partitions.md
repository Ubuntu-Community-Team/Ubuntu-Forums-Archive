---
title: "Need help doing partitions"
date: 2017-11-28
forum: General Help
---

### Post by future.progrr on 2017-11-28
Hello,

I know there are a lot of guides on partitioning but what most of them say is that "it depends on my needs". I am still a newb and would like to know how i should make the partition table when installing ubuntu.

I am currently on windows 10 but when I will install ubuntu I will erase windows and everything, wipe clean all the memory. I have 1tb hdd and 512 ssd and will use my computer for programming and installing apache2 server.

Can someone please help me with a detailed guide for partitioning with this kind of specs. Please, make it as clear as possible, I am pretty new and stupid when it comes to this kind of stuff. Also, do not fear to explain the concepts to me, what everything means and why it should be done like this. 

Thanks a lot

---

### Post by SeijiSensei on 2017-11-28
I don't see any need for partitioning.  I'd just let Ubuntu set up the SSD drive as the main "root" directory, and maybe use the other drive for /home.

---

### Post by irv on 2017-11-28
If you plan on having only Ubuntu Linux on this machine it is simple. Just let the install do it for you. You would pick format the entire drive and install Linux. It will do all the work for you.
Now if you want to run both Windows and Ubuntu you would pick install alongside Windows, and again it will do the partitioning for you. The install really does a good job.
After everything is up and running you can use a program called Gparted to change partitions sizes. 
I would suggest making a recovery USB for Windows so you can reinstall it if something goes wrong. It is alway good to safe than sorry.

---

### Post by oldfred on 2017-11-28
Was Windows 10 pre-installed and therefore UEFI, not old BIOS?
Best then to install Ubuntu in UEFI boot mode.

Do not know about apache server. Normally I thought server would be a separate system and most servers do not even have a gui, although newer users often install gui, but not full desktop which includes all the desktop applications.

Many that try to make leap to Linux, find they have to have one application that only runs in Windows. It took me 5 years to wean myself fully from Windows. Best to make a full back up of Windows just in case.

I also have a system with SSD & HDD. I install Ubuntu in / (root) on SSD in a 25GB partition and on HDD have a /mnt/data partition where all the data normally in /home is. For newer users often easier to put /home on HDD as then it is automatically set up with ownership & permissions and mounted when rebooted. But if running a server you need to learn about ownership, permission & mounting partitions which are something new to Windows users.

I would suggest walking before running. Maybe better to dual boot at first with both Windows & Ubuntu.  But installing Ubuntu is relatively easy (maybe a lot to learn first time or two). If you have good backup procedures, then in worst case easy to just reinstall.

What brand/model system? Some have unique requirements.
If installing desktop in UEFI mode review link in my signature. it also has a lot of good info in general and many links to further info. If you do not understand some terms scroll to bottom for definitions of many acronyms. 

This is still pretty much my partitions, but installs have been updated to newer versions. 
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by SeijiSensei on 2017-11-28
It's easy enough to run Apache on a desktop machine.  I'd install the LAMP package:
```
sudo apt-get install lamp-server^
```
That installs Apache, the PHP scripting language, and the MySQL database server.

The default website directory is /var/www/html.  If you put an index.html in that directory, it will appear when you navigate to [http://localhost/](http://localhost/).

---

### Post by irv on 2017-11-28
Oldfred, just a quick note on apache server. (I do have a separate server), but you can install apache server software to run on a desktop and use it as a local server. I did this back when I was still developing web pages for the Internet. I used it with PHP programming. This is a good way to test your pages before uploading them to the web. For some reason it sounded like the OP was thinking about doing this when had programming and Apache in the same line.
If this is what he meant, he can install the server software after the install and set it up as a local server. Users do this for a home server as well.

---

### Post by future.progrr on 2017-11-28
> **irv said:**
> If you plan on having only Ubuntu Linux on this machine it is simple. Just let the install do it for you. You would pick format the entire drive and install Linux. It will do all the work for you.
Now if you want to run both Windows and Ubuntu you would pick install alongside Windows, and again it will do the partitioning for you. The install really does a good job.
After everything is up and running you can use a program called Gparted to change partitions sizes. 
I would suggest making a recovery USB for Windows so you can reinstall it if something goes wrong. It is alway good to safe than sorry.
I would also like to have other OSes on virtual machines, forgot to mention that. I would like to have arch linux, kali and also windows, but the main to be ubuntu

> **oldfred said:**
> Was Windows 10 pre-installed and therefore UEFI, not old BIOS?
Best then to install Ubuntu in UEFI boot mode.

Do not know about apache server. Normally I thought server would be a separate system and most servers do not even have a gui, although newer users often install gui, but not full desktop which includes all the desktop applications.

Many that try to make leap to Linux, find they have to have one application that only runs in Windows. It took me 5 years to wean myself fully from Windows. Best to make a full back up of Windows just in case.

I also have a system with SSD & HDD. I install Ubuntu in / (root) on SSD in a 25GB partition and on HDD have a /mnt/data partition where all the data normally in /home is. For newer users often easier to put /home on HDD as then it is automatically set up with ownership & permissions and mounted when rebooted. But if running a server you need to learn about ownership, permission & mounting partitions which are something new to Windows users.

I would suggest walking before running. Maybe better to dual boot at first with both Windows & Ubuntu.  But installing Ubuntu is relatively easy (maybe a lot to learn first time or two). If you have good backup procedures, then in worst case easy to just reinstall.

What brand/model system? Some have unique requirements.
If installing desktop in UEFI mode review link in my signature. it also has a lot of good info in general and many links to further info. If you do not understand some terms scroll to bottom for definitions of many acronyms. 

This is still pretty much my partitions, but installs have been updated to newer versions. 
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)
I forgot to mention about wanting to install kali, arch and windows on virtual machines. As for experience, i have a little, have been running ubuntu on virtual machine for like a week. I studied ownership, permissions and most basic things. As for backup, i dont think i need any. The windows install was also pretty fresh, everything that was important i have already copied on a flash drive.

> **irv said:**
> Oldfred, just a quick note on apache server. (I do have a separate server), but you can install apache server software to run on a desktop and use it as a local server. I did this back when I was still developing web pages for the Internet. I used it with PHP programming. This is a good way to test your pages before uploading them to the web. For some reason it sounded like the OP was thinking about doing this when had programming and Apache in the same line.
If this is what he meant, he can install the server software after the install and set it up as a local server. Users do this for a home server as well.
Exactly my thought, I was going to install apache2 for web developing

---

### Post by oldos2er on 2017-11-28
Kali should be installed to a flash drive,  not a hard disk;  it's not a desktop distro.

---

