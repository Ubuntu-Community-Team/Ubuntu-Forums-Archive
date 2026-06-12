---
title: "Recommended dynamic dns and ssl certificate provider"
date: 2018-08-10
forum: General Help
---

### Post by freeflyjohn on 2018-08-10
I have been using the free dynamic DNS service from DYNU with the ddclient update tool but it never works, when my IP address changes it does not get updated at DYNU even though ddclient seems to be working as far as I can tell.

I also have an https address (for Nextcloud) but as there is no registered SSL certificate the warning page appears.

Because of these issues I am looking for recommendations for an alternative provider which will also provide an SSL certificate, I am prepared to pay for the service (e.g. a yearly subscription of £20) if necessary just to overcome these issues.

Can anyone recommend a service that will meet my needs ?

---

### Post by SeijiSensei on 2018-08-10
First get a static IP from your provider if you want to run a server. Everything will be much easier.

---

### Post by freeflyjohn on 2018-08-11
Unfortunately a static IP is not a viable option - as I have FTTP (Fibre to the property) which can only be supplied by BT. BT only offer static IP for business tariffs and I’m already paying an extortionate £56.99 a month for a residential tariff (Superfast Fibre 2 Unlimited inc. landline) so I would hate the think how much the business tariff would cost. The static IP on the business tariff also costs an additional £5.50 a month! I’ve tried shopping around for other ISPs but they are not available in my area (which is a new build estate). When I tell them it’s FTTP they tell me that BT will be my only option, so BT have a monopoly as my only ISP

---

### Post by dragonfly41 on 2018-08-11
You can try this .. [https://ngrok.com/](https://ngrok.com/)

---

### Post by freeflyjohn on 2018-08-12
> **dragonfly41 said:**
> You can try this .. [https://ngrok.com/](https://ngrok.com/)

Thanks dragonfly41, having looked at ngrok I have no idea what its about :-/

---

### Post by The Cog on 2018-08-12
Then all traffic passing to/from your site has to pass via ngrok's servers. I'm not sure I would want that.

---

### Post by dragonfly41 on 2018-08-12
That might be the case for sensitive data but surely no worse that other servers?
ngrok allows demonstrators to be setup but I would not use it for financial transactions.

However another thought.
I transferred my domain accounts from a registrar (who was closing down) over to Google Domains.
Google Domains offers a range of services such as static IP addresses and web forwarding.
So your front office website could be a micro instance on Google Cloud
but forwarded to your home based server.  
I have in mind that you could experiment by using ngrok on your home computer and giving the ngrok URL address to Google forwarding.

[https://support.google.com/domains/answer/4522141?hl=en](https://support.google.com/domains/answer/4522141?hl=en)

A bit convoluted.
Otherwise check out the pricing of dyndns or zoneedit.

---

### Post by SeijiSensei on 2018-08-13
Another option is to lease a VM in the cloud from a company like [Linode]("http://www.linode.com/").  They start at $10/month.  I no longer have any physical servers, and never have to worry about disk crashes, power outages, etc.

---

