---
title: "Cron environment settings"
date: 2008-07-04
forum: General Help
---

### Post by weezer316 on 2008-07-04
Anyone....

I have some serious problems getting cron to run. Basically, i installed perl 5.10 and then installed all my packages from cpan.

Now, when i try to run a cronjob it cannot find the .pm files as the PATH setting is tiny adn only searches the wrong places.

All the .pm files re located in /usr/local/lib and I need to make cron search there.....how do i do it?? I tried specifying the env at the top of my perl script ($ENV{'PATH'} = '/usr/local/lib';) bit it still not working. I simply get this error.


Can't locate Net/SSH/Expect.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/weezer/Documents/Perl/scripts/ssh_test.pl line 6.

any ideas??

---

### Post by HalPomeranz on 2008-07-05
The easiest thing to do is change the "shebang" line at the top of your script:

```

#!/usr/bin/perl -I/usr/local/lib

```

You can also do this:

```

#!/usr/bin/perl

BEGIN {
    push(@INC, '/usr/local/lib');
}

```

Either approach updates Perl's module include path, which is stored in the magic @INC variable.

---

