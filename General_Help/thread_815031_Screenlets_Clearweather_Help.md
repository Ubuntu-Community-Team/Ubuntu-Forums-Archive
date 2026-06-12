---
title: "Screenlets Clearweather Help"
date: 2008-06-01
forum: General Help
---

### Post by ChildOfMana on 2008-06-01
I'm trying to configure the Clearweather screenlet but all it will say is "no info available".

I'm using the correct area code for weather.com (I've checked and re-checked and it's definitely the right one) but it doesn't seem to be able to pull the data over.

I've also tried this with GDesklets and conky and get variations on the same error message.

I'm just wondering if it's my firewall settings at play (I installed lokkit and then later removed it but I assume that removing it doesn't re-set the iptables config back to default??). Or perhaps I need to forward the correct port for this little app through my router (Linksys BEFSR41 v4). if so what port?

Thanks.

---

### Post by ChildOfMana on 2008-06-01
Apologies - I'm running Hardy Heron in case it matters.

Cheers.

---

### Post by james9876 on 2008-06-01
Yeah, I had this at one point, it's a problem with the clearweather applet, due to the change in coding on the weather.com website and the applet hasn't been updated for it.

[http://ubuntuforums.org/showthread.php?t=784053]("http://ubuntuforums.org/showthread.php?t=784053")

it does involve changing the coding of the applet though - but quite easy :), so may be worth installing the applet into the hidden screenlets directory in your home folder first and work on that, and it should (in theory) load instead of from the usr directory (if it doesn't, you can copy it into there though I'm sure).

good luck!

---

### Post by ChildOfMana on 2008-06-01
Thanks man. Worked like a charm... after a little fiddling about anyway. :)

---

