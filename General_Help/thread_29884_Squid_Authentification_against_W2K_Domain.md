---
title: "Squid Authentification against W2K Domain"
date: 2005-04-26
forum: General Help
---

### Post by NewbieNik on 2005-04-26
Ok so I jumped riight in at the deep-end and found I'm not as good a swimmer as I thought I was.
Have install Hoary Gnome (Harry's Game? Wasn't that a good TV thriller from the 80's??)
Have installed winbind and connected to W2k domain. wbinfo -g and -u lists all the domain users and groups fine.
Have installed squid from apt-get and set local IP address range in ACL as allowed and I can access the web through squid fine.
What I can't do is set Ubuntu to check the users against our W2k domain controller. I want to set-up groups "WebAllow" and "WebDeny" in W2k or ubuntu and add the domain users into those groups and gice access to teh web accordingly, but as the domain has over 200 users I do not want to add each person individually.
This is something I am trying in my own time to further my knowledge of Linux and not for the company so any help would be greatly appreciated.

---

### Post by Guiome on 2005-05-13
[QUOTE=NewbieNik]Ok so I jumped riight in at the deep-end and found I'm not as good a swimmer as I thought I was.
Have install Hoary Gnome (Harry's Game? Wasn't that a good TV thriller from the 80's??)
Have installed winbind and connected to W2k domain. wbinfo -g and -u lists all the domain users and groups fine.
Have installed squid from apt-get and set local IP address range in ACL as allowed and I can access the web through squid fine.
What I can't do is set Ubuntu to check the users against our W2k domain controller. I want to set-up groups "WebAllow" and "WebDeny" in W2k or ubuntu and add the domain users into those groups and gice access to teh web accordingly, but as the domain has over 200 users I do not want to add each person individually.
This is something I am trying in my own time to further my knowledge of Linux and not for the company so any help would be greatly appreciated.[/QUOTE]

Sorry not to answer but i didn't manage to join my W2K domain...  Even if y follow explanations on this forum [http://www.ubuntuforums.org/showthread.php?t=5409&highlight=winbind](http://www.ubuntuforums.org/showthread.php?t=5409&highlight=winbind)... is it possible for you to explain step by step how you did it ?  :grin:

---

### Post by NewbieNik on 2005-05-25
Sorry, been away a while. Once samba and winbind was installed, set up SAMBA through SWAT to match workgroup name and domain name. Added a pre-windows 2000 computer account in W2K and the ran the netjoin -D *domainname* -U*adminsistrator-account*
Do not use the rpc switch. That is a rpc domain join, not active directory. Then use the install procedure as described in the previous article.

Problem I'm experiencing is with usenames or groups with a space in them. Its not fair. Iwantaspaceinmyname!!!!

Help me please. I'm going nuts (And 6 foot of nuts is the last thing you want to see!! ;-)

---

