---
title: "need help software management system"
date: 2008-05-01
forum: General Help
---

### Post by spokes18 on 2008-05-01
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I am new with Linux. I tryed and I keep on getting errors. I looked in the file sources.list, but if i make changes it will not save. I would appreciate any help thanks I was trying to install Cairo-dock

---

### Post by y-lee on 2008-05-01
Ok first of all check for broken packages.

Open synaptic package manager (should be under system administration)

Now click on edit and then fix broken packages. and see if it fixes anything. Now close synaptic when you are done.

Now open a terminal and type (or copy and paste) the code below:

```
sudo apt-get update
```


It will ask you for your password enter it but note it will not be displayed for security reasons.

Now enter the code below into the terminal


```
sudo apt-get install -f
```


This will also ask for a password as above.


In theory that should help with the broken packages stuff. If not post any error messages here and also post if ya need help installing Cairo-dock :)

---

### Post by spokes18 on 2008-05-01
y-lee thanks for the help but when I open the synaptic package manager a err comes up:

E: Type '“deb' is not known on line 62 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
“deb [http://cairo-dock.vef.fr/ubuntu](http://cairo-dock.vef.fr/ubuntu) gutsy cairo-dock”

and when i try and delete it and save the file it will not let me.

and i have to close the package manager any more help will be appreciated

---

### Post by y-lee on 2008-05-02
Ok sorry about the delay I actually had to go to work. :lolflag:


By the looks of things your sources.list file is corrupted.

> and when i try and delete it and save the file it will not let me.


this is a system file so you can not edit it or delete it unless you are root or a super user. First we make a backup copy just in case. (all code below here is typed or copied and pasted into the terminal)

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
```

Now we open it in gedit as super user so we can edit it:


```
gksudo gedit /etc/apt/sources.list
```

Now delete the line below (note later to install cairo-dock we might have to add a line like this back but first i wanna get synaptic working again :) )


> **&#8220;deb [http://cairo-dock.vef.fr/ubuntu](http://cairo-dock.vef.fr/ubuntu) gutsy cairo-dock&#8221;**

Now uncomment all lines that start **# deb**. This means removing the **#** character. I would also delete the lines "**# Line commented out by installer because it failed to verify:**"

Note also it is up to you if you wish to uncomment the partner lines below:

```
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner
```

The deb lines in your sources.list file should look like the below:


```
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main 
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Now save this file and close gedit

Now update the repos

```
sudo apt-get update
```


If this command works Synaptic should be ok. You can try opening it and trying the commands and info given above. 

If this doesn't work post back with all error messages. Also post your entire **sources.list** file by opening it in gedit and copy and paste it all here in your post. It helps for readability purposes to put code tags around all error messages and files posted here. You can do that by high-lighting text and then clicking the **#** character at the top of this text area box.

---

### Post by spokes18 on 2008-05-02
y-lee thanks for the help the last line was the problem removed the " at the beginning and end and it worked thanks for the help

---

