---
title: "Extra bits added to Evolution web links"
date: 2008-01-12
forum: General Help
---

### Post by otchie1 on 2008-01-12
Most web-links and embedded urls I receive in Evolution are simple and work just fine. More complex ones embedded in html mail fail.

Real url,

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=280191498569](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=280191498569)

Evolution url

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&amp;item=280191498569&amp;ssPageName=ADME:B:SS:GB:1123](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&amp;item=280191498569&amp;ssPageName=ADME:B:SS:GB:1123)

The extra junk is right there on the Evolution source,

Item URL:             =20
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=3D280191498569](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=3D280191498569)

I assume it's due to non-compliance to MS 'standards' but is there a work around?

---

### Post by dcstar on 2008-01-12
> **otchie1 said:**
> Most web-links and embedded urls I receive in Evolution are simple and work just fine. More complex ones embedded in html mail fail.

Real url,

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=280191498569](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=280191498569)

Evolution url

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&amp;item=280191498569&amp;ssPageName=ADME:B:SS:GB:1123](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&amp;item=280191498569&amp;ssPageName=ADME:B:SS:GB:1123)

The extra junk is right there on the Evolution source,

Item URL:             =20
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=3D280191498569](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=3D280191498569)

I assume it's due to non-compliance to MS 'standards' but is there a work around?

It is possibly a default Code Page setting that doesn't agree with the HTML e-mail, you may want to experiment with Edit-Preferences-Mail Preferences-General-Default Character Encoding and see if changes make any difference.

Mine is defaulting to UTF-8, maybe ISO-8859-1 is worth a try?

---

### Post by otchie1 on 2008-01-18
> **dcstar said:**
> It is possibly a default Code Page setting that doesn't agree with the HTML e-mail, you may want to experiment with Edit-Preferences-Mail Preferences-General-Default Character Encoding and see if changes make any difference.

Mine is defaulting to UTF-8, maybe ISO-8859-1 is worth a try?

I was using iso8859-1

I've stuck it back to UTF8.

I just now have to wait for a suitable email to check it out. Ebay is usually obliging.

---

### Post by otchie1 on 2008-01-19
Nope, didn't help.

If I forward the mail to a web account it works fine. It even works fine if I copy the Inbox over to a dummy Thunderbird install. must be something to do with html reading...hmmmmm

---

### Post by otchie1 on 2008-04-06
Never sorted this so solved it by flushing Evolution and installing Thunderbird.
Superior in every respect and it's still an 'active' project so things get fixed.

---

