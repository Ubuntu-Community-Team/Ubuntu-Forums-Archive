---
title: "Printing to Canon ImageRunner Advance C5030"
date: 2013-05-09
forum: General Help
---

### Post by olamina on 2013-05-09
I followed these instructions [http://ubuntuforums.org/showthread.php?t=1723101&p=10657848#post10657848](http://ubuntuforums.org/showthread.php?t=1723101&p=10657848#post10657848) to install this printer but have had no luck. 

When I type ```
/usr/lib/cups/backend/snmp <printer IP address>
```, I get:

```

network socket://192.168.254.4 "Canon iR-ADV C5030/5035 (UFR II)" "Canon iR-ADV C5030 69.03" "MFG:Canon;MDL:iR-ADV C5030/5035 (UFR II);CLS:PRINTER;DES:Canon iR-ADV C5030/5035;CID:;CMD:LIPSLX,CPCA,1284.4-2000;" ""
```

Which shows me that I can detect the printer. Not sure why I can't actually print anything...Job accounting *is* turned on. 

I used the "cnjatool" utility to add ID and password and when I try to print a test page nothing prints.

Thanks i advance for your help!

---

### Post by gordintoronto on 2013-05-09
What version of Ubuntu are you using? The printer is elsewhere on your network?

I have found that with recent versions of *buntu, I can run Printers (or some program with a similar name), click on "Add" or a plus-sign, select "network printer," then "yup, that one," and OK or Proceed until the printer works.

---

### Post by olamina on 2013-05-09
I'm using 12.04. Nope I tried the straightforward way and that's not working. The job accounting is what I think is throwing things off. I'm told it works with Fedora but not sure if I want to make the switch from Ubuntu to Red Hat...

> **gordintoronto said:**
> What version of Ubuntu are you using? The printer is elsewhere on your network?

I have found that with recent versions of *buntu, I can run Printers (or some program with a similar name), click on "Add" or a plus-sign, select "network printer," then "yup, that one," and OK or Proceed until the printer works.

---

