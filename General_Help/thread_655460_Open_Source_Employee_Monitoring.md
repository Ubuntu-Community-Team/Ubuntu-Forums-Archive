---
title: "Open Source Employee Monitoring"
date: 2008-01-01
forum: General Help
---

### Post by TorchlightJay on 2008-01-01
Hey,
 I want to know if there are any tools out there that I can use to monitor employee activity on the web. You know, see if they are wasting company time or looking at crap. I thought about making a proxy server and routing all data through it. What is a good open source proxy? Maybe there is some software out there available for download that can do what i've described. It'd be nice to limit or block stuff completely. Any thoughts?

---

### Post by spd106 on 2008-01-02
You're probably going to have to use something like Squid, [http://www.squid-cache.org/](http://www.squid-cache.org/). 

There are lots of other applications that work well with Squid and you should be able to figure out what you want.

---

### Post by TorchlightJay on 2008-01-03
Well thank you for your help. I'll try that. Do you think i oughta get a book or are the online tutorials just fine?

---

### Post by spd106 on 2008-01-04
I've not gone very deep into the advanced configuration options of Squid, but from what I have seen the included and online documentation is pretty good. However, if you're not used to editing text files it might be worth investing in a book at some point.

There are several more user-friendly solutions, both open source and commercial, that use Squid. So it's probably best to go with whatever you feel most comfortable with.

---

### Post by bmathis on 2008-01-04
You can use a combination of squid, dansguardian, and iptables to send all traffic through the proxy and then filter it using dansguardian. you wont need to modify any of the work station settings except changing dhcp to use your proxy box as the default gateway. 

I wrote a tutorial awhile back to setup squid and dansguardian, the only thing youll need to do after is setup iptables (a single line) and the dhcp part.

heres the link to the tutorial : [http://www.brianmathis.net/2007/11/30/howto-squid-and-dansguardian-with-dapper/]("http://www.brianmathis.net/2007/11/30/howto-squid-and-dansguardian-with-dapper/")

edit: also, if you're not too familiar with editing files via command line, you can use webmin!

enjoy!

---

### Post by tgalati4 on 2008-01-05
I remember seeing a program that populates your desktop with random images that come floating across your subnet.

---

### Post by HermanAB on 2008-01-05
Instead of monitoring employees, it is better to use squidguard and squid-cache to block the sites you don't want them to visit and scan all downloads for viruses, then you don't need to play spy vs spy and can get on to better things in your life.

See these:
[http://aeronetworks.ca/squidguard-howto.html](http://aeronetworks.ca/squidguard-howto.html)
[http://aeronetworks.ca/willowbark-howto.html](http://aeronetworks.ca/willowbark-howto.html)

Cheers,

Herman

---

### Post by anthonyJC on 2008-01-05
yep, you can google block lists for squid and they are tight.  i couldn't get round them. they are grouped into seperate lists for each category like webmail, gambling, auctions etc. with one of these set up there's no need to spy, it's suprisingly difficult to find a site not in the lists. plus i think its' illegal to spy on employees during break periods IANAL.

---

### Post by closebeauty on 2008-01-27
What can employee monitoring software do?
Real Time Centralized Network Surveillance

With a single click you can view the desktops of every workstation on your network, in realtime. Alternatively, you can use NetVizor’s activity ticker to view a constantly-updated list of all computers on your network, showing what users are logged in, and what windows they are working with.

Comprehensive Activity Logging and Reporting

NetVizor’s logging capabilities are virtually limitless. NetVizor can log keystrokes typed, application and website usage, detailed file system usage, incoming and outgoing chats and emails, windows interacted with, desktop screenshots, internet packet data, software installations, internet connections, and much more. All activities logged can be tied together and presented in easy-to-read graphical reports.

And Remote Administration Capabilities, Built-in Content Filtering

Where are they? 
[http://www.employee-computer-monitoring.com/](http://www.employee-computer-monitoring.com/)
[http://www.monitoring-world.com/employee-monitoring-software-maxapt-quickeye.html](http://www.monitoring-world.com/employee-monitoring-software-maxapt-quickeye.html)

---

