---
title: "Is This a Bug?"
date: 2007-07-11
forum: General Help
---

### Post by noctiphile on 2007-07-11
I had a problem of mailto links in Firefox 2.0.0.3 not opening in anything.  I don't use the Evolution mail client.  I use Thunderbird.  To attempt to fix the problem I did the obvious thing: I changed the Mail Reader program in Preferred Applications to Mozilla Thunderbird.  That's the number one suggestion in mozillaZine.  It didn't help anything.  The number two suggestion is to use gconf-editor from the command line, which I did following the gksudo command.  There, it was still set as "evolution" even though I changed it in Preferred Applications.  I updated it there to mozilla-thunderbird.  Still, Firefox would not launch a mail application.  An average user shouldn't have to go past this point to get it working, in my opinion.  So I ask: Is this a bug I should report?

The workaround is to create a key-value entry in Firefox's about:config editor:
```
network.protocol-handler.app.mailto
```
and give it the value of
```
/usr/bin/mozilla-thunderbird
```

If changing it doesn't work in Preferred Applications, why is the option for Thunderbird even in the list?

Does the problem have anything to do with running 32-bit Firefox?

---

### Post by alphane on 2007-07-11
I changed this last night at home and had no problems.  As soon as I closed the preferred apps screen, mailto: links openend a new message from Thunderbird.

Although thinking about it, Thunderbird was open at the time...  I wonder whether I would have hit a problem if I tried to compose a message through a mailto link when Thunderbird was closed.

I will try later...

---

