---
title: "Remove authorisation prompt"
date: 2008-07-01
forum: General Help
---

### Post by gbak1 on 2008-07-01
I have installed hardy and I want to know how I can disable the unlock feature whenever I want to change something like say dns. 
Since I am the administrator of my own computer why on earth do I need to click "unlock" re-enter the password that Ive already entered at logon before I can change anything? All this re-enter password again.....and again.....and again.....its driving me insane.

---

### Post by aquavitae on 2008-07-01
> **gbak1 said:**
> I have installed hardy and I want to know how I can disable the unlock feature whenever I want to change something like say dns.You want to disable passwords for sudo: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo"). But I think Hardy has an option for it when you enter the password the first time.
> 
Since I am the administrator of my own computer why on earth do I need to click "unlock" re-enter the password that Ive already entered at logon before I can change anything? All this re-enter password again.....and again.....and again.....its driving me insane.Security. Not against yourself, but against hackers, malware, viruses, etc. You'll read in a lot of places that viruses and malware are not a problem in linux, but one of the main reasons for this is that in order to make any changes to the system you have to enter a password. You can disable this, but then you remove one of the main reasons most people install linux in the first place. Btw, linux viruses do exist, but unless they have access to the root account they are pretty harmless. Disabling passwords is one way of giving them access to the root account.

---

### Post by Vishal Agarwal on 2008-07-01
use > sudo -i 

Vishal Agarwal

---

### Post by aquavitae on 2008-07-01
```
sudo -i
```will also work, and is more in keeping with ubuntu's philosophy on root logins. But you can't use gui tools that way, it has to be command line (unless you do a root login to X, which is a really, really bad idea).

---

### Post by Fingers &amp; Thumbs on 2008-07-01
The biggest problem with security for windows users is that most users who are the actual owners use the administrative account by default instead of a limited users acount, but it's not difficult to see why they do this. Having to log in and out of different accounts to perform different tasks is a huge inconvenience and a productivity muncher. Look at linux's password promt approach as a blessing, it gives us all the piece of mind of a limited user account, plus all of the useabily and functionality of an administrative account.

---

### Post by sisco311 on 2008-07-01
> **Vishal Agarwal said:**
> You can open root login for you in order to get full command on your system without any restriction. To do so u need to change the root password with 

change the password and login as 

or otherwise u can issue a command 

and do the changes as per your requirement.

But be careful this all is very dangerous.


Vishal Agarwal
It's against [forum policy]("http://ubuntuforums.org/showthread.php?t=765414") to give a tutorial on how to enable the root account.

---

### Post by billgoldberg on 2008-07-01
> **sisco311 said:**
> It's against [forum policy]("http://ubuntuforums.org/showthread.php?t=765414") to give a tutorial on how to enable the root account.

I didn't know it was against forum policy.

But it makes sense.

Using a root account when you don't know what you are doing is extremely dangerous.

---

### Post by Vishal Agarwal on 2008-07-01
Dear All,

The purpose was not to violate the forum policy. I was also facing the same problem, so that I searched the UBUNTU for help, and found the way out to work. The same was posted for the sake of helping only.

Vishal Agarwal

---

### Post by gbak1 on 2008-07-02
> **Fingers & Thumbs said:**
> The biggest problem with security for windows users is that most users who are the actual owners use the administrative account by default instead of a limited users acount, but it's not difficult to see why they do this. Having to log in and out of different accounts to perform different tasks is a huge inconvenience and a productivity muncher. Look at linux's password promt approach as a blessing, it gives us all the piece of mind of a limited user account, plus all of the useabily and functionality of an administrative account.

This is more what Im after. To enable more previleges to a particular user for certain services while setting up ubuntu (I found that a number of settings were continually not being saved after reboots and hence the frustration). Out of curiousity will sudo -i allow all other user accounts to freely access the root account?

---

### Post by aquavitae on 2008-07-03
sudo -i just temporarily logs you into a root shell. When you close the terminal it logs you out. So only users who have privileges to use sudo -i will be able to use it. Also note, sudo (not sudo -i) gives you the temporary privilege of using sudo repeatedly without entering a password. So if you open synaptic, enter the password and then open network setup, it won't ask for the password a second time.

---

### Post by Portable_Jim on 2008-07-03
> **aquavitae said:**
> Security. Not against yourself, but against hackers, malware, viruses, etc. You'll read in a lot of places that viruses and malware are not a problem in linux, but one of the main reasons for this is that in order to make any changes to the system you have to enter a password. You can disable this, but then you remove one of the main reasons most people install linux in the first place. Btw, linux viruses do exist, but unless they have access to the root account they are pretty harmless. Disabling passwords is one way of giving them access to the root account.
I agree.
Just to add another source: [http://www.psychocats.net/ubuntu/security#versuswindows](http://www.psychocats.net/ubuntu/security#versuswindows).

---

