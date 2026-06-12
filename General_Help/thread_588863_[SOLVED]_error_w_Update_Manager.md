---
title: "[SOLVED] error w/ Update Manager"
date: 2007-10-23
forum: General Help
---

### Post by PTelly on 2007-10-23
using 7.04
error when trying to initialize update Update Manager
Could not initialize the package information



A unresolvable problem occurred while initializing the package information.



Please report this bug against the 'update-manager' package and include the following error message:



'E:Type 'b' is not known on line 38 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

error when trying to initialize Add/Remove

Failed to check for installed and available applications



This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Tried the above w/ no sucess.

Thanx

---

### Post by por100pre1 on 2007-10-23
Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
cat /etc/apt/sources.list
```

copy and post the results... :-k

---

### Post by PTelly on 2007-10-23
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
b [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by por100pre1 on 2007-10-23
> **PTelly said:**
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
[COLOR="Red"]deb[/COLOR] [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

```
gksudo gedit /etc/apt/sources.list
```

Edit the last line as shown above and save. :)

---

### Post by wolanIT on 2007-10-23
At last line you have: 
```
b http://wine.budgetdedicated.com/apt edgy main
```

There must be:
```

deb http://wine.budgetdedicated.com/apt edgy main
```

edit **/etc/apt/sources.list** and correct last line.

---

### Post by PTelly on 2007-10-23
excuse my ignorance but edit what

thanx

---

### Post by por100pre1 on 2007-10-23
> **PTelly said:**
> excuse my ignorance but edit what

thanx

Use the commands I posted in my previous post and a text editor will appear. In the last line replace the first d with deb and close and save.

---

### Post by wolanIT on 2007-10-23
command in Terminal (Applications> Accesories> Terminal):

```
sudo gedit /etc/apt/sources.list
```

and than correct last line 

you have: 

b [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

there must be:

**[COLOR="Red"]deb[/COLOR]** [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

Than

command in Terminal

```
sudo apt-get update
```

and thats all.

---

### Post by por100pre1 on 2007-10-23
> **wolanIT said:**
> ```
sudo gedit /etc/apt/sources.list
```

Excuse me WolanIT, but to use sudo for graphical applications is **not** best practice. It can cause undesired effects in some files. This is the best way:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by PTelly on 2007-10-23
Works now. Thank you so much for your assistance. Hopefully I can remember/learn some of this. I did figure it out after staring for a few minutes. Really have enjoyed getting into Ubuntu and looking forward to upgrading to Gutsy.
Thanks very much for everything.

Paul

---

### Post by wolanIT on 2007-10-23
OK you have the rightness that is the better solution

---

### Post by por100pre1 on 2007-10-23
We are glad to help! 8)

---

