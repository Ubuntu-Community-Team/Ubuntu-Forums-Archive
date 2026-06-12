---
title: "Synaptic option in System&gt;Administration menu is gone! disappeared!"
date: 2008-05-07
forum: General Help
---

### Post by hurinth on 2008-05-07
I recently upgraded over the Internet from 7.10 to 8.04, days after I realize Synaptic is not present in the System>Administration submenu.

I go to System>Preferences>Main Menu and I see the checbox un-checked, so I check it, but 1 second later I can see how it unchecks by itself... This happens with any item from the Administration submenu.

Now, if I got to ~/.local/share/applications and double click the Synaptic icon, I get the error in the attached image.

Please anyone can help me here?

---

### Post by Bubba64 on 2008-05-07
[http://ubuntuforums.org/showthread.php?t=785019](http://ubuntuforums.org/showthread.php?t=785019)

---

### Post by hurinth on 2008-05-07
It won't open > hurin@Asfaloth:~$ sudo synaptic
[sudo] password for hurin: 
hurin@Asfaloth:~$ 

It stays there and never opens a thing, any other idea please!?!?

---

### Post by Bubba64 on 2008-05-07
When you upgraded to Hardy did you use an ISO CD or did you upgrade via the update manager. Open the system-administration-software-sources and check if the sources you want to use are ticked on, and the CD portion is off if you upgraded with a CD. I open all sources except source on the Ubuntu Software page. You might also Change the download source I was not linking with the main source this weekend so I used the find the best source via Download-other-find best source. I don't know if any of this is going to work but getting access to the software sources is important. If you get the link to soft sources set up and synaptic still is not available with a sudo synaptic in the terminal try in the terminal
sudo dpkg --configure -a then try sudo synaptic and see if it opens then. I am not an expert by any means on Linux but am just giving you what I would do if I was in your position, hopefully somebody else will chime in on this and help with this. It may be that if you have stuff on the Hardy program you have now that you need saved, save it on another computer or by another means and get an ISO alternative daily download and burn a CD and do a fresh install. I have never seen the exact problem you have synaptic being not available in the system-administration area. Usually it is not available due to being closed in the middle of a process and the dpkg just needs to be run to reset it.  First Thing I would do is I would possibly restart the computer and when you get to the login window choose safe mode and open up the terminal and run this  sudo dpkg --configure -a   it may be that somewhere in your download something went wrong that you didn't notice and this command will start it at that point. Good Luck

---

### Post by hurinth on 2008-05-08
Ok, I upgraded via Internet.
I can't do the steps on the software sources because it is also not present

sudo dpkg --configure -a won't bring it up, neither does sudo synaptic

Ne other idea?

---

### Post by Bubba64 on 2008-05-08
The dpkg command is used as a reset if somewhere synaptic or a download has been corrupted, so it shouldn't bring up anything unless while you were downloading it was corrupted and it would start the download again. As I said I am not an expert in Linux in general. Since nobody else has commented I think you probably need to save what you want or can and down load a daily alternative ISO of Hardy and burn it to a CD at no faster than 4x and do a clean install, this is what I would do. You could also try running in the terminal sudo apt-get update and if it runs correctly then sudo apt-get upgrade. But since you cannot access the software source information I doubt if this will make a difference. Here is the link to the alternative daily ISO download.
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
If you have a regular pc read the instructions and it will be the 1st download choice. There is also a link to a guide on the bottom part of the download section. If you need help in any of this post it and you will get answers on how to install if you don't know how already. You have kind of a unusual situation that seems like the original upgrade was corrupted at some point, there should of been a pop up giving you a messages to this.

---

### Post by hurinth on 2008-05-09
Thanks for all your help Bubba. I would rather find out what the h*** happened to my user. I realized it has to do with permissions, since I can't even get Add/Remove from Applications.

Anybody please help here to recover the software managers, could this be a virus?!?!?

---

### Post by jocko on 2008-05-09
> **hurinth said:**
> Anybody please help here to recover the software managers, could this be a virus?!?!?

Virus? Probably not. More likely your upgrade did not complete by some reason.

There's one thing you can try:```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop
```
If this works, it will probably fix your problem.
If not, get a Hardy CD, backup your /home (if you don't have a separate /home partition) and reinstall Ubuntu.

---

### Post by hurinth on 2008-05-09
Nothing worked.......

---

### Post by jocko on 2008-05-09
When you say nothing worked, did you by any chance get any error messages from those commands?

---

### Post by asrai on 2008-05-09
Are there any other users on your system?

If you go to users and groups from the system/administration menu, click on your name and then 'properties' then 'user privileges' is 'administer the system' ticked?

Looks like something strange has happened here :S

---

### Post by hurinth on 2008-05-09
> **jocko said:**
> When you say nothing worked, did you by any chance get any error messages from those commands?

No. I run each command and a shell prompt returned below. No window appeared. Now, as Asrai says, I don't see any chechbox ticked in my user's properties, as shown in the attachment

I have already been recommended to do a fresh install -number 13million- but I would rather like if someone has a rescue idea here. Maybe some commands to have my user properties include the privileges it should. 

NE ideas?!?!

---

### Post by asrai on 2008-05-09
Can you log in through recovery mode in the grub menu and then change privileges for your user account?

*fingers crossed for you* hopefully someone smarter than I am will come past as well and give you some more suggestions if that doesn't work.

---

### Post by hurinth on 2008-05-11
Thanks Asrai, I tried recovery mode and still nothing... too long with this problem, I had do a fresh install.

---

