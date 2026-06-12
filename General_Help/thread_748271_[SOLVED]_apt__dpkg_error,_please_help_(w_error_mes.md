---
title: "[SOLVED] apt / dpkg error, please help (w/ error message)"
date: 2008-04-07
forum: General Help
---

### Post by ticopelp on 2008-04-07
In trying to get my Brother laser printer to work correctly, I installed a .deb file from the Brother web site that seems to have wreaked havoc... the deb file was called hl5150dlpr and now every time I use apt-get for anything I get this:


```
Removing hl5150dlpr ...
/var/lib/dpkg/info/hl5150dlpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl5150dlpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl5150dlpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

My last attempt to remove this via the command line ended in disaster for me, so I could really use some assistance. How do I keep this message from continuing to crop up?

Thanks for any help.

---

### Post by pseudo-random on 2008-04-07
[https://answers.launchpad.net/ubuntu/+question/22818](https://answers.launchpad.net/ubuntu/+question/22818)
Different model, same prob.

---

### Post by ticopelp on 2008-04-07
That did it... thank you very much. 

Now if I can just get my printer working! :D

---

