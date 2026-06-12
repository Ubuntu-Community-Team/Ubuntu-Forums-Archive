---
title: "shut down linux while installing updates. All sorts of error (NEWBIE)"
date: 2007-07-15
forum: General Help
---

### Post by yungwunn911 on 2007-07-15
Hey all, 

First i would like to introduce myself. I'm mike and just install Ubuntu Linux on my old PC last night. I have NO CLUE what i am doing. I have setup up the system so that it has a boot swap and i can log between linux and windows at start up. 

last night, while playing with linux (just clicking around) and updater popped up and asked me to update some 90 items. I said OK and the updating began. It became late so I shut down the computer, forgetting all about the updates being installed. This morning i Log onto linux to check ti out again. After i while, i remembered abot the updates so i clicked the upper righgt hand corner where there is an orange star. Upon clicking this an update manage is tarted and within seconds i get an error saying...

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

So, not knowing what to do, i figure that this may be a "packet" that need to install. So i go to System->Admin->Synaptic Pack Manager   and as soon as i click that i get another error that says..

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Can you please advise me what to do? Also, please be as amatuer as possible when explaining to me. I tried searching, but i kept seeing, $ this and other such terms i was very unfamiliar about.

thanks, 

mike.

---

### Post by starsky on 2007-07-15
> **yungwunn911 said:**
> Hey all, 

First i would like to introduce myself. I'm mike and just install Ubuntu Linux on my old PC last night. I have NO CLUE what i am doing. I have setup up the system so that it has a boot swap and i can log between linux and windows at start up. 

last night, while playing with linux (just clicking around) and updater popped up and asked me to update some 90 items. I said OK and the updating began. It became late so I shut down the computer, forgetting all about the updates being installed. This morning i Log onto linux to check ti out again. After i while, i remembered abot the updates so i clicked the upper righgt hand corner where there is an orange star. Upon clicking this an update manage is tarted and within seconds i get an error saying...

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

So, not knowing what to do, i figure that this may be a "packet" that need to install. So i go to System->Admin->Synaptic Pack Manager   and as soon as i click that i get another error that says..

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Can you please advise me what to do? Also, please be as amatuer as possible when explaining to me. I tried searching, but i kept seeing, $ this and other such terms i was very unfamiliar about.

thanks, 

mike.



Hi there :) 

Try typing this in your terminal ( Press ALT+F2, type "gnome-terminal") -

```

$ sudo apt-get -f install

```

start synaptic and see if it fixes the problem.

Post back. :)

---

### Post by yungwunn911 on 2007-07-15
alt + F2 didnt work so i went into applications and entered terminal through there. 

I typed in what you told me and recieved this.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

---

### Post by Nythain on 2007-07-15
in terminal type
sudo dpkg --configure -a

that will attempt to continue installing anything that was downloaded and stored in apt cache but wasnt able to be installed do to the interruption (in your case the shutdown)

if running just that command still doesnt help you could consider
sudo apt clean

wich will clean out the apt cache of any and all packages that have been downloaded to install... it wont uninstall things, but it starts apt back at a clean slate, wich means anythign you downloaded that didnt get installed will need to be re downloaded

---

### Post by yungwunn911 on 2007-07-15
Nythain, thanks very much! worked very well. 

I copied sudo dpkg --configure -a into the terminal, and everything started processing within the terminal. Many funtions (ie alt+f2, switching workplaces, and minizing now work again!). 

Could you please break this code down for me and tell me what it means and why you knew to choose it? 

thanks, 

mike

---

### Post by starsky on 2007-07-15
glad you fixed it :)

As nythain pointed out, that would have been your second solution if apt -f install didn't work which it didn't :)

apt-get is a terminal based front-end to dpkg.
usually if things can't be fixed from apt-get, dpkg usually does the magic. :)

to read about them, do 

$ man dpkg
the press "/" and type "--configure" and read it.

to read about apt-get do
$ man apt-get 
then press "/" and type "-f"

Both the commands try to fix broken packages but dpkg way is little more complicated as it goes one level deeper than apt-get.

HTH.

---

### Post by Old Pink on 2007-12-15
[http://www.topicalmatt.com/14-12-2007/howto-update-and-shutdown-in-ubuntu](http://www.topicalmatt.com/14-12-2007/howto-update-and-shutdown-in-ubuntu)

Logos, scripts, downloadables. :) 

Seems to be what you're looking for.

---

