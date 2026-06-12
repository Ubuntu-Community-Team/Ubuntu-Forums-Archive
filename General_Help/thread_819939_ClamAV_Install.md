---
title: "ClamAV Install"
date: 2008-06-05
forum: General Help
---

### Post by Greenbean209 on 2008-06-05
I needed a anti virus and I was recommended to ClamAV, I installed it through the "sudo apt-get install" command and as far as I know the install went fine. And then I ran into a problem... I sat there for a second and thought how do i run it? I don't know what happened but i guess it doesn't exist. anyways I was wondering if anybody could give me a guided installation of clamav.

---

### Post by SunnyRabbiera on 2008-06-05
Well generally you dont have to worry about viruses in Ubuntu.
But if you want to protect your windows shares and stuff clam is pretty good.
but by default its a command line application, but there are frontends.
The one I use for windows shares is called klam.

---

### Post by deltaprime on 2008-06-05
you most likely installed the shell version so open a command promt and type in
> clamav

delta

---

### Post by deltaprime on 2008-06-05
i checked it out you will have to apt-get install clam-daemon and clam-data
trying it out just for you hang on

---

### Post by deltaprime on 2008-06-05
actually i just found this for you 

[http://linuxhelp.blogspot.com/2005/10/clamav-free-anti-virus-solution-for.html](http://linuxhelp.blogspot.com/2005/10/clamav-free-anti-virus-solution-for.html)

good luck

delta

---

### Post by deltaprime on 2008-06-05
> clamscan is the scan command but it will go through your user dir only 
> clamscan -h will give you the helpfile for it so you will find all your info there

---

