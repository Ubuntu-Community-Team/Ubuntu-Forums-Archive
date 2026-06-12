---
title: "Synaptic NOT working"
date: 2007-05-31
forum: General Help
---

### Post by leopard6661 on 2007-05-31
I tried to install second life from synaptic, it didn't work so I unistalled it fro synaptic and manually installed it and it didnt work too. But now when I start synaptic I get the message :
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I tried something from a previous post:
Code
 apt-get install synaptic / sources.list

And got the following in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.


Also update manager isnt running, I am getting the following messege:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package secondlife-install needs to be reinstalled, but I can't find an archive for it.'

Now I dont know what to do
Please HELP

---

### Post by renzokuken on 2007-05-31
have you tried running 

```
sudo apt-get -f install
```

and then trying again

---

### Post by leopard6661 on 2007-05-31
Thanks for your reply
I did what you said 
And here is what I got from the terminal

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
```

---

### Post by renzokuken on 2007-05-31
have you got all the repos enabled? universe and multiverse?

---

### Post by leopard6661 on 2007-05-31
Dont know what you mean
How do I know if they are enabled?
If not how do I enable them?
I am kinda of a linux newbie:oops:

---

### Post by renzokuken on 2007-05-31
follow this guide

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

then run

```
sudo apt-get update
```

then try again

---

### Post by leopard6661 on 2007-05-31
So I checked if the universe and stuff is enabled and every thing was enabled except source code so I enabled it, then I was asked to reload list and it did and then guess what I got the same old messege:
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Anyway I then run terminal and run
```
sudo apt-get update
```

And then got the following in terminal
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty Release
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/main Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/restricted Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/main Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/universe Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/universe Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 2s (1B/s)  
Reading package lists... Done

Now I run synaptic and get the same old message:
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report. ](*,)

---

### Post by leopard6661 on 2007-05-31
Can I like uninstall then reinistall synaptic
This may help right, but I dont know how???

---

### Post by zvacet on 2007-05-31
```
sudo apt-get --purge remove file_name
```

---

### Post by cowanh00 on 2007-05-31
I have this problem since I tried to install Virtualbox. I've tried all of the instructions here and searched the forum but I've never found a resolution.

How can this problem be fixed?

EDIT: after all the searching I found the command that solved this problem without reinstalling Ubuntu: ```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by leopard6661 on 2007-05-31
FINALLY
cowanh00 you are a true life saver =D>your code worked and synaptic is up and running again\\:D/

```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```

THANKS

---

