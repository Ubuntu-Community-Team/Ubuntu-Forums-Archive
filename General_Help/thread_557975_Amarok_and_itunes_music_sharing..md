---
title: "Amarok and itunes music sharing."
date: 2007-09-23
forum: General Help
---

### Post by jtreach on 2007-09-23
I have installed mt-daapd and enabled sharing in amarok by clicking the share button. I have then forwarded the ports neccesary on my router.

If I then try to access my amarok music share from iTunes on either of the two windows machines on my network (the main reason for doing this is that my brother likes to listen to my music across the network). They both return unknown error messages and suggest I check the firewall (which i believe is an automated response for unknown errors as both the windows machines do not have firewalls).

Any ideas as to what could be going wrong? I used the first bit of this ([http://en.opensuse.org/ITunes](http://en.opensuse.org/ITunes)) guide (not 'the long way').

---

### Post by kiwisparkles on 2007-09-27
Have you started the daapd server?

```
sudo /etc/init.d/mt-daapd restart
```

Once you have done this, you should be able to configure your MP3 Directory and other items from a web browser: [http://localhost:3689](http://localhost:3689)

---

