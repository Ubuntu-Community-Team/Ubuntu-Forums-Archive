---
title: "installing emacs, termcap/info"
date: 2007-06-17
forum: General Help
---

### Post by Greggle on 2007-06-17
I wanted to compile emacs from the source just to see how it all works, compiling that is.

Anyway, ./configure/make/install worked fine. However, once I tried to run emacs I received the error: 'cannot open the termcap database file.'

I did some searching and it would appear that termcap has been replaced by terminfo. I don't even know what termcap is, so the change to 'terminfo' is equally meaningless.

I tried to install termcap-compat per a recommendation I found elsewhere, but it did not work; it didn't exist anymore... I guess...

'How can I get emacs running,' I wonder quietly to myself?

P.S. I searched both Google and these-here forums, but the NUMEROUS suggested solutions have not availed me.

-Thanks

---

### Post by confused57 on 2007-06-17
> **Greggle said:**
> I wanted to compile emacs from the source just to see how it all works, compiling that is.

Anyway, ./configure/make/install worked fine. However, once I tried to run emacs I received the error: 'cannot open the termcap database file.'

I did some searching and it would appear that termcap has been replaced by terminfo. I don't even know what termcap is, so the change to 'terminfo' is equally meaningless.

I tried to install termcap-compat per a recommendation I found elsewhere, but it did not work; it didn't exist anymore... I guess...

'How can I get emacs running,' I wonder quietly to myself?

P.S. I searched both Google and these-here forums, but the NUMEROUS suggested solutions have not availed me.

-Thanks
You'll have to install several dependencies, before you can install termcap:
[http://packages.debian.org/oldstable/oldlibs/termcap-compat](http://packages.debian.org/oldstable/oldlibs/termcap-compat)

What I did was download termcap, then the dependencies, then you have to install accordingly.

---

### Post by Greggle on 2007-06-17
Thanks, confused. emacs is a go.

---

