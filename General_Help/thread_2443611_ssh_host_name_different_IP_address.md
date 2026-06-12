---
title: "ssh host name different IP address"
date: 2020-05-17
forum: General Help
---

### Post by aapyan on 2020-05-17
I am having issues when trying to ssh into my university hostname. After I start my laptop and login (ubuntu 18.04) i can successfully ssh if i try immediately after login. But after 10-20 seconds if i try to ssh again it doesn't respond and eventually times out. When i try with -vv option i notice that the IP address has changed. Why does the hostname IP address change few seconds after login into my ubuntu? 
  
To summarize, it works if i try ssh-ing immediately after starting my laptop but after few seconds the hostname starts pointing to a different IP address that hangs and times out. This behavior started only few days ago.

---

### Post by HermanAB on 2020-05-18
It means that you have a lame DNS configured in your router.  Test the resolvers with 'nslookup' and 'dig' and check the configuration of your gateway router.

---

### Post by aapyan on 2020-05-18
Thank you Herman. I restarted my router and the problem disappeared. All good now :)

---

### Post by ActionParsnip on 2020-05-18
[https://isitdns.com](https://isitdns.com)

---

