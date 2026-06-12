---
title: "Bypass VPN connections"
date: 2015-06-29
forum: General Help
---

### Post by zergling on 2015-06-29
Hello everyone, I am opening this thread because I am having issues in sending email through a VPN connection and I was wondering if there was a way to bypass it with Linux.

I know that my VPN provider offers an application to do that in Windows [http://support.vpnsecure.me/articles/tips-tricks/send-email-with-vpn-secure](http://support.vpnsecure.me/articles/tips-tricks/send-email-with-vpn-secure)
but of course, they do not offer any kind of help in Linux :(

My machine does not have any issues sending email without the VPN tunnel but once I activate it, I get the following error

```

zergling@ubuntu:~$ sudo ssmtp xxxxx@gmail.com
[sudo] password for zergling: 
test email
ssmtp: Cannot open smtp.gmail.com:587

```

I have been trying different configuration with my iptables and I tried also different tutorial but still, it does not work :(

Probably, I made some mistakes along the way because I have never modify/create new rules/iptables.

So, could someone please help me out with this?

Bye and thank you in advance :)

---

