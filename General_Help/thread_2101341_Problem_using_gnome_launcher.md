---
title: "Problem using gnome launcher"
date: 2013-01-04
forum: General Help
---

### Post by Nigirim on 2013-01-04
Hello

I want to make a launcher, which I created with 
```
gnome-desktop-item-edit Desktop --create-new
``` for my Bash script.

The script works perfectly as long as I start it in the terminal using ```
./scriptname
```but if I want to start it using my launcher I get something like
```
 ideasUnvToFoam command not found
```I'm using OpenFOAM 2.1.0 on Ubuntu 12.10 and allready edited my .bashrc.
OpenFOAM runs perfectly fine by typing all commands manually and also using bash scripts run from the terminal.

Just running my script using a launcher doesnt work

Did I miss something like an not only changing .bashrc?

Thanks in advance

/Edit says:

If I run echo $PATH in my terminal i get 
```

/opt/paraviewopenfoam3120/bin:/home/nigirim/OpenFOAM/nigirim-2.1.0/platforms/linux64GccDPOpt/bin:/opt/site/2.1.0/platforms/linux64GccDPOpt/bin:/opt/openfoam210/platforms/linux64GccDPOpt/bin:/opt/openfoam210/bin:/opt/openfoam210/wmake:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```
But if I run echo $PATH per launcher i get
```

/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```

---

### Post by Nigirim on 2013-01-09
Any ideas how to fix my problem?

---

### Post by Nigirim on 2013-01-11
For those who will somehow find the thread facing the same problem as me
This link helped me fix my problem
[http://ubuntutechnical.wordpress.com/2011/12/02/calling-shell-script-from-unity-launcher/](http://ubuntutechnical.wordpress.com/2011/12/02/calling-shell-script-from-unity-launcher/)

Nigirim

---

