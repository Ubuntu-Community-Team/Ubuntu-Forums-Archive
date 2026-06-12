---
title: "How do I get NeroLinux 3.0.2.1 installed?"
date: 2007-12-25
forum: General Help
---

### Post by Pepse3 on 2007-12-25
Altho I have been using KUBUNTU Feisty Fawn 7.04 for about 7 months I haven't been in a postion to download something that is not in Add/Remove programs or through Synaptic Package Manager, until now.  I downloaded NeroLinux-3.0.2.1-x86.deb and I don't really know how to install a .deb .  I was a Mandrake/Mandriva user for 6+ years and this .deb is much different.  So, how do I install this Nero Linux in KUBUNTU?

Pepse.

---

### Post by forestpixie on 2007-12-25
I'm not sure about that particular package - but you usually can dbl click a deb package and it'll install and get dependencies it need at he time

---

### Post by ugm6hr on 2007-12-25
> **Pepse3 said:**
> Altho I have been using KUBUNTU Feisty Fawn 7.04 for about 7 months I haven't been in a postion to download something that is not in Add/Remove programs or through Synaptic Package Manager, until now.  I downloaded NeroLinux-3.0.2.1-x86.deb and I don't really know how to install a .deb .  I was a Mandrake/Mandriva user for 6+ years and this .deb is much different.  So, how do I install this Nero Linux in KUBUNTU?

Pepse.

As stated - double-click works (in Ubuntu - so presumably in Kubuntu).

Be aware that .debs need to be Ubuntu specific, since Debian .debs might not work.

---

### Post by .nedberg on 2007-12-25
Or you could use

```
sudo dpkg -i <nero.deb>
```

As a fellow Kubuntu user I would also recomend K3B if you have not tried it. I think it is just as good as Nero and I never saw a reason to install  Nero on my Linux box.

---

### Post by Pepse3 on 2007-12-25
.nedberg,

  I tried sudo dpkg -i <nero.deb> and it didn't work.  As for K3B?  I have been using it since it came with one of the Mandrake distros years ago.  I like variety.  

  As for compatibility I downloaded the 32 bit .deb file.

Later.

---

### Post by jespdj on 2007-12-25
What does "it didn't work" mean? Do you get an error message? If yes, then tell us exactly what the error message is (copy and paste it here) so that we can help you with it.

Did you try double-clicking the .deb?

---

### Post by logos34 on 2007-12-25
> **Pepse3 said:**
> I tried sudo dpkg -i <nero.deb> and it didn't work.

You mean you tried **sudo dpkg -i NeroLinux-3.0.2.1-x86.deb** ?

---

### Post by disturbedite on 2007-12-25
there is absolutely [COLOR=Red]**0**[/COLOR] reason for me to use nerolinux.  (its not free any way).  k3b kicks its butt.  and if you have a disc image format like nrg you need to burn, you can always get nrg2iso and convert it.

---

### Post by Pepse3 on 2007-12-25
jespdj & logos34, 

  I didn't post the error because I figured I would see if there was any interest  in the problem.  Might sound cruel, but to be honest, help for some of my problems tend to be ignored in Ubuntu forums.  So, I figured that if there was no concern (replies like you 2 ask) then I would just try double-click the package on my desktop and hope for the best.  So, here is the error:

 jim@jims-computer:~$ sudo dpkg -i nerolinux-3.0.2.1-x86.deb
Password:
dpkg: error processing nerolinux-3.0.2.1-x86.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 nerolinux-3.0.2.1-x86.deb
jim@jims-computer:~$ [http://www.google.com/ig?hl=en](http://www.google.com/ig?hl=en)

disturbedite,

  like I said in my previous post, I like variety  With most programs in Linux or windows, whether music, video, web browsers, or whatever I find strong and weak points in each.  Therefore I tend to have more than one piece of software that allows for this.  

Later. Pepse.

---

### Post by ugm6hr on 2007-12-25
> **Pepse3 said:**
> I would just try double-click the package on my desktop and hope for the best. 

Why not just double click?

If you don't want to...

As for the error - it is because you need to give the correct path for the file.  Try moving the file from your desktop to your "Home" Folder.  Then run the same command in Terminal.

---

### Post by zvacet on 2007-12-25
Maybe I´m wrong but it look like you didn´t download it in your home directory.If you downloaded it on Desktop then 

```
cd Desktop
```

```
sudo dpkg -i nerolinux-3.0.2.1-x86.deb
```

Same if it is in any other directory,meaning that you have to be in directory where deb file is and then install it.

```
cd /folder where deb is
```

---

### Post by Pepse3 on 2007-12-25
Thanx people, my brain took a death, and now it is working:lolflag:.  At times I treat .deb's as really foreign.  So I forgot the simple thing of sending my request to the area where the package is.  Now it is loaded and ready.

Again I thank you both.

Later. Pepse.

---

