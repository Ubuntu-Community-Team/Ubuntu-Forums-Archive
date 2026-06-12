---
title: "fluent 6.2 on Ubuntu 7.10"
date: 2007-12-20
forum: General Help
---

### Post by ale.parente on 2007-12-20
Hi,

I Installed Fluent 6.2.16 on Ubuntu 7.10. The installation went fine. However, when I run fluent I get the following error message, namely:

./fluent: 1: Syntax error: Unterminated quoted string

I do not have any idea about the reason for that. Can anyone help me?

Thanks

Alex

---

### Post by geirha on 2007-12-20
Based on the error message it sounds like fluent here is a script, and that there's a syntax error on the first line. Could you post the first line? this command should output it: ```
head -1 ./fluent
```

---

### Post by Nodens on 2007-12-20
Hello, 

I try too to install fluent 6.2.16 on my ubuntu but it doesn't start. I get this error : 

```
Cannot open dump file "flprim.dmp.1119-32".

Error: Unable to open dump file
()
Error encountered in critical code section
```

Can you help me ?? 

Thanks, Nodens

---

### Post by ale.parente on 2007-12-21
Hi, Thanks for your reply..
The first line in the script is: 
#!/bin/sh

Any thought?

Alessandro

---

### Post by ale.parente on 2007-12-21
Hi,

I modified the first line of the script from #!/bin/sh
 to #!/bin/bash.. Now fluent starts but I get the following errors and warnings..


[email]alessandro@alex:~/Program_Files/Fluent.Inc[/email]/bin$ ./fluent
./fluent: line 590: rpm: command not found
./fluent: line 1543: domainname: command not found
./fluent: line 1646: /sbin/lspci: No such file or directory
sort: Warning: "+number" syntax is deprecated, please use "-k number"
sort: Warning: "+number" syntax is deprecated, please use "-k number"
sort: Warning: "+number" syntax is deprecated, please use "-k number"
/home/alessandro/Program_Files/Fluent.Inc/fluent6.2.16/cortex/lnx86/cortex.3.6.6 -f fluent (fluent "  -path/home/alessandro/Program_Files/Fluent.Inc")

So I think this is a shell problem.. but I do not know how to face it.. 

Thanks for your help

---

### Post by geirha on 2007-12-21
According to fluent.com, only suse and redhat is supported, and apparently no effort has been made from their side to make it usable on debian/ubuntu. So getting it to work in ubuntu will not be easy. You'll have to figure out what packages you need to install, and change the script yourself to match your system. The fact that it requires rpm to be installed is a bad sign, and chances are it will break your system if you install the rpm package. I'd reccomend installing redhat or suse on a seperate partition and install fluent there, or find an alternative to fluent that will work better on ubuntu.

---

### Post by Nodens on 2007-12-21
Hello, 

yes it is what I think : fluent is not supported on ubuntu. I will install a fedora on an other pc and I think it will run better. 

Thanks all, Nodens.

PS : Sorry for the bad english but I am a french student.

---

### Post by ale.parente on 2007-12-25
.. I am not sure.. I mean.. I am plyaing with the script fluent and it seems to be working.. I think I can do it...It's not fundamental that fluent is not ufficially supported.. 
I will post all the changes you need to do to make the script work on ubuntu

---

### Post by AlexVader on 2008-02-18
Hi Ale,
I am having the same problem as you... how did you change the script fluent so as to run in Ubuntu 7.10 Gutsy?

Thanks in Advance Alex

---

### Post by CapSizer on 2008-02-24
There is a simple fix for making Fluent 6.2 work on a newer Linux.  Basically the Fluent launch script does not work with bash 3.1, so what you need to do is to install bash 3.0 somewhere where you can easily get to it, and change the first line of the fluent script to use that rather than the default /bin/sh   Fluent 6.2 does not work with Fedora 6 unless you do this fix either.

---

### Post by AlexVader on 2008-03-07
Thanks a lot man...  I was begining to desperate about this...

Ok, i will try this kind of fix...

I also used to work with CFX 10.0 under Suse 10.0... but it doesn't seem to work in Ubuntu... and i REALLY need to have a cfd package in my pc...

Anyway, i think that fluent is far more complete (and less user friendly...  :-) ) than CFX 10.0.

Do you happen to know if CFX is installable in 7.10 Gutsy or in 6.10 Edgy...?

Just by curiosity....

I changed from W#$%/& to linux, well, i guess anyone knows why...  :-) and i changed from Fedora to Suse, and finally from Suse to Ubuntu when i bought my laptop... all hardware is configured out of the box...


Thanks for your time... :-)

Alex

---

### Post by AlexVader on 2008-03-12
Ok...Capizer,

That fix did the job...

I downloaded Bash 3.0 and did just that.. Fluent works fine now...

Thanx...  :-)  Do You happen to know if there is a similar fix for CFX...?

I am running in Ubuntu 7.10....  and i think that CFX 10.0 used to work fine under Ubuntu 6.10...

Alex

---

