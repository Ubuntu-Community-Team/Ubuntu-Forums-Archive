---
title: "All my Desktops Broken After Install Updates"
date: 2014-01-24
forum: General Help
---

### Post by Felix_Lugo on 2014-01-24
Hello everyone.

Yesterday I was using skype and the application gave me an error; therefore I decided to do apply the installation of 500mb in updates that i'd been delaying because some slow internet issues.

After the installation, I reboot the computer, and when logged in, the unity was messed up; and for messed up i mean it had a lot of errors that made impossible to manage the environment properly; after that I tried to resolve this issue using gnome instead of unity, but this environment was broken too.

Besides, some moths ago i had a similar problem using cinnamon but I decided to use unity instead of find a way to resolve it; now all the desktop environments are broken. 

Sorry for my English, is not my native language. I hope you can help me.  

I'm using ubuntu 12.04

---

### Post by Bucky Ball on 2014-01-24
*Thread moved to **General Help**.*

Hi and welcome to the forums. 

If this is the desktop you can get to, please open a terminal and post these two commands, one after the other, hitting return in between:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-update
```

Please post back any error messages you get by copying them from the terminal and pasting them here.

Best to keep updated, at least once a week, as these huge updates can sometimes throw things out. You would have been way behind with kernels and software. Hopefully this will sort it out. 

It's possible that a driver you've added manually for graphics may have been killed by your updates.

PS: I have attached your large image. To attach large images rather than insert them in your posts (spare a thought for those with slow connections and vision issues) go 'Adv. Reply' and use the paperclip icon.

---

### Post by Felix_Lugo on 2014-01-24
Hello Bucky Ball and thanks you for your answer. I did that what you wrote me and I got this error message:

```
E: Invalid operation dist-update
```

---

### Post by deadflowr on 2014-01-24
Typo on Bucky Ball's half. 
It should be
```
sudo apt-get dist-upgrade
```

---

### Post by Felix_Lugo on 2014-01-24
Hello deadflowr and thanks for your answer.
So I typed it in the terminal and got this message:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Felix_Lugo on 2014-01-24
nobody?

---

### Post by Bucky Ball on 2014-01-24
Did you reboot after all this and still the same problem?

(Thanks deadflowr, my mistake. Was about 6AM here. ;))

---

### Post by Felix_Lugo on 2014-01-25
Yes man, still the same problem

---

