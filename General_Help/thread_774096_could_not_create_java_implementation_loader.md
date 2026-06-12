---
title: "could not create java implementation loader"
date: 2008-04-29
forum: General Help
---

### Post by krestensb on 2008-04-29
Hi all.

I would like to use a openoffice extension witch needs java to work. When I try to add the extension from oo I get the message: 

"could not create java implementation loader"

I then go to the oo java setup, and I can see that no java is selected. I don't know how to add one. I can't find a file that oo will accept in my java folder. 

Oo has a wiki page ([http://wiki.services.openoffice.org/wiki/Extensions_trouble_shooting](http://wiki.services.openoffice.org/wiki/Extensions_trouble_shooting)) witch talks about changing the port for java. Am I correct this needs to be done from the oo java setup? 

I have java standard edition 6, update 6 installed.

I hope someone can help.
Best regards.
Kresten

---

### Post by krestensb on 2008-05-02
I found out.

I installed openoffice.org-java-comon and then it works.

Kresten

---

### Post by saeid on 2008-05-24
> **krestensb said:**
> 
I installed openoffice.org-java-comon and then it works.


openoffice.org-java-com**m**n (with **m** is worked for me too).
confirmed

---

### Post by xjgnsdof on 2008-10-22
I, too, solved that problem by installing openoffice.org-java-common.

---

### Post by samden on 2009-07-27
I have this exact error when I try to install ooo2gd (an openoffice extension to allow you to write to Google Docs or Zoho).

I have installed the openoffice.org metapackage to ensure I have all relevant packages, and openoffice.org-java-common is the newest version. I am using Sun Java 1.6, OpenOffice.org 3.0, and Ubuntu 9.04.

Does anyone have any suggestions?

---

### Post by mdurham on 2009-08-01
> **samden said:**
> I have this exact error when I try to install ooo2gd (an openoffice extension to allow you to write to Google Docs or Zoho).

I have installed the openoffice.org metapackage to ensure I have all relevant packages, and openoffice.org-java-common is the newest version. I am using Sun Java 1.6, OpenOffice.org 3.0, and Ubuntu 9.04.

Does anyone have any suggestions?

I have the same problem with the same setup as you. What a pain! Is it something about Ubuntu? I also tried it on my Hardy install with OO 2.4 it has just the same problem.

Cheers, Mike

---

### Post by Drigy on 2009-08-21
As I have too. If you find solution to this matter, please do post it here.

---

### Post by chudder on 2009-10-01
I'm having the problem too but I already have the openoffice.org-java-common file.  

Okay, I just reinstalled and then I selected the Sun JRE in the Options-Java section.  That seems to have worked, I can now install extensions.

---

### Post by jii on 2009-10-14
I had the same problem with samden's exact setup, but now it's fixed. Here's what I did:

Checked in Synaptic that openoffice.org-java-common was installed. It wasn't, so I installed it.

Restarted OpenOffice, tried to install eVoice extension, same problem.

Opened tools, options, java, and saw no java option was listed. I clicked add, it brought up a file dialog in my home directory. I closed it, took a deep sigh of frustration, went back to my web browser for a few seconds.

Clicked back at the java option window, and lo and behold, an entry suddenly appeared for Sun JRE, and then another with accessibility support. I selected the first one and closed the box.

Tried again to install eVoice, it worked.

---

### Post by ponsfrilus on 2009-10-28
> **krestensb said:**
> I installed openoffice.org-java-comon and then it works.

Works for me too!

```
sudo aptitude reinstall openoffice.org-java-common openoffice.org-java
```

Thanks!
:KS

---

