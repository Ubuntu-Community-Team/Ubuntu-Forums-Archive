---
title: "j-pilot &amp; thunderbird"
date: 2006-11-14
forum: General Help
---

### Post by frrobert on 2006-11-14
I am using j-pilot for my palm and thunderbird for email.  I was using evolution but could not get it to sync with the palm.  

Everything is working well I have j-pilot set that if I tell it to email it fills a thunderbird email with the correct address.

But I was wondering is there a way to sync the adressbook in jpilot and thunderbird?

thanks,

---

### Post by dare2dreamer on 2007-02-25
What I ended up doing was using jpilot as my address book, and then setting the mailto command as:

<code>
mozilla-thunderbird -compose "mailto:%s" &
</code>

This allows me to locate an address in jpilot, click on the email button and get a thunderbird compose email window.

---

