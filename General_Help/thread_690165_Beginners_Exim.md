---
title: "Beginners Exim"
date: 2008-02-07
forum: General Help
---

### Post by vanderkerkoff on 2008-02-07
Hello peeps.

I've installed gutsy gibbon with no added extras.

Exim is running, magic.

I now need to tell exim to use our internal smtp server to send mail  out, and not allow any mail to be sent through itself.

I'll then need to restart exim.

I've found a /etc/exim4/exim4.conf.template file.

Do I edit that?  If so, can anyone tell me where to add the gateway?

Any help, greatly appreciated.

---

### Post by jan quark on 2008-02-08
[http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html)
[http://smx.hagerstowncc.edu/atmailpro/docs/exim.html](http://smx.hagerstowncc.edu/atmailpro/docs/exim.html)
[http://homes.esat.kuleuven.be/~decockd/site/myHowTos/applications/exim/index.html](http://homes.esat.kuleuven.be/~decockd/site/myHowTos/applications/exim/index.html)
[http://www.telecom.otago.ac.nz/tele301/tele301hb_html/install-configure-exim.html](http://www.telecom.otago.ac.nz/tele301/tele301hb_html/install-configure-exim.html)

these seems quite straight forward guides, however I have no idea, never used exim

but can you please post the output of the file you mentioned ?

run

```
cat /etc/exim4/exim4.conf.template
```

---

### Post by vanderkerkoff on 2008-02-08
Hi Jan

I removed Exim and installed sendmail which I know how to configure.

All working now.

Out of interest I started using the 

sudo dpkg-reconfigure exim4-config

command and going through the onscreen options, that seemed alot more like it.

It didn't work in the end though, but I think that was because my localhost wasn't set properly, or maybe our networks people were telling me fibs and hadn't switched my access on.

Anyway, one phone call, reinstall sendmail and all was fine.

Thanks for replying.

---

