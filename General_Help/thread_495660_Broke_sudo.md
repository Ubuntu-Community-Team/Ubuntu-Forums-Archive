---
title: "Broke sudo"
date: 2007-07-08
forum: General Help
---

### Post by volkswagner on 2007-07-08
Newbie broke sudo trying to speed up internet (maybe?)

The last thing i did was follow this post [http://www.stchman.com/conf_host.html]("http://www.stchman.com/conf_host.html")

I think i went to far by commenting out the following,

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

can this break sudo?  I can no longer use sudo to change it back.  When i enter 
```
sudo gedit /etc/hosts
```
It asks for password, after entering password it just hangs

I tried following this help to check sudoers and groups [http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")

I did not see any problems with either file

Is a reinstall in order.  I have a seperate partion for my home folder

---

### Post by smoker on 2007-07-08
i doubt you have broke 'sudo', you can always try and open another file with it to make sure it is working ok, eg, sudo gedit /etc/fstab

i think more likely you have damaged the file 'hosts', if it won't open in gedit, open nautilus with alt+f2, and type gksudo nautilus and check the file is still in etc

best of luck

---

### Post by volkswagner on 2007-07-08
Still no joy with

```
sudo gedit /etc/fstab
```

asks for password and hangs
> 
i think more likely you have damaged the file 'hosts', if it won't open in gedit, open nautilus with alt+f2, and type gksudo nautilus and check the file is still in etc

File will open but i cant save edit

---

### Post by vexorian on 2007-07-08
just try 
```
gedit /etc/hosts
```

It should open it read only, if it also freezes then it is gedit's problem (most likely an issue with the file)

I should though say that I think that the page that told you to change the configuration is not correct.

If ubuntu was slowing down when internet was connected then it is probably that bugged wireless driver issue. Perhaps changing the hosts makes that bugged driver unable to get bugged, but I am not sure. For me Ubuntu is certainly not taking 75 seconds to resolve host names...

---

### Post by volkswagner on 2007-07-08
gedit works fine

how can i use recovery to edit the file?

---

### Post by vexorian on 2007-07-08
you mean gedit has no issues opening that file?

---

### Post by volkswagner on 2007-07-08
yes

---

### Post by volkswagner on 2007-07-08
> I should though say that I think that the page that told you to change the configuration is not correct.

If ubuntu was slowing down when internet was connected then it is probably that bugged wireless driver issue. Perhaps changing the hosts makes that bugged driver unable to get bugged, but I am not sure. For me Ubuntu is certainly not taking 75 seconds to resolve host names...

After changing the file and adding the the opendns to my router settings web pages loaded much quicker.  Not sure which caused the solution though
__________________

---

### Post by r0ck80y on 2007-07-08
Does "sudo <any command>" work?? Like say "sudo su"...gets stuck there too?

---

### Post by volkswagner on 2007-07-08
> Does "sudo <any command>" work?? Like say "sudo su"...gets stuck there too?

yes, is there another way to edit the file back to original?

---

### Post by deepclutch on 2007-07-08
it may not be a sudo problem.it once happened to me in Debian Experimental system.the problem was with a package called system-tools-backend.

---

### Post by r0ck80y on 2007-07-08
I guess you need to enable root to edit the file. You can do it using a live CD. Or boot into recovery mode where root is enabled, edit the file and boot into ubuntu again.

---

### Post by volkswagner on 2007-07-08
Got it fixed

recovery>sudo nano> then put the file back as i found it.  Now it opens with sudo gedit.  the change that was required i had to un-comment out he local host ip 

Thanks to all for putting my on the correct path....sudo was not broke

ubuntu rocks

---

### Post by Cuppa-Chino on 2007-07-08
ODD this happened to me as well but my SUDO GEDIT is still broken...

I can GEDIT files

I SUDO CP and SUDO NANO

but not SUDO GEDIT

am trying the reinstall of the system tools

---

### Post by Cuppa-Chino on 2007-07-08
Even odder: sudo kate works on but sudo gedit does not...

have reinstalled gedit, have reinstalled system-backend nothing helps

user manager -- ie to add more users now also does not work anymore... getting a little better all the time...

have reinstalled kernel as well but no luck

have also reinstalled sudo & gnome control centre etc still no change

---

