---
title: "Update Manger problems"
date: 2007-05-31
forum: General Help
---

### Post by Booher6194 on 2007-05-31
I tried to get Wine and when I ran the terminal program and typed in "sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list"
I get this problem,


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--16:04:51--' is not known on line 1 in source list /etc/apt/sources.list.d/winhg.list, E:The list of sources could not be read.'


Can anyone help, it would be really great. Thank you.

---

### Post by taurus on 2007-05-31
There's something with your wine repos so can you post it here?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list.d/winhg.list
```

---

### Post by Booher6194 on 2007-05-31
E: Type '--16:04:51--' is not known on line 1 in source list /etc/apt/sources.list.d/winhg.list
booher@dhcppc2:~$ cat /etc/apt/sources.list.d/winhg.list
--16:04:51--  [http://wine.budgetdedicated.com/apt/sources.list](http://wine.budgetdedicated.com/apt/sources.list)
           => `sources.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:04:51 ERROR 404: Not Found.


This is what it gave me but I still cannot run the update mangaer.

---

### Post by taurus on 2007-05-31
> **Booher6194 said:**
> 
booher@dhcppc2:~$ cat /etc/apt/sources.list.d/winhg.list
--16:04:51--  [http://wine.budgetdedicated.com/apt/sources.list](http://wine.budgetdedicated.com/apt/sources.list)
           => `sources.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:04:51 ERROR 404: Not Found.


Is that really your /etc/apt/sources.list.d/winhg.list?  Looks to me like an output from a terminal, not a repo for wine!  Where do you get the info on how to create a repo for wine?

Otherwise, remove it since it's no good anyway.

```
sudo rm  /etc/apt/sources.list.d/winhg.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Booher6194 on 2007-05-31
Ok thanks but it didn't install wine and what is repo? Do you know a good way to install wine?

---

### Post by YokoZar on 2007-05-31
> **Booher6194 said:**
> 'E:Type '--16:04:51--' is not known on line 1 in source list /etc/apt/sources.list.d/winhg.list, E:The list of sources could not be read.'


Can anyone help, it would be really great. Thank you.You've made a typo somewhere.  winehg is not winehq - it seems like you're rewriting the terminal command by hand rather than using the copy/paste feature.


If you go to system->administration->Synaptic package manager, then go to settings->repositories, then go to third party software, what does it tell you?

---

### Post by Booher6194 on 2007-05-31
WineHQ- ubuntu 7.04 "feisty fawn"
WineHQ- Ubuntu 7.04 "Feisty Fawn" (source code)
WineHQ- ubuntu 7.04 "feisty fawn"
WineHQ- Ubuntu 7.04 "Feisty Fawn" (source code)

there both checked

---

### Post by YokoZar on 2007-05-31
> **Booher6194 said:**
> WineHQ- ubuntu 7.04 "feisty fawn"
WineHQ- Ubuntu 7.04 "Feisty Fawn" (source code)
WineHQ- ubuntu 7.04 "feisty fawn"
WineHQ- Ubuntu 7.04 "Feisty Fawn" (source code)

there both checkedTry removing all of them and then do the terminal command again.  Using copy/paste this time ;)

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```

---

### Post by Booher6194 on 2007-06-02
OK thany you so much for everybodys help, everything is working now. Just again thank you.

Booher

---

