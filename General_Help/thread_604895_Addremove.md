---
title: "Add/remove"
date: 2007-11-06
forum: General Help
---

### Post by Songoty on 2007-11-06
In add/remove i type in Sun and i am trying to dwonload Jre for limewire to work, and it always pops up when i click the check mark and then download with The list of applications is not avilible, Cick on reload to reload the list. So i do, and when i try to download it agian, it pops up with teh same thing. 
what do i do?

---

### Post by LaRoza on 2007-11-06
Try running this command:

```

sudo aptitude install sun-java6-jre

```

---

### Post by Songoty on 2007-11-06
I did that command in terminal and this is waht i got

```

ben@ben-desktop:~$ sudo aptitude install sun-java6-jre
[sudo] password for ben:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for sun-java6-jre
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
ben@ben-desktop:~$ 


```

good or bad thing?

---

### Post by rsambuca on 2007-11-06
You may just need to activate some software repositories first.  Go to your top menu bar and select "System -> Administration -> Software Sources".  On the Ubuntu Software tab, make sure the universe and multiverse boxes are checked.  Then reload your repositories (you will be prompted when you close the window), then try installing again.

---

### Post by Songoty on 2007-11-06
K, so that worked, so thank you, but now there is a nother problem.
So when i click java runtime, it says
```

Cannot install 'sun-java5-bin'

This application conflicts with other installed software. To install 'sun-java5-bin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

```
So i go to the synaptic package manager, and search for java, and theres nothing!

---

### Post by LaRoza on 2007-11-06
> **Songoty said:**
> K, so that worked, so thank you, but now there is a nother problem.
So when i click java runtime, it says
```

Cannot install 'sun-java5-bin'

This application conflicts with other installed software. To install 'sun-java5-bin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

```
So i go to the synaptic package manager, and search for java, and theres nothing!

Use Java6.

---

