---
title: "Can't get on line"
date: 2007-02-15
forum: General Help
---

### Post by txmsgt on 2007-02-15
[FONT="Tahoma"][/FONT]
Heeeeelp!!!!
I am having a problem getting on line. I can install ubutu all right and get updates just fine. However, for some reason I cannot connect to the internet via Firefox. I have put all the DNS numbers I can find but to no avail. I am running Ubuntu 6.06 through a Linksys
begw11S4 and a GT701-WG DSL modem on QWest. I have called QWest several times and all they tell me is they cannot help because they are trained in Linux, just windows. How sad! When I type a URL in it tries to connect but times out. I really want to get on line with Ubuntu because I hate Windows. I know that I must keep it because I have some programs that will run on Windows only. Anybody got a solution? Hope so.

txmsgt

---

### Post by frafu on 2007-02-15
I have moved this thread to the General Help Forum.

Have a nice day.

---

### Post by mrmonday on 2007-02-15
Can you get onto websites by typing their IP address? try 64.233.167.99 this should get you to google. Does it work? If so try typing about:config into the address bar, in the filter box, type ipv6, double click the only value there. You should now be able to access the internet.

---

### Post by gvscornish on 2007-02-25
> **mrmonday said:**
> Can you get onto websites by typing their IP address? try 64.233.167.99 this should get you to google. Does it work? If so try typing about:config into the address bar, in the filter box, type ipv6, double click the only value there. You should now be able to access the internet.
I've been having trouble getting on to some websites for months - it was doing my head in until I googled the question, was redirected here, tried your solution of disabling ipv6 and...

YIPPEE!

Thank you so much.

Have you any idea why this problem would suddenly happen when it had been fine for a while? 

(i.e. I'm surfing away, able to connect to all the sites I need and then:  Oh No! I can't get to Google or something else very well known.)

This sometimes happens to me on a Sunday afternoon and stays like it until Monday morning - UK user, phone coop ISP, dapper on a thinkpad, resident geek baffled...

---

### Post by mrmonday on 2007-02-26
Do you use a router to access the Internet?

If you do is it set to do automatic firmware updates? New firmware could prevent your Internet access, with ipv6. As for why it only did it on Sundays, I'm baffled, it could be anything.

---

### Post by pcarlton on 2007-03-04
Thank you. I ran into the same problem after I updated to the latest version of Firefox (1.5.0.10). Disabling IPV6 worked. As a workaround, I installed Konqueror and was able to get to this forum. :) 

Cheers!

> **mrmonday said:**
> Can you get onto websites by typing their IP address? try 64.233.167.99 this should get you to google. Does it work? If so try typing about:config into the address bar, in the filter box, type ipv6, double click the only value there. You should now be able to access the internet.

---

### Post by mrmonday on 2007-03-04
When did you update firefox? The latest version is 2.0.0.2, or did you choose not to upgrade?

---

