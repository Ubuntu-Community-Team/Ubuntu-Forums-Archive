---
title: "Grubconf missing from package list????"
date: 2005-05-09
forum: General Help
---

### Post by Steve_187 on 2005-05-09
Hey, I'm very new to Ubuntu so I appologise in advance for my lack of knowledge.

I recently installed Warty on my computer along side Windows XP (that was after attempting to install Hoary but ended up with a command line instead of the GUI). After successfully installing Warty from a CD which I downloaded I went to upgrade to Hoary by changing all instances of "Warty" to "Hoary" in the repositoires.  Then after what I think was a successful upgrade to Hoary I upgraded the Linux kernel to recognise my 1GB of RAM.  

After all of this the GRUB menu has gotten quite long and doesnt look very nice.  I heard about "Grubconf" to edit the GRUB, but it's definitely not listed in my package list???  I'm pretty sure that all of the repositories are installed (including universe) because when I was using Warty I installed a MP3 plugin from the universe repository.

I would REALLY appreciate any help on this situation, I am completely stuck  ](*,) 

Thanks for any help  :smile: 
Steve.

---

### Post by bored2k on 2005-05-14
[QUOTE=Steve_187]Hey, I'm very new to Ubuntu so I appologise in advance for my lack of knowledge.

I recently installed Warty on my computer along side Windows XP (that was after attempting to install Hoary but ended up with a command line instead of the GUI). After successfully installing Warty from a CD which I downloaded I went to upgrade to Hoary by changing all instances of "Warty" to "Hoary" in the repositoires.  Then after what I think was a successful upgrade to Hoary I upgraded the Linux kernel to recognise my 1GB of RAM.  

After all of this the GRUB menu has gotten quite long and doesnt look very nice.  I heard about "Grubconf" to edit the GRUB, but it's definitely not listed in my package list???  I'm pretty sure that all of the repositories are installed (including universe) because when I was using Warty I installed a MP3 plugin from the universe repository.

I would REALLY appreciate any help on this situation, I am completely stuck  ](*,) 

Thanks for any help  :smile: 
Steve.[/QUOTE]
 [QUOTE=bored2k]Wait wait these methods are all sort of delicate , aren't they ?
I suggest you get grubconf , wich is a graphical manager for this on 
[http://www.metallikop.com/ubuntu/](http://www.metallikop.com/ubuntu/) . It will really help you avoid problems..

[img]http://img25.echo.cx/img25/7489/screenshotgrubconf6gc.png[/img][/QUOTE].

---

### Post by Firetech on 2005-06-10
[QUOTE=Steve_187]Hey, I'm very new to Ubuntu so I appologise in advance for my lack of knowledge.

I recently installed Warty on my computer along side Windows XP (that was after attempting to install Hoary but ended up with a command line instead of the GUI). After successfully installing Warty from a CD which I downloaded I went to upgrade to Hoary by changing all instances of "Warty" to "Hoary" in the repositoires.  Then after what I think was a successful upgrade to Hoary I upgraded the Linux kernel to recognise my 1GB of RAM.  

After all of this the GRUB menu has gotten quite long and doesnt look very nice.  I heard about "Grubconf" to edit the GRUB, but it's definitely not listed in my package list???  I'm pretty sure that all of the repositories are installed (including universe) because when I was using Warty I installed a MP3 plugin from the universe repository.

I would REALLY appreciate any help on this situation, I am completely stuck  ](*,) 

Thanks for any help  :smile: 
Steve.[/QUOTE]
 You should remove old, unused kernels from the computer (not only from the list) when you are absolutely sure the newer ones work... When they aren't in the list, they are unusable anyway...
You can remove kernels using synaptic (or "sudo apt-get remove --purge linux-image-[version]"

---

### Post by hanspb on 2005-06-13
From [www.metallikop.com/ubuntu/:](www.metallikop.com/ubuntu/:)

 > grubconf_0.5.1-4ubuntu2.diff.gz                 11-Mar-2005 15:50  7.2K  
 grubconf_0.5.1-4ubuntu2.dsc                     11-Mar-2005 15:50  742   
 grubconf_0.5.1-4ubuntu2_i386.changes            11-Mar-2005 15:50  944   
 grubconf_0.5.1-4ubuntu2_i386.deb                11-Mar-2005 15:50   85K  
 grubconf_0.5.1.orig.tar.gz                      11-Mar-2005 15:50  357K   

Which one should I use?

HP

---

### Post by drummer on 2005-06-13
download grubconf_0.5.1-4ubuntu2_i386.deb

then in a terminal:```
cd /path/where/file/is/
sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb
```

---

### Post by hanspb on 2005-06-13
Thanks a lot, I'll try when I get the time.

---

### Post by byen on 2005-06-15
[QUOTE=drummer]download grubconf_0.5.1-4ubuntu2_i386.deb

then in a terminal:```
cd /path/where/file/is/
sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb
```[/QUOTE]


accidentally ran into this.. but sure helped avoid a complicated procedure mentioned in another thread! thanx ;-)

---

### Post by vijaydeep on 2005-07-17
[QUOTE=drummer]download grubconf_0.5.1-4ubuntu2_i386.deb

then in a terminal:```
cd /path/where/file/is/
sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb
```[/QUOTE]

Thanks. My computer uses AMD64 (and hoary hedgeho...). And when I try to install grubconf, the terminal says:

 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 grubconf_0.5.1-4ubuntu2_i386.deb

Any suggestions?

Thanks. appreciate your help.

Vijay

---

### Post by vijaydeep on 2005-07-17
Let me rephrase. How can I get hold of a grubconf (or a good equivalent) for AMD64 ? Thanks.

Vijay

---

### Post by codejunkie on 2005-07-20
[QUOTE=vijaydeep]Let me rephrase. How can I get hold of a grubconf (or a good equivalent) for AMD64 ? Thanks.

Vijay[/QUOTE]
[http://www.metallikop.com/ubuntu/grubconf_0.5.1.orig.tar.gz](http://www.metallikop.com/ubuntu/grubconf_0.5.1.orig.tar.gz) download it and compile for your platform.

---

