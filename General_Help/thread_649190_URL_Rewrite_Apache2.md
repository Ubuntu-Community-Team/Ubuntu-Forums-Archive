---
title: "URL Rewrite Apache2"
date: 2007-12-24
forum: General Help
---

### Post by dropyeyez on 2007-12-24
Hello All, 

I am using ISPConfig on ubuntu gusty with apache2,squirrelmail installed as an addon in ispconfig, I need some help please with URL rewrite. If I can I would like to avoid adding a co-domain in ispconfig no specific reason thats the way I want it to be. 

At the minute to access my webmail I have to do this 

[https://www.abc.co.uk:81/squirrelmail](https://www.abc.co.uk:81/squirrelmail) and that redirects to [https://www.abc.co.uk:81/src/login.php](https://www.abc.co.uk:81/src/login.php) 

but what i want it to redirect it to (through apache2) 

[https://www.abc.co.uk/webmail](https://www.abc.co.uk/webmail).  

Also I want it done once, I do not want to it for every domain on my server, hence other customers if they want to access there webmail simply type https:// theredomain.name/webmail and through to there webmail from there.

I have read about it on different webites, forums including apache's website  but have not been able to solve the mystery. 

I cannot understand how it is done, it seems hard. 

Any help on this with examples would be really appreciated. 

Thank you very much in advance. Looking forward for positive response.

---

