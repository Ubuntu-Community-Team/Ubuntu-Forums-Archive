---
title: "Numix Circle Icon Theme doesn't work"
date: 2014-08-12
forum: General Help
---

### Post by UncleMonty on 2014-08-12
I'm using ubuntu 14.04 
I installed the application and added the ppa. 

It doesn't even load. 

Is there anything I can to do to get it to work?

---

### Post by Frogs Hair on 2014-08-12
I have been using the Numix PPA set since 14.04 was released . There are two circular  sets , both from the Numix Project. You may want to open Nautilus as root and check permissions, but that has never been a problem here.

---

### Post by UncleMonty on 2014-08-12
What's the other PPA please? How do I get to check the permissions?

---

### Post by nerdtron on 2014-08-12
> I'm using ubuntu 14.04 
I installed the application and added the ppa. 
How did you added the PPA? GUI or via command line? what command did you use? Did you update the repository afterwards? How did you installed the numix icon set?

> It doesn't even load. 
How do you confirm that it doesn't even load?

---

### Post by UncleMonty on 2014-08-12
I added the ppa via the command line (the one provided in software centre) and then ran sudo apt-get update and sudo apt-get upgrade. 

I installed the theme set via the software centre. 

If I click on the icon in the launcher - nothing happens.

---

### Post by Frogs Hair on 2014-08-12
The other set is named Numix Bevel and both sets are from the Numix Project.

I notice that the standard Numix icons are also installed and may be required for the set to work. Try the following command.

```
sudo apt-get install numix-icon-theme
```

---

### Post by UncleMonty on 2014-08-13
I deleted it and got a refund.

---

