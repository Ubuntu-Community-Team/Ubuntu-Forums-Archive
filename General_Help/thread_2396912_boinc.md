---
title: "boinc"
date: 2018-07-22
forum: General Help
---

### Post by gdesilva on 2018-07-22
Just wondering whether anyone could explain the purpose of running boinc if one is not interested doing any distributed computing? I just noticed that my system is running boinc but have no clue why it should b there.

Many thanks.

---

### Post by Claus7 on 2018-07-23
Hello,

checking my system (lubuntu 18.04):
ps ux | grep boinc
lubuntu   4009  0.0  0.0  21540   980 pts/0    S+   15:29   0:00 grep --color=auto boinc

it does not seem that boinc is running, even if it seems that is there.

Regards!

---

### Post by Topsiho on 2018-07-23
Ubuntu 18.04 is called bionic.
Maybe ???  Just guessing :)
Topsiho

---

### Post by Claus7 on 2018-07-23
Hello,

> **Topsiho said:**
> Ubuntu 18.04 is called bionic.
Maybe ???  Just guessing :)
Topsiho

the OP has to do with:
[https://boinc.berkeley.edu/](https://boinc.berkeley.edu/)

which is:
> The BOINC project is located at the University of California, Berkeley. It has existed since 2002, with funding primarily from the National Science Foundation.
and
> BOINC includes client, server, and web components, and APIs for connecting other components. It is distributed under the LGPLv3 open-source license.

Regards!

---

### Post by Topsiho on 2018-07-23
Hi,

The OP says he didn't install Boinc, is not interested in distributed computing. And wonders that he seems to have Boinc running nonetheless, and asks for an explanation.
I think he mistakes Bionic for Boinc.

:)

Topsiho

---

### Post by gdesilva on 2018-07-24
Sorry for the lack of response....being busy doing other things.

The question is about Boinc and NOT Bionic. @Claus7's reading is correct.

$ ps -ef | grep boinc
boinc     1567     1  0 10:15 ?        00:00:07 /usr/bin/boinc


I did not install boinc at any stage. Did install the Boinc Monitor after I detected that boinc is running to see whether there are any active projects but none listed. Just looks a bit strange...I guess all I can do is to uninstall it and keep monitoring?

EDIT: Synaptic shows boinc-client and boinc-virtualbox were installed - removed all boinc instances. Just wondering whether boinc was installed by default by Ubuntu Studio 18.04 which is what I have.

---

### Post by Claus7 on 2018-07-25
Hello,

> **gdesilva said:**
> 

I did not install boinc at any stage. Did install the Boinc Monitor after I detected that boinc is running to see whether there are any active projects but none listed. Just looks a bit strange...I guess all I can do is to uninstall it and keep monitoring?

EDIT: Synaptic shows boinc-client and boinc-virtualbox were installed - removed all boinc instances. Just wondering whether boinc was installed by default by Ubuntu Studio 18.04 which is what I have.

I just want to inform you that from lubuntu 18.04 there is nothing installed concerning boinc in synaptic, so I guess that having uninstalled the packages in question, boinc won't be running in your machine. Someone else might be able to inform you about Ubuntu Studio.

Regards!

---

### Post by gdesilva on 2018-07-25
> **Claus7 said:**
> Hello,



I just want to inform you that from lubuntu 18.04 there is nothing installed concerning boinc in synaptic, so I guess that having uninstalled the packages in question, boinc won't be running in your machine. Someone else might be able to inform you about Ubuntu Studio.

Regards!

@Claus7, thanks for confirming the status in lubuntu for me which means it is not very likely that boinc is installed by default, although Ubuntu Studio may have taken a different approach. 

When I get a bit of time, I might do a fresh install on another system and check it out the status of boinc and will post the findings.

Thanks.

---

