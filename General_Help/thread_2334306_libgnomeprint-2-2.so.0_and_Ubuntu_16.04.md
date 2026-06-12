---
title: "libgnomeprint-2-2.so.0 and Ubuntu 16.04"
date: 2016-08-18
forum: General Help
---

### Post by flavio_ on 2016-08-18
Hi, 

I running Ubuntu 16.04 and trying to install Stata. 

Trying to load Stata, this is the message I receive: 

***/xstata: error while loading shared libraries: libgnomeprint-2-2.so.0: cannot open shared object file: No such file or directory***


When I try to install libgnomeprint, this is the output: 

[I][B]~# sudo apt-get install libgnomeprint-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgnomeprint-2.0
E: Couldn't find any package by glob 'libgnomeprint-2.0'
E: Couldn't find any package by regex 'libgnomeprint-2.0'
[/B][/I]
How can I solve this? 

Thanks in advance,

---

### Post by steeldriver on 2016-08-18
libgnomeprint-2.0 appears to have been removed from the repositories after 12.04


If you want help moving forward then please provide some information about the software you are trying to install (what it is, where you got it, how you installed it)

---

### Post by flavio_ on 2016-08-18
Yes, exactly: it has been removed from repositories. But is there anything I can do to have access to it? [Remember, I'm a newbie :-)]

Stata is an statistical package. And I have been following online instructions to install it on my computer. It worked fine with Ubuntu 14.04

And did this before. But right now, it's not working. 
[I][B]Update 08/11/2014 
Dave Dixon had trouble installing  Stata 12 on Ubuntu 14.04 because libgnomeprint wasn&#8217;t in the  repositories. It&#8217;s easily solvable. He writes:[/B][/I]

[INDENT]***Ubuntu 14.04 eliminated libgnomeprint, so I had to add***
***deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) code_name main restricted universe multiverse***
***to my apt-get libraries.***

[/INDENT]

---

### Post by mook765 on 2016-08-18
As far as I see, libgnomeprint-2.0 is not in the Ubuntu repositories.
Stata is commercial software.
Assuming that you purchased a legal copy off Stata it might be the best to contact the Stata Support at
[http://www.stata.com/](http://www.stata.com/).
Kind regards...

---

### Post by flavio_ on 2016-08-18
Yes, I know Stata is a commercial software, but my point is about lilibgnomeprint-2.0. 

I did the procedure that I mentioned and it worked for Ubuntu 14.04. Why it isn't working for Ubuntu 16.04? 

Best,

---

### Post by mook765 on 2016-08-18
The reason that it don't work anymore is possibly that you are going to use a software which might be a bit out of date.
About the package you are missing you should look here:
[https://launchpad.net/ubuntu/+source/libgnomeprint/2.18.8-3ubuntu1](https://launchpad.net/ubuntu/+source/libgnomeprint/2.18.8-3ubuntu1)
Maybe you can get it to work...
Good luck...

---

