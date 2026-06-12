---
title: "Questions about installing new software"
date: 2004-10-28
forum: General Help
---

### Post by jwb on 2004-10-28
Hi-

I'm new to Ubuntu and Debian, having used MDK/RH/Fedora for the last 3 years. I am enjoying Ubuntu.

I have two questions that I've found some conflicting answers on in Googling for results.

How to I install a .deb file? I'm assuming it's something similar to RH's *rpm -i packagename*? I want to install Bluefish. I've got the .deb.

I've read in several places about "installing from Universal". Could someone explain that a bit and detail how that is done? (Or point me to some good instructions.)

Thanks-

jwb

---

### Post by Rancoras on 2004-10-28
If you have a .deb file that you've downloaded, then

sudo dpkg -i foo.deb

is what you're looking for.

As for universe, check this out:

[http://ubuntuforums.org/showthread.php?t=179](http://ubuntuforums.org/showthread.php?t=179)

---

### Post by jwb on 2004-10-28
Wow! That was quick! Thanks,  :-P

Worked great for Bluefish. The CLI told I needed "libpcre3", so I fired up synaptic. It said there was a broken package- Bluefish. I searched for libpcre3, installed it- and Bluefish was "unbroke". :-)

Of course, now I have to get back to work, since I've got Bluefish installed.  :neutral: 

jwb

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=jwb]Wow! That was quick! Thanks,  :-P[/QUOTE]


Service time is always a good benefit.

---

### Post by Rancoras on 2004-10-28
I aim to please :)

Welcome to the forums, by the way!

---

### Post by jwb on 2004-10-28
Thanks, Rancoras and FLeiXiuS! Good to see an active forum.

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=Rancoras]I aim to please :)

Welcome to the forums, by the way![/QUOTE]


It is of our duty!  \\:D/

---

