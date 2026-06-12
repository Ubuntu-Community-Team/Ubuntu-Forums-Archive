---
title: "libc6-i686.postinst corrupt"
date: 2007-02-09
forum: General Help
---

### Post by HET on 2007-02-09
I'm getting errors when using apt-get, namely with dpkg.

Ex:

Setting up libc6-i686 (2.4-1ubuntu12.3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libc6-i686 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 libc6-i686
E: Sub-process /usr/bin/dpkg returned an error code (1)

I looked for the script. It's /var/lib/dpkg/info/libc6-i686.postinst

I opened the file with emacs and it's just a bunch of @@@@@@@@@@@'s. I think it's corrupted.** Could anyone post the contents of this file so that I can replace it?** A non 686 optimized one will probably work too. I would really appreciate it.

Is there a better way of replacing files like this that might be corrupt in the future? Asking someone to post the script on a forum seems backwords, I'm sure there's a better way I am not aware of.

---

