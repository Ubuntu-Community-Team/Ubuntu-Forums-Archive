---
title: "Cornell spider security program"
date: 2008-05-27
forum: General Help
---

### Post by DouglasAWh on 2008-05-27
So, I am trying to run Cornell's spider [http://www.cit.cornell.edu/security/tools/](http://www.cit.cornell.edu/security/tools/) and I am getting the following error:

```

whitdoug@dev116:/usr/local/cornell/spider$ /usr/local/cornell/spider/spider-4.0/spider-4.0.pl -D /home/whitdoug/Documents
Can't locate MD5.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/cornell/spider/spider-4.0/spider-4.0.pl line 19.
BEGIN failed--compilation aborted at /usr/local/cornell/spider/spider-4.0/spider-4.0.pl line 19.


```

I have some sense of what the error is telling me, but I'm not certain what will fix it.  It appears I have perl installed.


```

whitdoug@dev116:/usr/local/cornell/spider$ which perl
/usr/bin/perl


```

Any help is much appreciated!

---

### Post by Monicker on 2008-05-27
You need to install the perl md5 module.  There are 2 likely candidates in the repos.

sudo apt-get install libmd5-perl
sudo apt-get install libdigest-md5-file-perl

---

