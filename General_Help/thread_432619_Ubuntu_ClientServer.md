---
title: "Ubuntu Client/Server"
date: 2007-05-04
forum: General Help
---

### Post by Jaxilian on 2007-05-04
I wonder if there is any information about how it works with Ubuntu client against Ubuntu server if it doesn't exist any MS products in that network.

*Does Ubuntu have similar functions as Windows servers when it comes to logonservers/domains etc?

*How do you set it up?

I gotten the question a lot of times from friends who use Windows, but I really can't answer them cause I just can't find the info.

I appreciate any help/info of this :confused:

---

### Post by 505 on 2007-05-04
I'm not an expert in that field, but yes it is possible. You can set up Linux to authenticate against an LDAP server. Google for 'ubuntu ldap authentication' and you should get a number of guides.

---

### Post by Jaxilian on 2007-05-04
I don't get any that I understand and most are not in english.
From what it looks like from my point of view, Ubuntu aren't really trying to promote it's serverside at all. I have tried to search this forum for things like this, but nothing shows up. I search for several days on google and come up with.....nothing.

Should be huge posts about it or a lot of wikis n' guides etc.....am I wrong? 
I am definitely not a Ubuntu expert....far from it, but I want to learn.

But nothin?? I am kinda disappointed

---

### Post by TheWizzard on 2007-05-04
> **flodis said:**
> I don't get any that I understand and most are not in english.
From what it looks like from my point of view, Ubuntu aren't really trying to promote it's serverside at all. I have tried to search this forum for things like this, but nothing shows up. I search for several days on google and come up with.....nothing.

Should be huge posts about it or a lot of wikis n' guides etc.....am I wrong? 
I am definitely not a Ubuntu expert....far from it, but I want to learn.

But nothin?? I am kinda disappointed

just google:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Servers](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Servers)
[https://wiki.ubuntu.com/ServerCandy](https://wiki.ubuntu.com/ServerCandy)

---

### Post by Jaxilian on 2007-06-08
Not really what I was looking for.

Is there truly nothing really user-friendly information about Ubuntu client/server? About how to make them work together and like what are the advantages/disadvantages etc

Microsoft has the edge cause they have a really sweet client/server package....does Ubuntu goin there too or what?
If any has good info, please post

---

### Post by Jaxilian on 2007-06-12
bump

---

### Post by Jaxilian on 2007-06-18
bump

---

### Post by MentholLite on 2007-06-18
Try looking for LDAP and Samba.

LDAP is just like Windows Active Directory (AD) type of providing directory access services (logon, logoff, users, groups, etc).
Or maybe I should say Windows followed the LDAP style when designing AD initally.
You can centralize database info for all your users, groups and objects into a *NIX machine.

Samba can be used to glued the networked peripherals together. 
E.g. In a mix environment with Windows & *NIX, you can share printers, share folders, etc.

---

### Post by xpd777 on 2007-06-27
> **flodis said:**
> I wonder if there is any information about how it works with Ubuntu client against Ubuntu server if it doesn't exist any MS products in that network.

*Does Ubuntu have similar functions as Windows servers when it comes to logonservers/domains etc?

*How do you set it up?

I gotten the question a lot of times from friends who use Windows, but I really can't answer them cause I just can't find the info.

I appreciate any help/info of this :confused:



Yes, i'm also wondering if ubuntu can act like windows' active directory with roaming profiles for users.

---

### Post by TheWizzard on 2007-06-27
> **flodis said:**
> Not really what I was looking for.

Is there truly nothing really user-friendly information about Ubuntu client/server? About how to make them work together and like what are the advantages/disadvantages etc

Microsoft has the edge cause they have a really sweet client/server package....does Ubuntu goin there too or what?
If any has good info, please post

sorry, but i know nothing about microsoft networking.
what kind of server do you want? file, email, etc...
everything is easy to setup.

---

### Post by TheWizzard on 2007-06-27
> **505 said:**
> I'm not an expert in that field, but yes it is possible. You can set up Linux to authenticate against an LDAP server. Google for 'ubuntu ldap authentication' and you should get a number of guides.

why is your name 505?

---

### Post by SuperMike on 2007-06-27
Ubuntu Server is not quite there yet with an easy, plug-n-play web-based admin server for mom and pop shops (small business) much like Microsoft's stuff. However, there's some projects on Launchpad where the Ubuntu devs are considering options. If you want to get two books like Ubuntu Hacks and The Ubuntu Book, they can show you how to setup an LDAP server, DHCP server, DNS server, SMTP/POP (mail) server, and so on. However, if you want to get there with a stable version of Debian, which Ubuntu is based upon, check out the ebox-platform:

[http://ebox-platform.com/](http://ebox-platform.com/)

They make it super-easy.

I'm actually trying to find the time to make a Plug-n-Play Ubuntu Server Appliance with a snazzy web-based admin interface much like ebox-platform, but haven't had time. All I've got so far are some fancy menus and a template system in PHP and SQLite3. I'll be building it shortly.

---

### Post by Jaxilian on 2007-06-28
> **SuperMike said:**
> Ubuntu Server is not quite there yet with an easy, plug-n-play web-based admin server for mom and pop shops (small business) much like Microsoft's stuff. However, there's some projects on Launchpad where the Ubuntu devs are considering options. If you want to get two books like Ubuntu Hacks and The Ubuntu Book, they can show you how to setup an LDAP server, DHCP server, DNS server, SMTP/POP (mail) server, and so on. However, if you want to get there with a stable version of Debian, which Ubuntu is based upon, check out the ebox-platform:

[http://ebox-platform.com/](http://ebox-platform.com/)

They make it super-easy.

I'm actually trying to find the time to make a Plug-n-Play Ubuntu Server Appliance with a snazzy web-based admin interface much like ebox-platform, but haven't had time. All I've got so far are some fancy menus and a template system in PHP and SQLite3. I'll be building it shortly.


thanks man! :D

---

