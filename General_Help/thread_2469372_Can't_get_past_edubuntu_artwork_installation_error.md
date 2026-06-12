---
title: "Can't get past edubuntu artwork installation error to install anything else"
date: 2021-11-26
forum: General Help
---

### Post by dora5 on 2021-11-26
I ran into some kind of problem using the Synaptic package manager to install Edubuntu-artwork.   Now I'm not able to install anything else.  Every time I try to install anything, it tries to remove edubuntu-artwork but says there is an error processing package edubuntu+artowrpl, dpkg: installed edubuntu-artwork package post-removal script subprocess returend error exit status 127.  dpkg:  too many errors, stopping.   eventually dükg returned error code 1.   When I try to remove it in Synaptic I get the same error message. 

What do I do with it?  It won't let me remove it, reinstall it, or do anything else.

On another post about a similar problem, someone said to post the output of dpkg -l | grep edubuntu-artwork.

It gave me

rH edubuntu-artwork (in red)    15.12.1
all  edubuntu themes and artwork

I don't know what was the point of that.

Synaptic has it in red too.  Just won't remove it.

---

### Post by Bashing-om on 2021-11-26
dora5; Hey -

As we have:
> 
 [color=red]rH[/color] edubuntu-artwork (in red) 15.12.1

Let's take this approach and see what the package manager has to say:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```

see where we go from here.

---

### Post by dora5 on 2021-11-26
It's fixed.  i did 

sudo rm /var/lib/dpkg/info/[package_name].*
sudo dpkg --configure -a
sudo apt-get update


and then 


sudo apt-get install --reinstall dpkg


which said it removed edubuntu-artwork.


Then I successfully installed something.

---

### Post by Bashing-om on 2021-11-26
dora5 : Yay :D

You do good work.

-if at fist you do not succeed --- do something else

---

