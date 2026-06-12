---
title: "Problem with whatsapp service (possibily chrome rendering?)"
date: 2020-04-27
forum: General Help
---

### Post by Briga on 2020-04-27
Hi, I have just made a fresh installation of Ubuntu 20.04 (no upgrade). 

Most works well but few things, one of them is applications like Franz or Rambox or All-in-one-messenger. They all share the same issue. Telegram and other services works nice but whatsapp service is rendered with no text only media. 

Here is a screenshot taken from Rambox 
[IMG]https://i.ibb.co/0yzD2S8/Screenshot-from-2020-04-27-15-18-24.png[/IMG]

I believe (but I am not sure) the rendering is done with chrome. In 18.04 they were working just fine without chrome installed. Here I tried to install the latest stable chrome but to no use.

web.whatsapp.com on Firefox works well.

Any one any idea?

Thanks

---

### Post by ActionParsnip on 2020-04-27
I suggest you report a bug

---

### Post by CelticWarrior on 2020-04-27
I suggest you use a different theme or just keep the defaults.

---

### Post by Briga on 2020-04-27
> **CelticWarrior said:**
> I suggest you use a different theme or just keep the defaults.

Thanks for the reply.... what theme are you suggesting? Franz (or the other apps) they don't have a theme (or if there's one I haven't changed it) and Ubuntu I am running the default one from installation.

---

### Post by Briga on 2020-05-03
I eventually find a solution to it and I am posting it here for any one who may encounter the same issue along the way. 

The problem is the user agent passed. With rambox you can override it in the preferences. Go there and as a user agent I am using:
Mozilla/5.0 (Macintosh; Intel Mac OS X 10.12; rv:58.0) Gecko/20100101 Firefox/58.0

This fixed whatsapp. 

Since it works also in firefox (via web.whatsapp.com) you can also launch Firefox, Google search "What is my User Agent" and copy and paste the text Google reports back to you in the preferences of rambox.

Best of luck

---

