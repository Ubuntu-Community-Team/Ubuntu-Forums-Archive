---
title: "How to Port forward over ssh"
date: 2007-05-08
forum: General Help
---

### Post by vav on 2007-05-08
I run software which needs a license to be checked out from a server. I'm not able to do this from home though, since the server accepts access only from it's domain. 

My license file reads: license=<four_digit_num>@<server.domain>

So I'm guessing the license is available at <four_digit_num> port of the server <server.domain> right?

I do have an ssh login to the server though. I was told I could possibly use port forwarding on Ubuntu to connect the license manager to the server through ssh... how do I do this?

Thanks!

---

### Post by sadaraine on 2007-05-10
Hey Vav - check out gstm at gstm.sourceforge.net (you can get it in synaptic by searching for gstm).  It is a front-end used to manage ssh tunneled port redirects which should accomplish what you need.  I've used a similar function to do some remote work.  The terminology you want to use to search for more information is "ssh tunnel".

---

### Post by vav on 2007-05-11
Thanks for that link... it's a great piece of s/w. However, I'm still unable to get through...

The issue is like this:
There's a license file variable defined as [email]5280@server1.doma[/email]in1
If my laptop is in domain1's internal network, I can run the software.

I have a ssh login to another server [email]mylogin@server2.doma[/email]in1
This server also runs the software I want, and in it's bash environment, there's the same license file variable. And it's always able to connect to 5280@server1 since it's in domain1. 

I asked the admin of domain1 if I could get access to [email]5280@server1.doma[/email]in1, but he said that would allow anybody on the internet to get the license to the s/w, so he cant allow that, but I should try port forwarding over ssh. He didnt say exactly how though. So all I have is port 22 access to server2.domain1

What steps do I follow? Basically it seems like I have to use my credentials on server2 to get access to the 5280 port at server1... is this possible through gstm?
I tried a few combinations with gstm but it doesnt work... :( I've never done tunneling before.

Thanks

---

### Post by vav on 2007-05-11
bump...
anyone please?

---

### Post by kennythegeek on 2007-06-24
can't help you with gstm, but i can help you with tunnelling.

Do you want to tunnel from your own computer to server1.domain1? or to ssh to server2.domain1 and then make the tunnel to the other server?

do you know if port 22 is open at the other server? and if it got ssh? if it is, it is simple enough:
```
ssh -fNL port1:localhost:port2 5280@server1.domain1
```

port1 is the port on server1 you want access to, port2 is the port that it will connect to on your computer.

---

