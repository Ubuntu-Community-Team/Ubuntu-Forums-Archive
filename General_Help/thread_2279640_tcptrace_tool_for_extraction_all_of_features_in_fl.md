---
title: "tcptrace tool for extraction all of features in flows"
date: 2015-05-25
forum: General Help
---

### Post by almehrdad on 2015-05-25
i want to extract all features in the isot botnet dataset uses tcptrace instruction .
what is instruction that extract all of features and save all of them into document file or excel file ?

for example: tcptrace -lr test.pcap

But this is not enough to do my job.
[B]

please help me.[/B]

---

### Post by dragonfly41 on 2015-05-25
[http://manpages.ubuntu.com/manpages/hardy/man1/tcptrace.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/tcptrace.1.html)


[http://etc-hosts.blogspot.co.uk/2012/08/tcptrace-introduction.html](http://etc-hosts.blogspot.co.uk/2012/08/tcptrace-introduction.html)


install wireshark GUI and follow tutorial.

---

### Post by almehrdad on 2015-05-26
[B]I've read all the available resources.

[/B]
**I want extract all of feature from broken pcap file and split bot stream(malicious) from non malicious .**
**what is instruction(command- line) for extraction all of features.**
[B]what is better( argus-client or tcptrace) for extraction?

[/B]
[B] please help

i am confuse.
[/B]

---

### Post by dragonfly41 on 2015-05-26
Information is out there .. just google ..

**re:** I want extract all of feature from broken pcap file ...

[https://f00l.de/pcapfix/](https://f00l.de/pcapfix/)

[http://sourceforge.net/projects/pcapfix/](http://sourceforge.net/projects/pcapfix/)

[http://www.netresec.com/?page=SplitCap](http://www.netresec.com/?page=SplitCap)
...

**re:** what is better( argus-client or tcptrace) for extraction? ...

[https://sites.google.com/site/cyberforensictools/tools-for-network-connections/command-line](https://sites.google.com/site/cyberforensictools/tools-for-network-connections/command-line)

Perhaps try tcpflow? It is in Ubuntu Software Centre.

[http://linux.about.com/cs/linux101/g/tcpflow.htm](http://linux.about.com/cs/linux101/g/tcpflow.htm)

> tcpflow can also rebuild flows from data captured with 'tcpdump -w'.

---

### Post by almehrdad on 2015-05-30
Not helpful

---

### Post by dragonfly41 on 2015-05-30
Please explain *why* "the previous post was not helpful". 

e.g. exactly what "features" to you want to extract from broken pcap file.

*Why* does wireshark and pcapfix not help you?

Then we can give more helpful replies.

---

