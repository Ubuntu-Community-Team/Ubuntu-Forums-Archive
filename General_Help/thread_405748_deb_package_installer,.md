---
title: "deb package installer,"
date: 2007-04-10
forum: General Help
---

### Post by Quartlow on 2007-04-10
I crashed it during an install of virtualbox. 

[see here]("http://ubuntuforums.org/showthread.php?p=2407422#post2407422")

Now if you try to install any deb package it says the package is corrupt.
Oh though I can copy the same package to another computer on the network and it will work fine.

Is it possible to remove the debian package installer with apt? then reinstall it with apt? If so how.

---

### Post by useResa on 2007-04-10
Have you tried doing exactly what is stated?
So, in a terminal```
sudo apt-get install virtualbox --reinstall
```

If this succeeds you can remove it by doing
```
sudo apt-get remove virtualbox --purge
```

Hope this will help you in solving this matter.

---

### Post by Quartlow on 2007-04-10
tried that and it returns this message

```
robert@robert-desktop:~$ sudo apt-get install virtualbox --reinstall
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
robert@robert-desktop:~$ 
 
```


```
robert@robert-desktop:~$ sudo apt-get remove virtualbox --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
robert@robert-desktop:~$ 
```

There has to be a place where synaptic and the deb package manager keep track of whats installed.

---

### Post by useResa on 2007-04-11
I just went back to check [your old thread]("http://ubuntuforums.org/showthread.php?p=2407422") and noticed the following:

You were given the advice to issue the following command
```
dpkg --remove --force-remove-reinstreq virtulbox
```And you reply is
>                               dpkg - warning: ignoring request to remove virtulbox which isn't installed.What I noticed is that in both the suggestion and your reply the same typo is indicated, namely virtulbox instead of virtu**a**lbox.
Based on this I assume that you have literally done the command as proposed resulting in the error you indicate.

Just for confirmation could you please try
```
dpkg --remove --force-remove-reinstreq virtualbox
```(Hope I did not make a typo ;))

Basically with the above command you are asking the package to be removed (the --remove option) and additionally force some extra requests.
The remove-reinstreq asks for a removal of a package even if it is broken and marked for reinstallation, which is the case in your situation.
If you like to know more about the dpkg command, there are many locations where you can find this. One example is [here]("http://www.abc.se/home/m10828/webgine1320e_linux/man__H_dpkg.html").

Hope this helps and will solve your problem.
Regards.

---

### Post by Quartlow on 2007-04-11
meh, no biggie. Both spellings return the same results :D 

Great link I added it to my list of info. I took the cheaters way out last night and just backed up and blew it all out and started over. That fixed it's wagon :D  :D 

I'm just rather proud of myself for stumping the community :mrgreen:  It's amazing what a dummy can break!!

---

### Post by useResa on 2007-04-11
> **Quartlow said:**
> meh, no biggie. Both spellings return the same results :D 
Too bad, I hoped that I found the issue ;)

> **Quartlow said:**
>  Great link I added it to my list of info.
Your welcome

> **Quartlow said:**
> I took the cheaters way out last night and just backed up and blew it all out and started over. That fixed it's wagon :D  :D 
Congratulations! Sorry that I could not help you fix it another way

> **Quartlow said:**
>  I'm just rather proud of myself for stumping the community :mrgreen:  It's amazing what a dummy can break!!
You are certainly not a dummy because you broke something. Trust me ... anyone can break a system.
The fact that you were able to find a solution and fix it by yourself proves to me you are certainly not a dummy.
Once again ... congratulations.

---

