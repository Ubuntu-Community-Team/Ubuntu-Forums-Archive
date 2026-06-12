---
title: "Adobe connect add-in freeze in connecting page"
date: 2012-12-06
forum: General Help
---

### Post by sinaphysics on 2012-12-06
I have lots of problem in 12.10. maybe this night I'll back to 12.04. However I use a virtual class by adobe connect. I've installed "adobe flash player, adobe connect", but when I want to access my course the page freeze in connecting page. and for few seconds before the connecting page appears, It's shown that "the adobe connect add-in not installed" but I installed it manually( and maybe it's useful to mention the adobe connect is for ubuntu 10.x and later) . I've downloaded it by adobe website for Linux-32 bit and deb type. Also I'm using X.org X server as my driver for Graphic Card. what do u think about changing to Nvidia. And it's cool to say when I was in ubuntu 12.04 I just installed 'adobe flash player' without 'adbobe connect add-in' and easily was connected. I fall this problem by migration to ubuntu 12.10 ??

---

### Post by sinaphysics on 2012-12-08
I studied the Adobe connect add-in comments on its website which these ports should be open :

80,
90,
1935,
443,

I try to connect to adobe connect, I mean my class. at the same time I try to listen my network by
```
netstat -an | grep "LISTEN "
```
the result shows ```

tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN 
```. And by this command ```
nmap -v scanme.nmap.org 
```, the result demonstrate these ports are just open ```

22/tcp   open  ssh
80/tcp   open  http
9929/tcp open  nping-echo 
``` . So?

---

### Post by notbitmonk on 2013-04-18
Adobe Connect does not work in Ubuntu 12.04 and I will guess it does not work in 12.10. Check this link: [http://www.colorado.edu/oit/services/conferencing-services/adobe-connect/known-issues](http://www.colorado.edu/oit/services/conferencing-services/adobe-connect/known-issues) which contrasts with this Adobe response for upcoming support in Linux: [http://blogs.adobe.com/connectsupport/adobe-connect-9-0-2-release-notes/](http://blogs.adobe.com/connectsupport/adobe-connect-9-0-2-release-notes/).

I've tried to use it and it appears that the Adobe Connect server security configuration, as determined by the server manager, blocks us. It does not matter if you are using the add-in or just the browser. I can view the list of Meetings available to me but I can never join one. So that means that all the necessary ports are open. That means that there is no luck for us. Adobe offers a test connection at [http://na1cps.adobeconnect.com/common/help/en/support/meeting_test.htm](http://na1cps.adobeconnect.com/common/help/en/support/meeting_test.htm). I pass the test but still can't Connect.

> **sinaphysics said:**
> I studied the Adobe connect add-in comments on its website which these ports should be open :

80,
90,
1935,
443,

I try to connect to adobe connect, I mean my class. at the same time I try to listen my network by
```
netstat -an | grep "LISTEN "
```
the result shows ```

tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN 
```. And by this command ```
nmap -v scanme.nmap.org 
```, the result demonstrate these ports are just open ```

22/tcp   open  ssh
80/tcp   open  http
9929/tcp open  nping-echo 
``` . So?

---

