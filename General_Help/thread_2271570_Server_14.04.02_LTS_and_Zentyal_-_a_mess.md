---
title: "Server 14.04.02 LTS and Zentyal - a mess?"
date: 2015-03-31
forum: General Help
---

### Post by wurstsalat2 on 2015-03-31
Hi together,

i tried several ways to get Zentyal to run on Server 14.04.02 (just plain install)

When i try using the standard repo to install it, zentyal-core failes with an post install skript and errorcode 2. I can reproduce this no matter what i do and no matter how i install it. I searched around and found this
[https://bugs.launchpad.net/ubuntu/+source/zentyal-core/+bug/1310694](https://bugs.launchpad.net/ubuntu/+source/zentyal-core/+bug/1310694)

kk known bug with no real solution but installing just a newer Version, so i jumped over to [https://wiki.zentyal.org/wiki/Installation_Guide](https://wiki.zentyal.org/wiki/Installation_Guide) and tried it. Install runs, fine...i can access the website and login but i want to use/install squid and of course the zentyal squid module. Next problem, the squid module depends on samba module and this one failes with the following message:
"The following packages are not properly installed. You need to fix this before trying to use them or install new modules. 
To solve this situation, please try to execute the following command in the console: 

sudo dpkg --configure -a 

After the above command is finished you can reload this page. If the problem persists, you can ask for help in the community forum or file a ticket in the Zentyal trac."

When i run "sudo dpkg --configure -a" it says for zentyal-samba
"Package samba is not yet configured"
for zentyal-squid that zentyal-samba isn`t configured yet.

So how i get a working zentyal? I tried install through apt-get and zentyal Software Management Website, nothing worked.
Or as an alternative, what is a vialable solution to have a web based Management for the System and Squid?

Thanks in advance for your help.

---

### Post by dino99 on 2015-03-31
zentyal seems no more maintained since 2012
googling around for some alternatives, here is a list: [http://alternativeto.net/software/ebox/](http://alternativeto.net/software/ebox/) [http://alternativeto.net/software/turnkey-linux/](http://alternativeto.net/software/turnkey-linux/)

---

### Post by dragonfly41 on 2015-03-31
[COLOR=#696969]**Webmin **[/COLOR]pkg (from Ubuntu Software Centre) has a Squid module.

[http://doxfer.webmin.com/Webmin/Squid_Basic_Configuration](http://doxfer.webmin.com/Webmin/Squid_Basic_Configuration)

---

### Post by wurstsalat2 on 2015-03-31
> **9d9 said:**
> zentyal seems no more maintained since 2012
but only in ubuntu respo? Cause zentyal itself has just released 4.1 (but without squid module)
The zentyal says the Commercial one is official supported by ubuntu?!
> **9d9 said:**
> 
googling around for some alternatives, here is a list: [http://alternativeto.net/software/ebox/](http://alternativeto.net/software/ebox/)   i did and i dont find a viable solution (anyway zentyal do more than i want)
ispconfig is a massive Software, if i install this i can install a full x Server....
artika is not rly a "on top" product and current ubuntu install doesnt exist (ok there is a Debian one...) and there is no community?!
Best solution i found so far, [http://ajenti.org/](http://ajenti.org/) ... but it is very limitted regarding to squid and there is no community, too?
Squidalyzer is only to view logs (but not bad)

So the alternatives i found are not rly what i am looking for, ajenti ist nearly what i search but the squid functionality is very very limited like the community



@dragonfly41
i didnt mention webmin cause people say it produces problems with ubuntu, also see: [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin) (i found several warnings not to use webmin anymore)
isnt this the current state?



But thanks so far....hope to find a solution which fits better my Needs :)

---

### Post by dragonfly41 on 2015-03-31
Re: compatibility of webmin with Ubuntu ..

I do believe that was a very old scare story.

[https://www.virtualmin.com/node/21110](https://www.virtualmin.com/node/21110)

Works fine here on Ubuntu 14.04 .. in fact I'm building a custom module.

Try latest version 1.4.*

[later edit]

Here is just one blog link ...

[http://www.techrepublic.com/blog/smb-technologist/configure-a-squid-proxy-server-through-webmin/](http://www.techrepublic.com/blog/smb-technologist/configure-a-squid-proxy-server-through-webmin/)

---

