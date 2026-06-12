---
title: "Unity &quot;login&quot; or &quot;welcome&quot; screen. 12.04"
date: 2012-12-10
forum: General Help
---

### Post by tekhammer on 2012-12-10
For security reasons, I do not wish all usernames to be displayed on system boot up.
I only wish the old, familiar field "user" with a blank field.
And the old, familiar (also blank) field "password".

In previous versions of Linux and other OS's, this option has always been available.
I'm sure there is a simple solution.

Thanks in advance for your answers.

---

### Post by CaptainMark on 2012-12-10
Ubuntu's login manager does this by default, I don't know of any comprehensive lightdm theme collections so I'd recommend switching to gdm or mdm, this link will help you with mdm, [http://www.webupd8.org/2012/05/install-mint-display-manager-mdm-in.html](http://www.webupd8.org/2012/05/install-mint-display-manager-mdm-in.html) its written for Ubuntu 12.04 you don't have listed which version your using but the method shoudln't differ drastically for 12.10, gdm is the official repos but I'm not familiar with its newest version and I don't know how much it offers in the way of customisation

---

### Post by tekhammer on 2012-12-12
Captain mark (or anyone who can help)

I've successfully installed GDM on my 12.04 (Desktop, i386), and it does give me an "other" feature.
That helped. what I need to know now? 
How do I customize it? 
in 11.04, there was an app called "login screen" which had a check box
"show list of users"
This is what I DON'T want to see, so I'd always uncheck the check box.

Anyone, got any ideas, perhaps there is a command line alternative...that's fine. Please advise.

---

### Post by CaptainMark on 2012-12-12
I know mdm has this feature, sorry I havent used gdm for some time

---

### Post by dcstar on 2012-12-13
> **tekhammer said:**
> For security reasons, I do not wish all usernames to be displayed on system boot up.
I only wish the old, familiar field "user" with a blank field.
And the old, familiar (also blank) field "password".

In previous versions of Linux and other OS's, this option has always been available.
I'm sure there is a simple solution.

Thanks in advance for your answers.

I can't remember if this tool has a setting for that, but you might want to give it a try:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Cheesemill on 2012-12-13
There was no need to switch display managers, this can be done using the default LightDM.
Just edit the file /etc/lightdm/lightdm.conf and add the line:
```
greeter-hide-users = true
```

---

### Post by CaptainMark on 2012-12-13
> **Cheesemill said:**
> There was no need to switch display managers, this can be done using the default LightDM.
Just edit the file /etc/lightdm/lightdm.conf and add the line:
```
greeter-hide-users = true
```
Cool, nice little hack, run ```
sudo dpkg-reconfigure lightdm
``` to select lightdm back as the login manager for this

---

### Post by tekhammer on 2012-12-13
This is good to know. I already installed gdm. I'd prefer to use LightDM like you say. Is there a way to swith Display managers w/o uninstalling gdm?
What happens if I just uninstall gdm? I'd rather not try, it has given me some extra stuff.

One MORE question.
I'm using 12.04 desktop. which file do I VIM and what parameters do I change too..
boot w/o any gui front end? ie just a login from the bash shell?
I've done this with 11.04, installing the server from scratch. But I don't want to go through that again and I like 12.04.
also what is the command to start the gui? it used to be "startx"

Thanks everyone.


> **Cheesemill said:**
> There was no need to switch display managers, this can be done using the default LightDM.
Just edit the file /etc/lightdm/lightdm.conf and add the line:
```
greeter-hide-users = true
```

---

### Post by Cheesemill on 2012-12-13
> **tekhammer said:**
> This is good to know. I already installed gdm. I'd prefer to use LightDM like you say. Is there a way to swith Display managers w/o uninstalling gdm?
Just do what CaptainMark said a couple of posts up.
```
sudo dpkg-reconfigure lightdm
```> I'm using 12.04 desktop. which file do I VIM and what parameters do I change too..
boot w/o any gui front end? ie just a login from the bash shell?No need to edit any existing files, just run the following to create the lightdm.override file:
```
echo  "manual" | sudo tee -a /etc/init/lightdm.override
```> also what is the command to start the gui? it used to be "startx"
It still is.

---

### Post by tekhammer on 2012-12-13
Many thanks, will try.

---

### Post by tekhammer on 2012-12-19
> **Cheesemill said:**
> Just do what CaptainMark said a couple of posts up.
```
sudo dpkg-reconfigure lightdm
```No need to edit any existing files, just run the following to create the lightdm.override file:
```
echo  "manual" | sudo tee -a /etc/init/lightdm.override
```
It still is.
okay, this is a learning experience. 
a frustrating one, however. 
I ran the override (code follows) and now 12.04 (desktop i386) won't boot to the welcome screen at all. it just displays ........ endlessly. I'm able to login as root from the recovery console..so I can access the system. I can see my samba share from my laptop (which I'm obviously using to type this)
I SHOULD have checked out the code before I blindly paisted it into the command line.
So, I'm sure there is a way to undo this. 
I'm keen to learn how to config Lightdm. 
Please help, so I can boot to a gui. 
Also, startx does not work.
"
echo  "manual" | sudo tee -a /etc/init/lightdm.override

---

### Post by tekhammer on 2012-12-20
okay, I ran 
sudo dpkg-reconfigure lightdm
which got me back to gdm. 
Then I commented out # the "manual" in /etc/init/lightdm.override

---

### Post by tekhammer on 2012-12-21
HMM. Well I'm making progress, found a site
[https://wiki.ubuntu.com/LightDM#Debugging_LightDM](https://wiki.ubuntu.com/LightDM#Debugging_LightDM)

That helps, but I've not received a response to my question of a few posts ago. 

HOW do I reverse the damage done when I ran  the code
"echo  "manual" | sudo tee -a /etc/init/lightdm.override"

That Cheese mill advised I run. 
The workaround is to go back to gdm
sudo dpkg-reconfigure lightdm

I've done that. I'm looking for a way to reverse the "echo "manual...." statment above.
I just does not work.
:o
Thanks in advance for your reply.

I'm learning a lot.

Oh, and I CAN use VIM, I don't mind editing conf files myself.

---

### Post by Cheesemill on 2012-12-21
> **tekhammer said:**
> 
HOW do I reverse the damage done when I ran  the code
"echo  "manual" | sudo tee -a /etc/init/lightdm.override"
Just delete the file that the command created:
```
sudo rm /etc/init/lightdm.override
```

---

### Post by tekhammer on 2013-01-12
Thanks for all the feedback. It seem to have helped. Mark this one as resolved,
thanks.):P

---

