---
title: "SSH port blocked. Access through different ports?"
date: 2008-06-03
forum: General Help
---

### Post by kevlarRelic on 2008-06-03
I've been using Ubuntu on my desktop for a month and it has changed the way I think about computers.

That is why I set my desktop up to do SSH while I'm away from home on this trip.

My problem is that when I arrived at the place I'd be staying, I discovered that they had port 22 blocked on their router, which is the port I had my home router set up to forward SSH to my desktop. 

So my question is if there is any way to connect to my home desktop , and if it is even a problem that port 22 is blocked here? 

I have no access to my home router or computer ( they are far far away ), and I am using putty and winscp on my sister's windows laptop. 

This is all so new to me, and I guess this isn't really a ubuntu specific problem, but the people on ubuntu forums have been the nicest and most helpful people since I started using linux, I know you can help me out. Thanks. :)

---

### Post by Joeb454 on 2008-06-03
I don't think there is, because you'd have to forward port xxxx on your router to port 22 on your PC at home.

Now if somebody else at home knows how to set up port forwarding on your router, then that'd be fine :)

If they can, you would run ```
ssh user@ipAddress -p <port>
```

Don't forget you'll need to know your IP (unless you have a dyndns/domain set up to point there)

---

### Post by kevlarRelic on 2008-06-03
Thanks for the response Joeb454! I was afraid of that. 

On a related note, does anyone know of a public wireless access point in or around Dallas Texas where port 22 would be open? For example, would the wireless at Starbucks allow me to ssh to my router and set up the port forwarding?

---

### Post by Joeb454 on 2008-06-03
Hehe :p

I don't think Starbucks would, though I'd say it's worth a try :)

---

### Post by rkolb86 on 2010-05-22
The problem is probably not the location from where you are attempting to connect from. 

The problem probably lies within your ISP or YOUR router. Did you set up port forwarding in your router? Does your ISP block incoming connections on port 22? did your IP address change? So ISPs will tell you know, but they lie...believe me. Usually they only block 80 and 25 on residential connections, but i've seen some crazy stuff.

---

