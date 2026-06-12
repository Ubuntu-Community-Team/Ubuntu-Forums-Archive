---
title: "Evolution and exchange.1and1.com"
date: 2007-03-20
forum: General Help
---

### Post by raymond3 on 2007-03-20
I am really trying to avoid booting into windows as much as possible but I use an exchange email account so I get push mail on my phone as well as have my contacts, calendar, and tasks all synced over the air.

I can't get evolution to connection to 1and1.com's server.  I emailed them and they just replied that they only support Outlook.  They use RPC over HTTP.

Does anyone know how to get evolution to connect to this?  Alternatively, does anyone know of a hosted exchange company that does push email and will support evolution?

I've tried using IE4linux so I could at least get a decent OWA interface but it crashes every time a reminder popup happens.

Thanks for any help.

---

### Post by chocbar31 on 2007-03-20
Have you looked here?

[http://www.novell.com/coolsolutions/trench/16234.html]("http://www.novell.com/coolsolutions/trench/16234.html")

I get in this way:

mail.myuniversity.edu/exchange

---

### Post by obojarski1 on 2007-06-25
raymond3,

Did you ever get it working? I am having the same problem...
Thanks!

---

### Post by tr1xter47 on 2007-12-16
i just started using ubuntu, and been having problems with exchange.1and1.com

try using [http://217.160.230.241/exchange](http://217.160.230.241/exchange)

and use the 217.160.230.241  for the GAL

Evolution may seem like it has froze and may crash out, but its just downloading your contacts in mail.


it worked for me:)

---

### Post by PrincessNybor on 2008-03-21
Just a quick update on this, as it's the first hit on Google for this issue, and I have spent the past several days trying to make this work. For me, the IP address above did not do the trick, but the following did.

[http://legacy.exchange.1and1.com/exchange](http://legacy.exchange.1and1.com/exchange)

You must type that in exactly as it appears, or it will not work. Using https:// makes it fail, adding a trailing slash makes it fail, and leaving off /exchange makes it fail. I also found that entering your actual username (for example, e123456789) instead of your exchange e-mail address is more reliable, but your mileage may vary. 

1and1 certainly hasn't made this easy on us! They are somehow using the Exchange 2007 OWA login by default, even with existing Exchange 2003 accounts. This legacy address takes you to the Exchange 2003 OWA login. However, they did guarantee that this address would continue to work, and that my account would not be upgraded to Exchange 2007 unless I explicitly requested it.

Nonetheless, I hope the Evolution team gets full MAPI over HTTP working in the near future! OWA is a great backup solution, but I would still love to get MAPI.

---

