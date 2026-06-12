---
title: "can't run pl files"
date: 2024-04-17
forum: General Help
---

### Post by theyikes on 2024-04-17
hi! i'm having trouble running a .pl file, to be exact it's 7z2john.pl. I've installed perl according to a site i found but it's not running. 

here's the error message i'm getting :
 
```
[FONT=monospace][COLOR=#000000]/snap/john-the-ripper/639/run/7z2john.pl *.7z > hashfile[/COLOR]
Can't locate Compress/Raw/Lzma.pm in @INC (you may need to install the Compress::Raw::Lzma module) (@INC contains: /home/yikes/perl5/lib/perl5/5.36.0/x86_64-linux-gnu-thread-multi /home/yikes/perl5/lib/perl5/5.36.0 /home/yikes/perl5/lib
/perl5/x86_64-linux-gnu-thread-multi /home/yikes/perl5/lib/perl5 /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.36.0 /usr/local/share/perl/5.36.0 /usr/lib/x86_64-linux-gnu/perl5/5.36 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl-bas
e /usr/lib/x86_64-linux-gnu/perl/5.36 /usr/share/perl/5.36 /usr/local/lib/site_perl) at /snap/john-the-ripper/639/run/7z2john.pl line 6.
BEGIN failed--compilation aborted at /snap/john-the-ripper/639/run/7z2john.pl line 6.

[/FONT]
```

any help would be great. Thanks.

---

### Post by theyikes on 2024-04-17
found this online.

```
[FONT=monospace][COLOR=#000000]sudo apt-get install -y libcompress-raw-lzma-perl[/COLOR]

[/FONT]
```

all good now.

---

