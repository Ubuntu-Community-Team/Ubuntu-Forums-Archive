---
title: "Can't remove Gimp"
date: 2008-05-19
forum: General Help
---

### Post by thwoom on 2008-05-19
Hey, i am trying to remove gimp but when i go to do it in synaptic, it wants to remove a ton of other things, for example Ubuntu-Desktop and others that i think are important. thank you in advance

---

### Post by thwoom on 2008-05-19
more info: i consider this very important because i am on an eeepc and need all the space i can get. Thank you

---

### Post by RATM_Owns on 2008-05-19
Did you try 
```
sudo apt-get remove gimp
```?

---

### Post by Enthralled on 2008-05-19
Enter this in your console:

```
sudo apt-get remove gimp
```

It should remove only GIMP. But if you want to also remove the libraries that come with it, and wich are unneeded when you uninstall GIMP, you should enter this command:

```
sudo apt-get autoremove gimp
```

---

### Post by thwoom on 2008-05-19
yeah i tried that but it also wants to remove ubuntu-desktop, i geuss it is not an important file though so ill just go through with it. thank you :)

---

### Post by onlyonesock on 2008-07-21
Hi
Have uninstalled Gimp as per advice given here but can't reinstall either by package manager or Terminal.

Package manager tells me:

Cannot install 'gimp'

This application conflicts with other installed software. To install 'gimp' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

Terminal tells me:

[michael@michael-desktop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gimp: Depends: libgimp2.0 (< 2.4.5-z) but 2.4.6-1ubuntu1~gutsy1 is to be installed
E: Broken packages
michael@michael-desktop:~$ ]

Can anybody gently talk me through this? 
Thanks.

---

