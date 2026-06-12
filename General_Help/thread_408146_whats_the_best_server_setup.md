---
title: "whats the best server setup?"
date: 2007-04-13
forum: General Help
---

### Post by Atrio05 on 2007-04-13
i'm really just looking for the easyiest way to setup a solid secure server, i'm going to be installing it on my second hard drive if that means anything.

like which version of ubnutu is the best to set up a server on? 6.06, 6.10, 7.04, which one?

i have had apache 2 and mysql setup on ubuntu edgy but i don't think i installed and configured everything properly like mysql i think was messed up.

any How-To's or anything like that is welcome!!

i just want a simple web server so i can host my own site and forums.(like phpbb)

any help would be greatly appreciated!!

thank you in advance!!

---

### Post by amohanty on 2007-04-13
[http://www.aboutdebian.com/internet.htm](http://www.aboutdebian.com/internet.htm) is a very good starting point. Just keep in mind that tha package names may be different.

As to security that's a bit too complex to explain in a 'easy' howto and depends too much on your particular needs to have a generic howto. For starters:

- if possible dont host your own public internet server
- if you absolutely have to to set it up, buy a hardware firewall (not one of those router+firewall thingies) a real SOHO firewall, you can get decent ones for ~$300 or so.
- do not run anything that is not an absolute requirement for apache, mysql and php.
- get very friendly with **nmap** make sure you only have port 80 exposed and nothing else.
- I would suggest setting it up and playing around with it with a good linux sys admin book for a couple of months before even trying to go public.

I have been using linux for the last 8 yrs and consider myself an experienced (not an expert) user, yet am constantly amazed at how little I know.

HTH
AM

---

### Post by Atrio05 on 2007-04-13
so which version of ubuntu would be the best candidate for my server? whats the most stable, the most secure, the easyiest to use? i just need a solid base to work with.

should i go with the LAMP server installs and then add a gui or what?

---

### Post by HereInOz on 2007-04-13
Have a look at this page:

[http://howtoforge.com/perfect_setup_ubuntu_6.10](http://howtoforge.com/perfect_setup_ubuntu_6.10)

It may give you some clues.

---

### Post by az on 2007-04-13
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Use Dapper.

---

### Post by Atrio05 on 2007-04-14
ok thanx!!

---

