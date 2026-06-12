---
title: "internet not working?"
date: 2005-09-07
forum: General Help
---

### Post by mastershake on 2005-09-07
im completly new to linux and just installed ubuntu from the live cd. for some reason my internet is not connecting. i am using a dell with wireless cable, the internet is fine on every other computer in my house. can any one help me?

---

### Post by mlomker on 2005-09-07
Wireless can be difficult to get working.  If you have a wired ethernet connection then I'd recommend trying that and figuring out the wireless as you go.

You'll have to start by figuring out what driver you'll need for the wireless card (if there is one for linux).

**lspci** at a command prompt will give you a list of hardware that linux can see inside your machine...one of them should be the chipset of your wireless card.

---

