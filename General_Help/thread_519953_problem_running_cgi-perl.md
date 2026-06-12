---
title: "problem running cgi-perl"
date: 2007-08-07
forum: General Help
---

### Post by nikhil_rathod on 2007-08-07
Hello every one,
In ubuntu when I try to run perl scripts like this

./test.pl 

it dosent work, but when I try 

perl test.pl

it workes fine

when working with cgi-perl if I write the scripts like
#!/usr/bin/perl
print "Content-type: text/html\n\n";

it gives error "500 Interal server error"
but when I try

#!/usr/bin/perl -wT
print "Content-type: text/html\n\n";

it works fine. Any suggestions what might be wrong over here?

thanks

---

### Post by aJayRoo on 2007-08-07
When you say typing ./test.pl doesn't work, in what way doesn't it work? Could it be that you have not set the permissions of the script to be executable? if that is the case then the command:
```
chmod +x test.pl
```
will allow all users to execute the script. In order to be executed on its own a script requires these permissions, however they would not be necessary if you run the script as an argument to the perl interpreter as in:
```
perl test.pl
```
as this operation only requires read permission for the script. As for the server error I'm not too sure about the cause, perhaps some one else will be able to shed some light on that for you.

---

### Post by tr333 on 2007-08-26
It looks like you have a typo in what you're printing out.  There should be a "T" instead of "t" for "Content-Type".

Instead of printing out this yourself, consider using the [CGI](http://search.cpan.org/modlist/World_Wide_Web/CGI) module.

---

