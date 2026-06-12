---
title: "SSH forwarding help needed!!!"
date: 2006-09-21
forum: General Help
---

### Post by moufranica on 2006-09-21
Dear Gurus,
I am trying ssh tunneling and my command binds to localhost but not to the IP address bond to eth0. Here is the command line I used:
  **ssh -L 8080:<myexternalip>:443 - p <loginame>@<myexternalbox>**

This works fine, but I can only use it on localhost, but not from my other machines. What changes do I have to make? Thanks so much in advance. :)

---

### Post by markymarknz on 2006-09-21
> **moufranica said:**
> Dear Gurus,
I am trying ssh tunneling and my command binds to localhost but not to the IP address bond to eth0. Here is the command line I used:
  **ssh -L 8080:<myexternalip>:443 - p <loginame>@<myexternalbox>**

This works fine, but I can only use it on localhost, but not from my other machines. What changes do I have to make? Thanks so much in advance. :)

I'm not a guru but might be able to help a bit.
What are your other machines that you try to run that command off?
Are they linux machines as well?

---

### Post by moufranica on 2006-09-22
> **markymarknz said:**
> I'm not a guru but might be able to help a bit.
What are your other machines that you try to run that command off?
Are they linux machines as well?

Hi Marky,
I have got it working now. What was happening was my forwarding was bond to localhost:8080. That way my other machines in the network could not access this forwarding service. Now I have it bond to the IP address rather than "localhost". I didn't read ssh --help more properly. :) Thanks for you support and willingness to help me. It is working now. Here is my new command that made it work.

```
ssh -L <mylocalip>8080:<myexternalip>:443 - p 443 <loginame>@<myexternalbox>
```

My orignial command was this:
```

ssh -L 8080:<myexternalip>:443 - p 443 <loginame>@<myexternalbox>

```
As you can see, I did not add the local IP address to which I wanted forwading (on 8080). Hence it defaulted to localhost and I was not able access 8080 from my network. Now I have so many other quetions as I start setting up Ubuntu. Like getting Tapioca  VoIP working (it has no options to add Proxy), adding a local repo for my network and general manteniance of a Ubuntu Network. I am migrating my machines at work to Ubuntu. :) I will post these on new threads. Keep me cheered guys. I need that sometimes. ;)

---

