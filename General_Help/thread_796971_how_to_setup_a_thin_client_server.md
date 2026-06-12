---
title: "how to setup a thin client server?"
date: 2008-05-16
forum: General Help
---

### Post by tuff3rthanu on 2008-05-16
I run Ubuntu linux hardy heron (current stable version) and just bought (I got it for $50.00 on ebay a HPt5135 really cheap. Here is the link for what it does [http://h10010.www1.hp.com/wwpc/us/en/en/WF05a/12454-12454-321959-338927-89307-3341342.html]("HP5135"). Feel free to send links of what needs to be done or tell me. Does it have it just run samba? Thanks

---

### Post by rlcomstock3 on 2008-05-16
Your link seems to be dead to me, that doesn't mean much I sometime cannot connect to specific servers with my dumb ISP...

Your question is very vague, are you asking how to set up a thin client server?  Or are you asking how to setup a windows file server.  

If it is the first...

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

Else restate your question.

---

### Post by tuff3rthanu on 2008-05-16
Thanks yes thats what I am looking to do. [http://h10010.www1.hp.com/wwpc/us/en/en/WF05a/12454-12454-321959-338927-89307-3341342.html](http://h10010.www1.hp.com/wwpc/us/en/en/WF05a/12454-12454-321959-338927-89307-3341342.html) is the link

---

### Post by PilotJLR on 2008-05-16
The thin client you bought appears to only support RDP and ICA... which means you basically need a windows server.

For thin clients that support X11 or VNC, you'd be all set... this isn't one of them, though.

---

### Post by tuff3rthanu on 2008-05-16
I have gotten to step 4 of the process and I got a few errors. Also i am running AMD64 bit version of ubuntu. but this is what i get on step 4 willslap:~$ sudo gedit /opt/ltsp/amd64/etc/ssh/ssh_known_hosts
willslap:~$ sudo invoke-rc.d dhcp3-server start
invoke-rc.d: unknown initscript, /etc/init.d/dhcp3-server not found.
willslap:~$

---

### Post by tuff3rthanu on 2008-05-16
is it possiable to reformat this device and what would i reformat it with?

---

### Post by gopher2x on 2008-08-28
you dont have to reformat. I have 2 of these one runs ubuntu one runs debian. I am running text mode servers on these boxes. Get a netboot image and dd it to a usb flash drive as soon as it start booting plug in another usb flash drive and install to that drive. after installed remove the install flash and you set. It works great. msg me if you want a dd of my boot HD

---

