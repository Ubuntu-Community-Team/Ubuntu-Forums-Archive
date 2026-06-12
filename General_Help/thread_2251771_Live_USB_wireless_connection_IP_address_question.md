---
title: "Live USB wireless connection IP address question"
date: 2014-11-06
forum: General Help
---

### Post by Penguin360 on 2014-11-06
I boot my laptop up with Live USB and then connect to my company's wireless network. Everything works fine but I notice one interesting thing:

When I run ifconfig wlan0, it shows my IP address is 10.161.55.29, as far as I know, this is an internal IP address. Then I see an IP6 address in the list. Is it because my computer uses IP6 address instead of IP4? How can I see my actual IP4 address?

Thanks,

---

### Post by ringstaart on 2014-11-06
If all you need is your public ip address, and it doesn't really matter how you get it, just search for "what is my ip" on Google or Duckduckgo. Both will show you above the results, without you even needing to click anything.

---

### Post by Penguin360 on 2014-11-06
> **ringstaart said:**
> If all you need is your public ip address, and it doesn't really matter how you get it, just search for "what is my ip" on Google or Duckduckgo. Both will show you above the results, without you even needing to click anything.

Thank you.

I did a Google search and it show my IP starts with 192.XX.XXX.XX, still an internal address, isn't it? (I am not behind any router. My Windows computer shows a public IP address, not internal IP address).

I ask this question out of curiosity, and am trying to understand if it is related to Live USB.

---

### Post by ringstaart on 2014-11-06
> **Penguin360 said:**
> Thank you.

I did a Google search and it show my IP starts with 192.XX.XXX.XX, still an internal address, isn't it? (I am not behind any router. My Windows computer shows a public IP address, not internal IP address).

I ask this question out of curiosity, and am trying to understand if it is related to Live USB.
If it's 192.168.XXX.XXX, it's an internal ip address, but if the second number isn't 168, I believe it's a public one.

There's no way for search engines to get your local ip address anyway, without executing code locally. It's easy to get your public one - they need it to send you anything at all.

---

### Post by nerdtron on 2014-11-06
> **Penguin360 said:**
> Thank you.

I did a Google search and it show my IP starts with 192.XX.XXX.XX, still an internal address, isn't it? (I am not behind any router. My Windows computer shows a public IP address, not internal IP address).

I ask this question out of curiosity, and am trying to understand if it is related to Live USB.

10.x.x.x - Private IP
192.168.x.x - Private IP
172.16.x.x - Pricate IP

If you want to know you Public IP you should use "www.whatismyIP.com" to see you IP address.

As for desktop and wireless connection, It can be that your LAN connection uses different IP addressing that the wireless connection.

---

### Post by Penguin360 on 2014-11-06
> **nerdtron said:**
> 10.x.x.x - Private IP
192.168.x.x - Private IP
172.16.x.x - Pricate IP

If you want to know you Public IP you should use "www.whatismyIP.com" to see you IP address.

As for desktop and wireless connection, It can be that your LAN connection uses different IP addressing that the wireless connection.

Ah, you are right. My wireless connection does use different IP addressing than the wired connection. I didn't realize it.

But why ifconfig command cannot give my the public IP even though my connection is public (not behind router)?

---

### Post by nerdtron on 2014-11-06
> But why ifconfig command cannot give my the public IP even though my connection is public (not behind router)?

Are you sure about that? A wireless router will surely NAT you to another IP (probably your Public IP)

---

