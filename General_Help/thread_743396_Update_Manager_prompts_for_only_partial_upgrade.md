---
title: "Update Manager prompts for only partial upgrade"
date: 2008-04-02
forum: General Help
---

### Post by retrow on 2008-04-02
The update manager icon was flashing in the taskbar so as usual I left-clicked on it and after it read the package information, there was a prompt asking if I want to go for a partial upgrade. After I ran the partial upgrade there was another prompt which told me what the possible error might be. The only problem I have now is that each time I run the update manager, this error keeps showing up. 

[Screenshot 1]("http://nuclear-imaging.info/files/image/partial_upgrade_01.png")
[Screenshot 2]("http://nuclear-imaging.info/files/image/partial_upgrade_02.png")

Is there a way to disable automatic update checking for certain packages while running them for rest of the packages?

---

### Post by sekinto on 2008-04-02
You could try this in terminal:
> 
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade


---

### Post by retrow on 2008-04-02
Thanks. I ran the commands and it seems like the openoffice.org packages have some sort of inconsistency in them. Hopefully the repositories and lists would be updated pretty soon. ```
xxxxx@Lithium:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
[COLOR="Red"]Building tag database... Done      
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic openoffice.org-base 
  openoffice.org-base-core openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-style-human 
  openoffice.org-writer python-uno 
0 packages upgraded, 0 newly installed, 0 to remove and 16 not upgraded.[/COLOR]
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done
```

---

### Post by sekinto on 2008-04-02
Yeah, a few weeks ago I was having problems upgrading OpenOffice to, but it worked the next day.

---

### Post by calc on 2008-04-02
This should be resolved soon (in the next day or so), the openoffice.org-l10n packages haven't been uploaded yet which is what it is keeping the other openoffice.org packages held back for now.

---

### Post by Chonnawonga on 2008-04-03
I'm running into exactly the same messages. I hope this is resolved before too long.

---

### Post by calc on 2008-04-03
The problem with OpenOffice is already resolved if you are still having issues its either due to a different problem or the mirror you are using is out of date.

---

### Post by Chonnawonga on 2008-04-04
Oh! Well, it seems to have resolved itself anyway. Go figure. :P

Thanks, though!

---

### Post by hihihi on 2008-06-05
this problem keeps on coming with eveyr new update.
it is slightly irritating.
grml

---

