---
title: "Remove need to enter sudo/su and password to carry out admin tasks?"
date: 2013-09-17
forum: General Help
---

### Post by bfitzp on 2013-09-17
I am the only person using my laptop and the only person who will ever be using it. I don't require the security feature of having to sudo/su every time I want to carry out some admin task. I have an account under my laptop under the name 'brian'. How can I set things up so that I never have to enter sudo/su and then a password when using this account?

---

### Post by Impavidus on 2013-09-17
Forum policy requires me not to answer that particular question and to provide you with this link: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Having that password not only offers some protection from other people with access to your computer (although physical access = root access), but also helps against remote attacks. It limits the consequences of for example a security leak in your web browser. It also protects you from ruining your system accidentally.

Furthermore, how often do you actually need sudo? I need it less than once a week.

---

### Post by CeejRab on 2013-09-17
Hello Bfitzp,

As impavidus noted, its a pretty good idea to have a root password for general security, but if you truly want no password you can follow the link they provided above. 

My thought would be rather than to remove the password, to make it something very simple for you to remember and type. It's really not that big of an intrusion to the experience, it takes a couple seconds. "An ounce of prevention is better than a pound of cure", and if you were unprotected it would need a whole lot of cure when just a pass code could help prevent it :) 

All the Best,

---

### Post by bfitzp on 2013-09-17
Cheers, yea I think I'll go with the old one letter password...that doesn't really disrupt the workflow too much.

---

### Post by buzzingrobot on 2013-09-17
I'm a frequent Fedora user, where you can do something close to what you're asking about.  But, in truth, there's only a marginal gain in convenience and a big and real increase in risk. For example, I've managed to accidentally remove the kernel. Oops. And, /home.  Oops, again.

---

### Post by deadflowr on 2013-09-17
I don't advocate or condone setting a no password Ubuntu system, but if you do be prepared to reinstall.
It is very easy to get careless and change some setting on a whim.
As the saying goes, power corrupts and absolute power corrupts absolutely.

Besides, after the initial setup the need to invoke a password should be slim anyway.

---

### Post by CeejRab on 2013-09-17
> **bfitzp said:**
> Cheers, yea I think I'll go with the old one letter password...that doesn't really disrupt the workflow too much.

..... Maybe just a couple characters at least? lol, i dont think it will let you use a one letter passcode even. I use something that i can type fast and that pops into my head whenever i see the prompt, plus it helps that i type around 70wpm so typing isnt much of an intrusion to me during my computing :)

---

### Post by Elfy on 2013-09-17
Closed.

You have the information you think you need.

Don't come back complaining if it all goes wrong for you.

---

