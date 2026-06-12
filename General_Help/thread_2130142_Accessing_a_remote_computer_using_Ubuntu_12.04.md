---
title: "Accessing a remote computer using Ubuntu 12.04?"
date: 2013-03-28
forum: General Help
---

### Post by uzumakifahim on 2013-03-28
Hi,

I'm using Ubuntu 12.04; Remmina and Vino is installed on my system. Now I want to access another remote computer (which is in different network and IP is not static). 

Is it possible to do that? If so, then how can I connect? 

I'd really appreciate any help from anyone. Thanks in advance.

---

### Post by Slim Odds on 2013-03-28
Are the networks routeable? Do you know the address?

Yes, it is possible.

---

### Post by uzumakifahim on 2013-03-28
WOW!!! Really thanks for this prompt reply. 

Could you please clarify what do you mean by "routable"? I'm not very familiar with networking terms. 

Whatever, I'm on a wired network, have a static IP; but when I type on Google "what is my ip",it shows a different IP.

Another computer is using a wireless connection (4G), and IP is not static.

Hope this info can help you to understand the situation.

---

### Post by dcstar on 2013-03-28
> **uzumakifahim said:**
> WOW!!! Really thanks for this prompt reply. 

Could you please clarify what do you mean by "routable"? I'm not very familiar with networking terms. 

Whatever, I'm on a wired network, have a static IP; but when I type on Google "what is my ip",it shows a different IP.

Another computer is using a wireless connection (4G), and IP is not static.

Your IP is irrelevant, you just need to know the remote IP. You have to set up the network of the remote PC to allow traffic from the Internet through to the PC as required by the particular remote connection method you want to use.

You should be able to search out detailed instructions for the router/firewall hardware of the remote network on how to do this.

---

### Post by uzumakifahim on 2013-03-28
@dcstar, Thanks for your clarification. Remote computer is using dynamic addressing, so I know the WAN IP address of that computer. Is that WAN IP address enough to connect to that computer? When I google "what is my ip" from that (remote) computer, it also shows me same IP address (WAN).

Now please help me about the next step to connect.

---

### Post by uzumakifahim on 2013-03-29
I understand that, to connect to a remote PC, I need to input the WAN address of that remote PC. No problem with that. 

Fact is that, there are more that 30 PC under that WAN address. So, how it'll find that specific remote computer between those 30 computers, that I need to connect?

Please tell me details. I need this solution very badly.

Thanks in advance.

---

### Post by steeldriver on 2013-03-29
that would be done by forwarding a port from the WAN side of the router to the specific remote computer on the LAN - the details will depend on your router but there is a fairly good general explanation here [http://www.realvnc.com/support/portforward.html](http://www.realvnc.com/support/portforward.html)

---

### Post by uzumakifahim on 2013-03-29
> **steeldriver said:**
> that would be done by forwarding a port from the WAN side of the router to the specific remote computer on the LAN - the details will depend on your router but there is a fairly good general explanation here [http://www.realvnc.com/support/portforward.html](http://www.realvnc.com/support/portforward.html)

@steeldriver - OHHH!!! Really thanks. That means I can do this job without any proprietary solution. I can do this with Remmina or Vinagre and Vino. But I have keep in mind that points. Is that it?

---

### Post by uzumakifahim on 2013-03-29
I have read the all of that link, but I have two question

[LIST=1]
[*]In "**Accessing more than one computer**" section; how many port can I forward like this? Is there any limitation?
[*]It seems it's working for static IPs, but what about Non-static (Dynamic IP)?
[/LIST]

---

### Post by Slim Odds on 2013-03-29
> **uzumakifahim said:**
> I have read the all of that link, but I have two question

[LIST=1]
[*]In "**Accessing more than one computer**" section; how many port can I forward like this? Is there any limitation? 
[*]It seems it's working for static IPs, but what about Non-static (Dynamic IP)? 
[/LIST]

Computer networks are not magic, they use very well defined protocols. If you can find the IP using DNS, they you're good to go. If not, then you might have a problem.

How about a description of the network that you are trying to use? That would help immensely. It's a little hard to answer these types of questions without some details.

---

### Post by uzumakifahim on 2013-03-29
Actually I pretty new with this remote desktop thing, that's why maybe sometime my questions are not logical. I can't understand the whole thing yet. So, sorry for that.

Whatever, end point is that, Is possible to connect to remote computer using dynamic IP over the Internet, by using software Remmina or Vinagre and Vino? If so, then is there any simple step by step guide for this? I need a free but GUI based solution.

---

### Post by Slim Odds on 2013-03-30
> **uzumakifahim said:**
> Actually I pretty new with this remote desktop thing, that's why maybe sometime my questions are not logical. I can't understand the whole thing yet. So, sorry for that.

Whatever, end point is that, Is possible to connect to remote computer using dynamic IP over the Internet, by using software Remmina or Vinagre and Vino? If so, then is there any simple step by step guide for this? I need a free but GUI based solution.
I could help you if you'd give some information. Since you can't, I can't.

---

