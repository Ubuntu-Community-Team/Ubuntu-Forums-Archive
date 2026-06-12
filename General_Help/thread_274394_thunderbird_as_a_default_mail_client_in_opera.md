---
title: "thunderbird as a default mail client in opera"
date: 2006-10-09
forum: General Help
---

### Post by cccc on 2006-10-09
hi

howto configure opera to get thunderbird as a default mail client ?

greetings
cccc

---

### Post by Kateikyoushi on 2006-10-09
Is thunderbird set up as the default mail client but opera still uses another app ?

See here.
System >> Preferences >> Preferred applications.

---

### Post by cccc on 2006-10-09
> **Kateikyoushi said:**
> Is thunderbird set up as the default mail client but opera still uses another app ?

See here.
System >> Preferences >> Preferred applications.

in System >> Preferences >> Preferred applications I have thunderbird setuped, but opera still wants open all mail links with its mail client.

---

### Post by Kateikyoushi on 2006-10-09
Okay now I see, have to change it in Opera.

Tools >> Preferences >> Advanced Tab >> Programs.
Then edit the mailto protocol.

---

### Post by cccc on 2006-10-09
thanks, now it works well.

---

### Post by kristalsoldier on 2007-03-13
> **Kateikyoushi said:**
> Okay now I see, have to change it in Opera.

Tools >> Preferences >> Advanced Tab >> Programs.
Then edit the mailto protocol.

Hi...

This is an old thread but I thought it better to ask here than to start a new one. I use TB as my mail client. At the point of Edit Program, I pick 'Open with Other Application'. At this point I can choose (1) /etc/...mozilla-tb/ autoconfig.js OR /etc/...mozilla-tb/ globalconfig.js.

Regardless, when I try to use email through Opera, I still get asked 'Do you want to set up a mail account', which I do not want to do.

Obviously these two options don't work. So, what should I be choosing?

Thanks.

---

### Post by Kateikyoushi on 2007-03-13
Neither of them, I would point it to /use/bin/mozilla-thunderbird but did not try it yet myself.
Let us know if it works.

---

### Post by kristalsoldier on 2007-03-13
> **Kateikyoushi said:**
> Neither of them, I would point it to /use/bin/mozilla-thunderbird but did not try it yet myself.
Let us know if it works.

Yup...it worked thanks!

So, it goes.../usr/bin/mozilla-thunderbird

Thanks

I better put down the whole sequence:

In Opera...Tools>Preferences>Advanced>Programs>Edit mailto and then choose /usr/bin/mozilla-thunderbird

---

