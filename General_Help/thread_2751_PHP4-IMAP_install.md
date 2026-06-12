---
title: "PHP4-IMAP install?"
date: 2004-10-31
forum: General Help
---

### Post by z3steve on 2004-10-31
Hi there,

I'm setting up my first linux server to host eGroupware (branch from phpgroupware) . I've got mysql, apache2 and php working fine but I'm missing one module to allow email from within the groupware app. The module is PHP4-IMAP and I cant find it within the package repositories. I've found the .deb package at Debians site but its dependant on zendapi-20010901 {virtual package} and I have no idea what this is.  #-o 

Would appreciate any help in getting IMAP support in php4.

Thanks in advance

Steve.
ps. tried 10 different distros in 2 weeks...Ubuntu rocks  :lol:

---

### Post by ljoris on 2004-11-25
[QUOTE=z3steve]Hi there,

I'm setting up my first linux server to host eGroupware (branch from phpgroupware) . I've got mysql, apache2 and php working fine but I'm missing one module to allow email from within the groupware app. The module is PHP4-IMAP and I cant find it within the package repositories. I've found the .deb package at Debians site but its dependant on zendapi-20010901 {virtual package} and I have no idea what this is.  #-o 

Would appreciate any help in getting IMAP support in php4.

Thanks in advance

Steve.
ps. tried 10 different distros in 2 weeks...Ubuntu rocks  :lol:[/QUOTE]


Hey Steve,

Same problem here ... crazy, ubuntu is releasing warty with broken packages .!.

Will keep you posted on any progres.

Regards,

Joris

---

### Post by ljoris on 2004-11-30
[QUOTE=ljoris]Hey Steve,

Same problem here ... crazy, ubuntu is releasing warty with broken packages .!.

Will keep you posted on any progres.

Regards,

Joris[/QUOTE]

Ehr, isn't there some inspiring guru around to notice these messages ?

---

### Post by jdodson on 2004-12-01
[QUOTE=ljoris]Ehr, isn't there some inspiring guru around to notice these messages ?[/QUOTE]

i replicated this problem on my machine too, it does in fact seem that there is a package dependecy problem.  please follow this link to submit a bug on the issue, this has a chance to be fixed:

[http://www.ubuntulinux.org/support/bugs](http://www.ubuntulinux.org/support/bugs)

---

### Post by ljoris on 2004-12-02
[QUOTE=jdodson]i replicated this problem on my machine too, it does in fact seem that there is a package dependecy problem.  please follow this link to submit a bug on the issue, this has a chance to be fixed:

[http://www.ubuntulinux.org/support/bugs](http://www.ubuntulinux.org/support/bugs)[/QUOTE]

THAT worked out great ! Please, it is very helpfull of you to support the ubuntuforums but phpgroupware is NOT supported. I've been trying various approaches to get this to work in any other way ... no luck. Even using the phpgroupware stable repository does not work out ...

I wonder if this might be the reason i cannot get postgres-sql to work either ...

Please, i don't think it is a very wise decision of the ubuntu maintainers to NOT support a big package like phpgroupware, in fact phpgroupware is NOT the real issue, that is a php4-package wich i have a hard time believing is NOT supported ... even if it isn't really it would be a stupid thing to not do anything to get this to work ... c'mon people PHP IV !   :confused:

---

### Post by sanitys3j on 2004-12-10
From what I can tell so far, the Ubuntu team is very security concious.  They attempt to make decisions accordingly.  The PostgreSQL issue you're having is a result of NOT reading the documentation about permissions and changing things in your load accordingly, I had the same issue (now working great after 3 minutes or so of chmod'ing) so I seriously doubt it's tied to the php4-imap issue.  Point being: quit blaming Ubuntu & it's developers for your own ineptitude.

I'm not sure why php4-imap is a broken package, but perhaps (due to the security focus) this link may explain it a bit:  [http://www.net-security.org/advisory.php?id=2205](http://www.net-security.org/advisory.php?id=2205)

Universally,
Shayne

---

### Post by sanitys3j on 2004-12-10
I think I jumped the gun on that link, after reading further it's for an older version of php4.  

Any input about security issues with phpgroupware?  Particularly (i'd imagine) with imap?

Universally,
Shayne

---

### Post by alexking on 2005-01-27
[QUOTE=z3steve]Hi there,

I'm setting up my first linux server to host eGroupware (branch from phpgroupware) . I've got mysql, apache2 and php working fine but I'm missing one module to allow email from within the groupware app. The module is PHP4-IMAP and I cant find it within the package repositories. I've found the .deb package at Debians site but its dependant on zendapi-20010901 {virtual package} and I have no idea what this is.  #-o 

Would appreciate any help in getting IMAP support in php4.

Thanks in advance

Steve.
ps. tried 10 different distros in 2 weeks...Ubuntu rocks  :lol:[/QUOTE]

I've collected what I know about this issue and listed the results on the ubuntu wiki at: [https://www.ubuntulinux.org/wiki/Php4ImapIssue](https://www.ubuntulinux.org/wiki/Php4ImapIssue).  There is a possible apt source to fix this problem

---

### Post by daniels on 2005-01-27
a) php4-imap is now in universe, and has been for about 12 hours as I understand it,
b) we decided not to include it in the normal php4 package, as that would mean bringing libc-client-dev into supported, which is an absolute horror show as far as security goes.

---

