---
title: "Weird warnings about tornado coming out of nowhere"
date: 2016-06-30
forum: General Help
---

### Post by scottbomb on 2016-06-30
I've got a terminal open on the laptop and it's just sitting there, doing nothing in particular when all of a sudden, a bunch of errors suddenly appear. Unfortunately, like most modern errors, they're cryptic and don't tell me anything. I don't know what tornado is or what it does but nothing else appears to be be wrong. The computer is connected to the internet via a VPN and Dropbox is running (says up to date), in case either of those has anything to do with it.

```
scottbomb@laptop:~$ WARNING:tornado.access:404 HEAD /blocks/70282547/V1QiTPDbDr-HwCRy-_-K6ft_ga8PkLgzzCxueFr3DqA (192.168.1.176) 33.43ms
WARNING:tornado.access:404 HEAD /blocks/70282547/V1QiTPDbDr-HwCRy-_-K6ft_ga8PkLgzzCxueFr3DqA (192.168.1.176) 29.85ms
WARNING:tornado.access:404 HEAD /blocks/70282547/V1QiTPDbDr-HwCRy-_-K6ft_ga8PkLgzzCxueFr3DqA (192.168.1.176) 15.84ms
WARNING:tornado.access:404 HEAD /blocks/70282547/V1QiTPDbDr-HwCRy-_-K6ft_ga8PkLgzzCxueFr3DqA (192.168.1.176) 22.47ms
WARNING:tornado.access:404 HEAD /blocks/70282547/UFxlOnwgfSaaER1CnhS6EEz-eWcjKrtIyo0e6-2IVIc (192.168.1.176) 22.52ms
WARNING:tornado.access:404 HEAD /blocks/70282547/UFxlOnwgfSaaER1CnhS6EEz-eWcjKrtIyo0e6-2IVIc (192.168.1.176) 19.73ms
WARNING:tornado.access:404 HEAD /blocks/70282547/UFxlOnwgfSaaER1CnhS6EEz-eWcjKrtIyo0e6-2IVIc (192.168.1.176) 5.89ms
WARNING:tornado.access:404 HEAD /blocks/70282547/UFxlOnwgfSaaER1CnhS6EEz-eWcjKrtIyo0e6-2IVIc (192.168.1.176) 4.72ms
```

---

### Post by ian-weisser on 2016-06-30
It's telling you about a Dropbox failure.
Dropbox uses Python Tornado.

Please report the problem to Dropbox if you want them to look into their software's problem.

---

### Post by scottbomb on 2016-06-30
Interesting and will do, thank you. I had seen some other threads suspecting Dropbox (though none of them seem to be solved) but it didn't seem to have any errors of its own.

---

### Post by scottbomb on 2016-06-30
This does bring about about another question: How does a running application get permission to suddenly output to an open terminal? I didn't start Dropbox from the terminal, it starts when the system starts. I've never seen any other application do this and I keep a terminal open all the time.

---

