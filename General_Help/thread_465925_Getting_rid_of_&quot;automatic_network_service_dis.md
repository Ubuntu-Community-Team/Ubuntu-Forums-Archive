---
title: "Getting rid of &quot;automatic network service discovery disabled&quot; message?"
date: 2007-06-06
forum: General Help
---

### Post by rapha on 2007-06-06
Hi all,

since installing Feisty, upon every (re)connect to the WLAN, we're greeted by a notification popup saying something along the lines of "automatic network service discovery disabled" (rough translation from German) because we were using some .local domain.

For one thing, I don't have .local in my resolv.conf ANYwhere, but more importantly I couldn't care less: I just want that message to GO AWAY and STAY GONE. Any advice on how to do that?

(Searching the forums and Google yielded nothing so far. I did try messing around with nsswitch.conf and also adding "mdns off" to resolv.conf, both of which had no effect whatsoever. Also, I don't want to fix this, I just want to get rid of the message)

TIA and best regards from Germany,
Raphael

---

### Post by Jaxilian on 2007-06-16
I want to know too. it's annoying as hell :(

---

### Post by rapha on 2007-06-17
Can't anybody even comment on this? I know devs are also reading the forums... every bit of info would be helpful...

---

### Post by Jaxilian on 2007-06-24
bump

---

### Post by merlinus on 2007-06-24
Look in System/Administration/Network in the General tab and see if the Automatic Service Discovery box is unchecked.

-merlin

---

### Post by rapha on 2007-06-25
Wow, that was easy, thanks! ... Seems to work for me and I'll try it at my gf's place next week :)

---

