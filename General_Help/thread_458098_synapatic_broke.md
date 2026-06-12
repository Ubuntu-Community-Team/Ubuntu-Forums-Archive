---
title: "synapatic broke"
date: 2007-05-29
forum: General Help
---

### Post by dan171717 on 2007-05-29
i install feisty last night it installed fine after it had installed i went into synaptic and installed beryl
i also later treied to install virtual box with no luck. now when i load synaptic it says

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


is there anything i can do

---

### Post by Crafty Kisses on 2007-05-29
> **dan171717 said:**
> i install feisty last night it installed fine after it had installed i went into synaptic and installed beryl
i also later treied to install virtual box with no luck. now when i load synaptic it says

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


is there anything i can do

Try to manually get the lists, let's just see if you still get the error.

```
apt-get install synaptic / sources.list
```

---

### Post by dan171717 on 2007-05-29
i get this in the root terminal

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by zvacet on 2007-05-29
```
sudo apt-get --purge remove file_name
```

---

### Post by dan171717 on 2007-05-29
> **zvacet said:**
> ```
sudo apt-get --purge remove file_name
```

still get


```
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
```

---

### Post by dan171717 on 2007-05-29
.

---

### Post by Crafty Kisses on 2007-05-29
This is quite strange, I'll guess you'll have to reinstall the Synaptic Packet Manager, I'll try to look into this further.

---

### Post by dan171717 on 2007-05-30
> **Codename said:**
> This is quite strange, I'll guess you'll have to reinstall the Synaptic Packet Manager, I'll try to look into this further.

my beryl broke to so i reinstalled Ubuntu.i did not format the partion so when i reinstalled nothing happened:( i reinstalled again a diffrent way so it works now.

p.s. apt-get didn't work either so i had to reinstall

---

### Post by Crafty Kisses on 2007-05-30
> **dan171717 said:**
> my beryl broke to so i reinstalled Ubuntu.i did not format the partion so when i reinstalled nothing happened:( i reinstalled again a diffrent way so it works now.

p.s. apt-get didn't work either so i had to reinstall

The command line method should of worked, that's what boggles me, but you say it works now?

---

### Post by dan171717 on 2007-05-30
i reinstalled ubuntu

---

### Post by bubbafrye on 2007-06-10
I too have a damaged virtualbox install.  (virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb)

I attempted the steps here:  [https://answers.launchpad.net/update-manager/+question/5811 ]("https://answers.launchpad.net/update-manager/+question/5811")

but no luck.

from my console:
```


chuck@Chuck-Norris:~$ sudo apt-get --purge remove virtualbox
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chuck@Chuck-Norris:~$ sudo dpkg --configure -a
chuck@Chuck-Norris:~$ sudo apt-get --purge remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
chuck@Chuck-Norris:~$ 


```

at this point, I don't mind putting virtualbox on hold - but a busted apt-get is not nice.  

any other suggestions?

---

### Post by zvacet on 2007-06-10
Remove it manualy.Use this commands to find where virtualbox is

```
whereis virtualbox
```

or 

```
locate virtualbox
```

and go to the every direcory 
```
cd /folder_where_virtualbox_is
```

```
sudo rm -r file_name
```

 file_name = exact virtualbox file name in directory

---

### Post by bubbafrye on 2007-06-10
thanks fro teh tip.

I was able to solve the problem via this method found at [http://ubuntuforums.org/showthread.php?t=367515&page=2]("http://ubuntuforums.org/showthread.php?t=367515&page=2")

> 

1) use the following command to open nautilus with root privileges:
sudo nautilus

2) open the file:
/var/lib/dpkg/status

3) search for "virtualbox" you should find the following lines:
Package: virtualbox
Status: install reinstreq half-installed
Priority: optional
Section: misc
Version: 1.3.6_Ubuntu_edgy

4) Remove these lines from the file and save




big thanks to bigyoy and zvacet

---

### Post by ramjet_1953 on 2007-06-10
How did you initially install virtualbox?

It isn't in the repositories, that's why Synaptic can't find it.

Did you use AutoMatix or did you download a package from the VirtualBox website?

Regards,
Roger :cool:

---

### Post by arnieboy on 2007-06-10
The OP needs to run the following two commands to fix apt:
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```
```
sudo apt-get update
```

---

### Post by fabian_v on 2007-10-11
> **bubbafrye said:**
> thanks fro teh tip.

I was able to solve the problem via this method found at [http://ubuntuforums.org/showthread.php?t=367515&page=2]("http://ubuntuforums.org/showthread.php?t=367515&page=2")



big thanks to bigyoy and zvacet

Thank you so much for this solution. You spared me a lot of effort!

---

