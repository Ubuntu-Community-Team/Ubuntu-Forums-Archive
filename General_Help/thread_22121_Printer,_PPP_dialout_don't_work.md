---
title: "Printer, PPP dialout don't work"
date: 2005-03-25
forum: General Help
---

### Post by Nathaniel Firethorn on 2005-03-25
Hi all,

I've been using Red Hat for a number of years and decided to give Ubuntu a try. Got the live CD (version 4.10) and it booted right up.  The issues I have are:

- Printer won't print (Lexmark E322, configured as a generic Postscript printer)

- PPP networking won't dial out (the connection immediately deactivates without doing anything to the modem)

- After setting the modem up, I can't open any new windows (!!!)

Is this normal behavior for the live disk? Or is something seriously kerflooey?

I've got a bone-stock Dell Dimension 4100.


Thanks,
- NT

---

### Post by Nathaniel Firethorn on 2005-03-27
Well, the PPP dialout is fixed. I had to follow the DialupModemHowto, PLUS edit /etc/resolv.conf to add Earthlink's DNS hosts **statically** (dynamic detection didn't work, dunno why) PLUS edit /etc/ppp/pap-secrets to add my username and password.

Now, it's just the printer that's not working. I'll post that in a separate message.

- NF

---

