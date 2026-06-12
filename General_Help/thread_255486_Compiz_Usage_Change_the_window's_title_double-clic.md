---
title: "Compiz Usage: Change the window's title double-click behavior"
date: 2006-09-11
forum: General Help
---

### Post by tribaal on 2006-09-11
Hi folks

I've installed XGL/Compiz and everything works fine. I love the new csm program, and everything works smoothly under the sun.

However I have only one little annoyance left: how the heck do I change the "double click on the window's titlebar" behavior?
The default behavior for this seems to be to "roll up" the window so that only the said titlebar is left visible, but I would like this action to maximise the window instead.

I've looked through csm pretty extensively, but I cannot seem to find the answer by myself... anyone knows?

Cheers

- trib'

---

### Post by bulldog on 2006-09-11
Did you also install cgwd and cgwd-themes?

If you did you can change the setting in cgwd themer under cgwd settings.

---

### Post by tribaal on 2006-09-11
You rock :)

I looked everywhere but here, of course :)

---

### Post by bulldog on 2006-09-11
Glad to be of some help.:D

---

### Post by hotstovejer on 2006-09-13
Dumb question, but how do you install cgwd and cgwd-themes? Do you have to update your sources.list to include something that isn't in there already?

Thanks for the help. I'm just a dumb noob. :P

Jeremy

---

### Post by tribaal on 2006-09-13
Hum I simply "apt-get cgwd cgwd-themes" with the following repos' enabled (the ones I used to install xgl/compiz in the first place):

```
#XGL / Compiz repositories
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

```

Hope this helps :)

- trib'

PS: there's no such thing as a dumb question, there are only dumb answers ;)

---

