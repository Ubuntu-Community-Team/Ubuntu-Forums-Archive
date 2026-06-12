---
title: "logon pages not accessable"
date: 2007-10-16
forum: General Help
---

### Post by mikebou on 2007-10-16
Hi all,

don't know where to dirrect this post specifically, so thought I'ld start here and if need be someone can redirect me to a more appropriate formum.

We have installed and configured Ubuntu Server 6.04. (There is an issue with 7.04 and the scsi card in the server we are using) We installed and configured Shorewall firewall and Dansguardian with these instructions from this link:

[http://www.branchdistrictlibrary.org/professional/ubuntu_and_dansguardian_page_3.php](http://www.branchdistrictlibrary.org/professional/ubuntu_and_dansguardian_page_3.php)

With a little bit of extra configuring due to differences in squid versions, we got things running nicely and now the kids at the school we are doing this for are protected from inappropriate material and attacks. The problem at the moment is that you can go to a web site and thats fine. But if you try to log onto any website, the browser will just sit there (after entering the username and password and pressing enter) and eventually (10 min or more) complain it can't find the server. I suspect that it is a port issue. If you have a look through the instruction from the link I have mentioned, then you'll see that port 443 for https is opened up for use to the net. Do logon pages use another port? If we redirect the browsers to the old proxy, the logon pages are instant, so I'm sure it's a config issue either in shorewall or Ubuntu. 

Thanks in advance ,

Mike B

---

