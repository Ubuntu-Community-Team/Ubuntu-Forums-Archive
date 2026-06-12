---
title: "Simple SOCKS Proxy setup under Linux"
date: 2014-03-29
forum: General Help
---

### Post by Robbyx on 2014-03-29
I came accross this guidance and have followed it as far as possible:

[http://www.noobslab.com/2014/03/browse-internet-as-nobody-knows-what.html](http://www.noobslab.com/2014/03/browse-internet-as-nobody-knows-what.html)

I now find that web pages open quicker in Firefox.

Is there a way of checking if I have followed the advice properly and my trafic is now encrypted?

The article became unclear to me about half way down:

In firefox I only changed the network settings  to manual. All the field were left untouched.

I have then run 
ssh -N -D 0.0.0.0:1080 localhost

and nothing further. 

How does this encryption system work? Not, the detail just is the whole of the browsing enrypted or just the first hop?

I ask because I do not understand what is  decrypting my ssh encrypted browsing.

---

### Post by Robbyx on 2014-03-29
The socks proxy did not prevent piratebay from being blocked by my ISP. Does this mean I have not set up the socks SSH properly?

---

### Post by QDR06VV9 on 2014-03-29
> **Robbyx said:**
> The socks proxy did not prevent piratebay from being blocked by my ISP. Does this mean I have not set up the socks SSH properly?
I think you missunderstood.
```
It is not like VPN, **_since rules are already set by your ISP and you  can't access blocked sites by this method. It just encrypt stuff._**
The  reason is that you are using your ISP DNS and your ISP already set  rules to block some site and you are behind that rules, so when you 
 request for something your request goes via SSH Tunnel with encryption  then your ISP DNS start looking for address and found it is already  blocked 
in the rules then it returns you result(as blocked or allowed).
This method has only one purpose that nobody is able to log your requests. *I didn't mention anywhere in the post that you can access blocked sites.*
In order to access blocked sites you need to use VPN service or you have to create them by yourself(it will be hard).
```

---

### Post by QDR06VV9 on 2014-03-29
> **Robbyx said:**
> 
The article became unclear to me about half way down:

_In firefox I only changed the network settings  to manual. All the field were left untouched._

I have then run 
ssh -N -D 0.0.0.0:1080 localhost

and nothing further. .

You will have to add.
```
localhost Port=1080 
```
So it will look like this <Socks Host localhost Port 1080>
Attachment provided

And here what my open ports show now<Attachment>

---

### Post by Robbyx on 2014-03-30
I have sorted this. See next posting.

Since switching to SSH via the instructions at 
[http://www.noobslab.com/2014/03/brow...nows-what.html](http://www.noobslab.com/2014/03/brow...nows-what.html)

and 

including the opendns addresses  my browsing is ok, but 

thunderbird  no longer gets my POP3  mail from  googlemail. Nothing happens.

I think I have been trying to mix water and oil. What should I change?

This is  what I  have done:

Network Proxy: Proxy= manual,  Socks host = localhost/1080
Network Wired: IPv4 Setting= Auto (DHCP) address only, DNS servers 208.67.222.222, 208.67.220.220

In Firefox: Manual proxy configuration,  socks v5, no proxy for locashost, 127.0.0.1
 all the rest blank

In Thunderbird: proxy=manual, socks host =localhost, 1080


Router: not altered

Is it possible to mix SSH with opendns?

---

