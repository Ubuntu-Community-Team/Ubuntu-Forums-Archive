---
title: "[SOLVED] Xubuntu problems"
date: 2008-03-23
forum: General Help
---

### Post by Rytron on 2008-03-23
Hi,
I am using Ubuntu for a month now. It is great.

I have installed Xubuntu on my old Pc. Now I am getting used to the features of Gnome. As Xubuntu has Xfce there are some differences.

[COLOR="DarkRed"]Anyway here are some problems I am having:
I cannot log in as root at startup, when I try it says 'root can not log in here'. Where can I log in as root?

How do I enable cut and paste in xubuntu desktop?

I cannot add/remove software as when I click on a software item to install it says 'need to refresh list', when I refresh list it says again 'need to refresh list' - this goes on in a neverending loop.

I want to speed up the internet connection. To do this I need to edit and save a text file (alias). however I require to be root to do this, yet I cannot get into root mode.[/COLOR]

[COLOR="DarkRed"]And another thing, I cannot select anything from the settings list - the icons are there but when I click on them i.e. Synaptic manager - nothing happens![/COLOR]

Please help!

:mad:

---

### Post by mali2297 on 2008-03-23
> **Rytron said:**
> Hi,
I am using Ubuntu for a month now. It is great.

I have installed Xubuntu on my old Pc. Now I am getting used to the features of Gnome. As Xubuntu has Xfce there are some differences.

[COLOR="DarkRed"]Anyway here are some problems I am having:
I cannot log in as root at startup, when I try it says 'root can not log in here'. Where can I log in as root?

How do I enable cut and paste in xubuntu desktop?

I cannot add/remove software as when I click on a software item to install it says 'need to refresh list', when I refresh list it says again 'need to refresh list' - this goes on in a neverending loop.

I want to speed up the internet connection. To do this I need to edit and save a text file (alias). however I require to be root to do this, yet I cannot get into root mode.[/COLOR]

[COLOR="DarkRed"]And another thing, I cannot select anything from the settings list - the icons are there but when I click on them i.e. Synaptic manager - nothing happens![/COLOR]

Please help!

:mad:

You shouldn't log in as root, use sudo/gksu instead. 

To edit a system configuration file, type
```

gksu mousepad /path/to/filename

```
in a terminal.

To troubleshoot the last problem, try
```

gksu synaptic

```
(...in the terminal.)

---

### Post by bapoumba on 2008-03-23
[Regarding root login]("http://ubuntuforums.org/showthread.php?t=716201").

---

### Post by Rytron on 2008-03-26
> **mali2297 said:**
> You shouldn't log in as root, use sudo/gksu instead. 

To edit a system configuration file, type
```

gksu mousepad /path/to/filename

```
in a terminal.

To troubleshoot the last problem, try
```

gksu synaptic

```
(...in the terminal.)


[COLOR="DarkGreen"]Hi,
I tried the methods above. Both gksu and sudo did not work. 

I input them in the terminal but nothing happened.
Then I tried su, it then asked me for the root password. I typed in root password and then my terminal prompt went to root@... thus I was then in root mode. I opened the file to edit and presto all done.

I am perplexed as to why sudo/gksu did not work. Any ideas? Also I have tried both gksu synaptic and sudo synaptic and su synaptic. None of these do anything. I can use add/remove tool.

I have discovered that when I can use su to get to root mode, I type synaptic and then I can use synaptic manager. 

Xubuntu seems much more strict than Ubuntu. I got gksudo thunar to work via first using su.
.
.
.
EUREKA!
As root I navigated to users and groups 

su
users-admin

In users and groups under in applications>>systems I ticked the box 'administrator system'. I am not as root group but I can not access most things. Also since I ticked the box 'administrator system' sudo and gksu now work fine.

Conclusion: The account I had trouble with was a second user account I set up on Xubuntu. Perhaps this is the reason for it being so restricted?

I hope this helps others using Xubuntu.[/COLOR]

---

### Post by mali2297 on 2008-03-26
> **Rytron said:**
> 
Conclusion: The account I had trouble with was a second user account I set up on Xubuntu. Perhaps this is the reason for it being so restricted?


Yes, it is only the user which is created during installation that automatically gets administrative rights.

---

### Post by bapoumba on 2008-03-26
> **Rytron said:**
> 
Conclusion: The account I had trouble with was a second user account I set up on Xubuntu. Perhaps this is the reason for it being so restricted?

I hope this helps others using Xubuntu.
Yes, that probably was the problem. On Ubuntu (and not only Xubuntu), the first account created is in the **admin** group, which grants the user rights to have root acces with sudo/gksudo. Any subsequent account is not by default in the admin group. 

Type **groups** in a terminal.

To add an account to a group:
```
sudo adduser <user_login> <group>
```
Of course from an account with admin privileges :)

Edit: Rytron, please, no color fonts all over the posts, thanks.

---

### Post by Rytron on 2008-03-26
> **bapoumba said:**
> Yes, that probably was the problem. On Ubuntu (and not only Xubuntu), the first account created is in the **admin** group, which grants the user rights to have root acces with sudo/gksudo. Any subsequent account is not by default in the admin group. 

Type **groups** in a terminal.

To add an account to a group:
```
sudo adduser <user_login> <group>
```Of course from an account with admin privileges :)

Edit: Rytron, please, no color fonts all over the posts, thanks.

Xubuntu is now purring on my 256mb ram old pc. Although is says only something like 224mb. Anyway it is still smooth running.

Is it best to just use black font on future threads? Apologies for the different coloured fonts, I though they'd help to highlight parts of a thread.

Cheers. Bye.

---

### Post by oneup on 2008-05-20
224 meg ram plus onboard graphics on old puter say 32meg = 256 !

---

