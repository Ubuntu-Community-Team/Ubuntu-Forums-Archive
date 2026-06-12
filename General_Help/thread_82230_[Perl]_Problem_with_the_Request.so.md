---
title: "[Perl] Problem with the Request.so"
date: 2005-10-26
forum: General Help
---

### Post by yussef on 2005-10-26
I have migrated from SID to ubuntu so now i have to reinstall all my servers etc.

I am trying to install the Apache::Gallery. However when I try to access it from the web I get this error : [http://gallery.yussef.no-ip.com](http://gallery.yussef.no-ip.com)

And when I look in the apache error logs, this comes up:

```
[Wed Oct 26 12:41:27 2005] [error] Can't load '/usr/lib/perl5/auto/Apache/Request/Request.so' for module Apache::Request: libapreq.so: cannot open shared object file: No such file or directory at /usr/lib/perl/5.8/DynaLoader.pm line 225.\n at /usr/lib/perl5/mod_perl.pm line 14\nCompilation failed in require at /usr/local/share/perl/5.8.7/Apache/Gallery.pm line 36.\nBEGIN failed--compilation aborted at /usr/local/share/perl/5.8.7/Apache/Gallery.pm line 41.\nCompilation failed in require at (eval 7) line 3.\n
[Wed Oct 26 12:41:27 2005] [error] Undefined subroutine &Apache::Gallery::handler called.\n
[Wed Oct 26 12:41:27 2005] [error] Undefined subroutine &Apache::Gallery::handler called.\n

```

Anyone know what the problem is? And how I should correct it?

Thanks

PS: I have checked and all the files are present.

---

