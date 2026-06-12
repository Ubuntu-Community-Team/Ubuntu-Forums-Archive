---
title: "wget advice?"
date: 2008-06-25
forum: General Help
---

### Post by apidya on 2008-06-25
Hey;

Can someone give me advice on wget? I wish to make a recursive retrival using a list of accepted domains for it to follow. The man says this is possible using the option:

> 
-D,  --domains=LIST              comma-separated list of accepted domains.


But I am still having trouble writing a command that gets this to work. Am I right in thinking it is along the lines of...

> wget -r -H -D domains.txt [http://mysite.co.uk](http://mysite.co.uk)

what would be the format of the domains file?

any help greatly appricated.

---

### Post by apidya on 2008-06-25
I think I've found what will do the job:


> wget -r -H -D domaintoallow.ac.uk [http://mysite.co.uk](http://mysite.co.uk)

---

