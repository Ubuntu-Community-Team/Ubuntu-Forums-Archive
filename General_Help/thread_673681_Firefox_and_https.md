---
title: "Firefox and https://"
date: 2008-01-20
forum: General Help
---

### Post by ElEdwards on 2008-01-20
I'm having a problem accessing secured sites in Gutsy and Firefox (v2.0.0.11).  All too often, when I try to access a website that is prefixed with **https://**, Firefox goes gray and I finally have to close it.

I can access these same sites in WinXP and IE6 without any problems at all.

This is all on my Presario 2170us laptop with a Linksys wireless card.

I have disabled IPV6 .... but are there any other things I can change in Firefox's **about:config** to fix this problem?

Thanks! :)

---

### Post by CupofDice on 2008-01-20
[This]("http://ubuntuforums.org/showthread.php?t=319191") may help. It seems that disabling ipv6 in about:config helps.

Edit- Idiot me. Did you disable ipv6 just on ubuntu or through Firefox's about:config too?

---

### Post by ElEdwards on 2008-01-21
I had disabled IPV6 through **about:config** in Firefox... but after reading further, I see that this may not be enough.

CupofDice, thanks for that link.  I went there and after some reading and digging, I see that it can also help to make a change to **/etc/modprobe.d/aliases** with this:
```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

```The commented line above (with the #) is the original line.

Is this good to do, too, or not?  Thoughts, please?

Thanks!
El :)

---

### Post by CupofDice on 2008-01-21
Well, if you followed the instructions exactly, it won't hurt (It didn't when I did it). Just make sure to backup the file.

---

