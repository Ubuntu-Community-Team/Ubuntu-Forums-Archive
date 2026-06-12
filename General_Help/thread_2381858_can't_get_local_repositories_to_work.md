---
title: "can't get local repositories to work"
date: 2018-01-06
forum: General Help
---

### Post by mintmag on 2018-01-06
Thisis frustrating me being belief. So I&#8217;m trying to set up a little dvd repository and I can never get it to work. [https://www.pcsuggest.com/how-to-use-an-iso-file-as-offline-repository-in-debian/](https://www.pcsuggest.com/how-to-use-an-iso-file-as-offline-repository-in-debian/)I know this tutorial is focused on Debain but after following it to the letter I wasn&#8217;t able to use the repo. What happens is that after I add the line ```
deb [file:///media/repo_1/](file:///media/repo_1/)
```followed by the rest of the address sure enough it appears in the software list but I can&#8217;t get anything from it. I&#8217;ve tried this sort of thing in Ubuntu as other Debain based systems before. Could someone please show me how this is done.

---

### Post by cruzer001 on 2018-01-06
That tutorial looks like a pain to me compared to apt-mirror (its in the repositories).

[http://apt-mirror.github.io/](http://apt-mirror.github.io/)

Or just maybe go the ultra-lazy route :)

[https://www.osdisc.com/products/linux/ubuntu/ubuntu-1604-lts-software-repository-13-dvd-set-64bit.html](https://www.osdisc.com/products/linux/ubuntu/ubuntu-1604-lts-software-repository-13-dvd-set-64bit.html)

---

### Post by mintmag on 2018-01-06
> **cruzer001 said:**
> That tutorial looks like a pain to me compared to apt-mirror (its in the repositories).

[http://apt-mirror.github.io/](http://apt-mirror.github.io/)

Or just maybe go the ultra-lazy route :)

[https://www.osdisc.com/products/linux/ubuntu/ubuntu-1604-lts-software-repository-13-dvd-set-64bit.html](https://www.osdisc.com/products/linux/ubuntu/ubuntu-1604-lts-software-repository-13-dvd-set-64bit.html)

Thanks for responding but apt-mirror is pain and I never got it working. With repositories on multiple discs is there anyway to just add them to the system?

---

