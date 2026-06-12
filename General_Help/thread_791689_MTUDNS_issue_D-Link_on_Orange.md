---
title: "MTU/DNS issue? D-Link on Orange"
date: 2008-05-12
forum: General Help
---

### Post by brendanpiater on 2008-05-12
EDIT 2008/05/19

Well who knows how but it's working. Think I will be using this online time to find a new service provider....


####

Hi All,

After much frustration I've decided to post to the most helpful community I know :)

So Orange Broadband, anyone who lives in the UK knows by now they they worst...don't even ask why I have to still use them... it's a long story and I'm stuck with them for now...gggrrr.

I have a D-Link 2740B Wireless Broadband router, which in general I'm happy with except for the fact that I can't seem to connect to Internet with it. Not a great situation.

I can sync, connect to and browse the Internet via an older router so all "seems" good on the line/ISP side. Wireless went on this router so bought the D-Link. However if I connect the new router to same socket, same settings, I can sync, ping urls and IP addresses but cannot browse web pages. 

Google is ok and one or two others but 99.9% will not open in a browser although one can ping the URL, so DNS resolves.

If I change from PPPoA to PPPoE without rebooting router, and adding my own dns settings to my PC (say opendns), I can browse and connect to the Internet as per normal with the new router.

So what I've deduced from various forum posts is that this may initially be a MTU issue made worse by some sort of DNS issue when playing around with the router/adsl settings? 

Help! 

Would love some input on any test's I could run to nail down the problem and hopefully solve it.

Thanks in advance.

Cheers
B

Ubuntu 7.10

---

### Post by canadiandude007 on 2008-05-20
Hello,

I've found a similar problem with Orange using a Zoom router.

Taking a look at: [http://help.orange.co.uk/resultDisplay.do?gotoLink=161&docType=1006&contextId=406:161.212&docPropValue=kb193&clusterName=DefaultCluster&contentId=f6101e62-d437-4e53-b850-85d39887db5a&responseId=7fc004a3f2245237:100ebec:11a05fc3fb2:579c&groupId=1&answerGroup=1&score=578&page=http://ESERVER_6904428f-0486-422d-907c-12a1e8338d9e.xhtml&result=0&excerpt=mail+servers+dns+servers+IP+address+router+settings&resultType=5002#Goto161](http://help.orange.co.uk/resultDisplay.do?gotoLink=161&docType=1006&contextId=406:161.212&docPropValue=kb193&clusterName=DefaultCluster&contentId=f6101e62-d437-4e53-b850-85d39887db5a&responseId=7fc004a3f2245237:100ebec:11a05fc3fb2:579c&groupId=1&answerGroup=1&score=578&page=http://ESERVER_6904428f-0486-422d-907c-12a1e8338d9e.xhtml&result=0&excerpt=mail+servers+dns+servers+IP+address+router+settings&resultType=5002#Goto161)

Have you made the recommended changes of the above document?

Does your Internet connection fail now and then or all the time?

I've had to add DNS entries to my router, as it does not seem to pick up dynamic DNS from Orange.

Let me know.

---

### Post by canadiandude007 on 2008-05-21
Hello,

This issue certainly seems to be with DNS resolution.  I think this might affect more than Orange with anyone using ADSL router connections to the Internet.

It looks like the router will override entries in the /etc/resolv.conf file, but these can be superceded by modifying the /etc/dhcp3/dhclient.conf 

Looks like a bug in the debian package with Gutsy 7.10 of Ubuntu.

Check more here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462570](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462570)

For a temp fix, try adding ...

supercede namesever <ip of dns>, <ip of other dns>;

to the /etc/dhcp3/dhclient.conf file.

Or you can also make changes to the /etc/resolv.conf file.

Or even better, find a DNS server to add to your router DNS table that is not Orange.

Cheers,
CanadianDude007

---

