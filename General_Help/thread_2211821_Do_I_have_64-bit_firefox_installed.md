---
title: "Do I have 64-bit firefox installed?"
date: 2014-03-17
forum: General Help
---

### Post by putz3000 on 2014-03-17
I installed Firefox using the software center but am not seeing what version (64-bit/32-bit) was installed. I am not seeing that information under options or by using the "config" or "about" commands. I am trying to figure out what version of Java I need to try and install. I am running 64-bit OS but if none of the browsers installs default to 64-bit I don't want to waste my time installing it.

Can anyone offer me some guidance in determining if I am running 32-bit or 64-bit Firefox?  Also, I am assuming the Google Chrome is a 32-bit default install just like in the Windows environment?

---

### Post by sammiev on 2014-03-18
Just go into FF then Help then Troubleshooting Information. :)

---

### Post by putz3000 on 2014-03-18
> **sammiev said:**
> Just go into FF then Help then Troubleshooting Information. :)

Unless I am missing something, the way I read that information is it is telling me what platform Firefox is running on, not identifying if firefox is a 32-bit or 64-bit install. Here is the information I am seeing: 

 	Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:27.0) Gecko/20100101 Firefox/27.0

---

### Post by deadflowr on 2014-03-18
You can run
```
apt-cache policy firefox
```
in a terminal and if it says amd64 anywhere then it is 64-bit
If it says i386 anywhere, then it is 32-bit.

Google-Chrome offers the version best suited for your system.
Be that 64-bit or 32-bit.

Edit: Completely missed this in the post before me
> Mozilla/5.0 (X11; Ubuntu; Linux **x86_64**; rv:27.0) Gecko/20100101 Firefox/27.0
x86_64 means 64-bit
or else it would probably say i386,or something like that(i686 is common now a days)

---

### Post by monkeybrain20122 on 2014-03-18
Isn't Firefox installed by default? Why would you need to install it from the Software Centre?

Incidentally if you want a package manager that shows more information about what you install you should get synaptic. Either install it from the Software Centre of from the terminal

```
sudo apt-get install synaptic
```

---

### Post by deadflowr on 2014-03-18
> **monkeybrain20122 said:**
> Isn't Firefox installed by default? Why would you need to install it from the Software Centre?


 I glazed over and missed that, I feel I now have to go back and find Waldo.
(or something)
I thought I read this thread, but maybe I just stared at the screen.
(Then started randomly typing coherent statements)

---

### Post by Yellow Pasque on 2014-03-18
> **putz3000 said:**
> Also, I am assuming the Google Chrome is a 32-bit default install just like in the Windows environment?

That's a bad assumption. Chrome is not in Ubuntu's repos, so there is no "default" install. Chrome's download page offers 32-bit and 64-bit versions, and if you're using a PPA, you will get the 64-bit version unless you explicitly get the 32-bit one (something like 'apt-get install chrome:i386').

---

### Post by vasa1 on 2014-03-18
> **putz3000 said:**
> ...
 	Mozilla/5.0 (X11; Ubuntu; **Linux x86_64**; rv:27.0) Gecko/20100101 Firefox/27.0

So you have the 64-bit version.

I have

Mozilla/5.0 (X11; **Linux x86_64**; rv:29.0) Gecko/20100101 Firefox/29.0

And for Google Chrome, it's

Mozilla/5.0 (X11; **Linux x86_64**) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/33.0.1750.117 Safari/537.36

---

### Post by 3rdalbum on 2014-03-18
64-bit Ubuntu comes with 64-bit Firefox.

You can take my word for it. A default install of Ubuntu 64-bit does not include the basic 32-bit libraries needed to run 32-bit applications. Also, the Firefox package is just 'firefox', if it was 32-bit the package name would be 'firefox:i386'.

---

### Post by plucky on 2014-03-18
> I am not seeing that information under options or by using the "config" or "about" commands. 

Try ```
about:buildconfig
```

Good Luck

---

### Post by Vaphell on 2014-03-18
another way to skin the cat:

firefox binary is /usr/lib/firefox/firefox, so
```
$ file /usr/lib/firefox/firefox
/usr/lib/firefox/firefox: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```

---

### Post by putz3000 on 2014-03-19
Thank you all for your help. I believe the apt-cache command answered my Firefox problem. As to the issue of installing Firefox vs already installed by defualt, it is because I installed elementary on one of my computers which is running on an Ubuntu base but is not just a recycled Ubuntu product. I have been an Ubuntu user in one form or another since 6.04 or 6.10 and have always found the Ubuntu forums to be one of the best sources of information and help. I cannot see myself using anything but Ubuntu other than perhaps an Ubuntu connected distro. I hope you all do not mind that I asked for help with a "based on distro" as upposed to a full Ubuntu distro. If so I appologize but do want to say thank you.

---

### Post by vasa1 on 2014-03-19
> **putz3000 said:**
> ... I hope you all do not mind that I asked for help with a "based on distro" as upposed to a full Ubuntu distro. If so I appologize but do want to say thank you.
Well, I would think it's better to be upfront mainly so that people don't get puzzled. There's a section for other OS/distros and it's totally legit and people help out there as well.

---

