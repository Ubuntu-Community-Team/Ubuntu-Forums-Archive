---
title: "Postfix setup sending emails but cannot send emails with client"
date: 2020-10-20
forum: General Help
---

### Post by hungrygeneration on 2020-10-20
[FONT=arial][SIZE=3][SIZE=4][SIZE=2]So I can send emails with the mail command from command line but when I try to send emails externally with SMTP I am getting the message, [/SIZE]"The Server refused to allow a connection on port 587." Do you know what could be going wrong? I am just trying to set up a server to send mail not receive it. I have set it up as loopback and even set up [COLOR=#000000]opendkim. Thanks so much!![/COLOR][/SIZE][/SIZE][/FONT]

---

### Post by SeijiSensei on 2020-10-20
Try using port 25 instead.  If you're talking to localhost, there aren't any security issues.  I have an SMTP server in my home office. It uses no authentication and plain-text SMTP on port 25. Only the machines in my house can see it.

---

### Post by hungrygeneration on 2020-10-21
Just tried port 25. I'm getting the same message? I am on an outside network. Should I try an inside network? Would that help with troubleshooting?

---

### Post by TheFu on 2020-10-21
Did you setup port forwarding on the wan router?

---

### Post by SeijiSensei on 2020-10-21
You won't be able to see the server unless you set up port forwarding as TheFu suggests. However, I don't think that's what you want to do.

Where are the emails you intend to send originating? On the server? On the server and the local network? If those are the only cases, you don't want to the server to be visible from outside your network. If you just need to send locally-originating mail, then you should be testing from within the local network.

---

### Post by hungrygeneration on 2020-10-22
> **TheFu said:**
> Did you setup port forwarding on the wan router?
Yes port forwarding is set up and I did confirm that Google Fiber does not block those ports. 

No I do want it accessible from the outside. That is the whole point. I want to be able to use it as a SMTP server externally. I am trying to set up email services to accompany my web server I have already set up.

---

### Post by SeijiSensei on 2020-10-22
By default Postfix is configured only to listen on the localhost interface for security reasons.  You need to change the "inet_interfaces" directive in main.cf.  Choose
```
inet_interfaces = all
```
to have the server listen on all interfaces. Restart Postfix. Any better?

If you do this, you'll need to make sure you're not creating an "open relay." Read this at least twice: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html).  When you think you have everything set up correctly, test the server's configuration with [https://mxtoolbox.com/diagnostic.aspx](https://mxtoolbox.com/diagnostic.aspx).

---

### Post by hungrygeneration on 2020-10-22
> **SeijiSensei said:**
> By default Postfix is configured only to listen on the localhost interface for security reasons.  You need to change the "inet_interfaces" directive in main.cf.  Choose
```
inet_interfaces = all
```
to have the server listen on all interfaces. Restart Postfix. Any better?


Unfortunately that is already set as all :-/ but I will read through what you sent and just see if I can figure it out. I might have missed something when I was setting up? I'll let you know after that if I still can't figure it out.

---

### Post by ActionParsnip on 2020-10-22
Did you configure the firewall on the email server? If so did you allow the port to be accessible from your client?

---

### Post by hungrygeneration on 2020-10-22
Ok so good news I do have a successful configuration now. After reading the article you sent I realized I had never updated the domain in my main.cf. I am testing on an alternative domain before bringing it live to my main domain. I have never gotten this far so thank you!!
But I am still having authentication problems I'm guessing? How do I set up an account? I tried using my admin email / password I set up for authentication but that is a different domain (since I am testing on the alternative domain which is just a forwarder domain). How do I set up an account with this alternative domain??

---

### Post by SeijiSensei on 2020-10-22
I don't know. I don't use authenticated SMTP. You'll have to consult the Postfix documentation for that. As you can see from the piece you read, it's pretty extensive.

You also might want to look into using a database for this.  I can imagine that user names in the database aren't limited to the same domain.

---

### Post by hungrygeneration on 2020-10-24
Well how can I set it up to not require authentication?
Also this is my latest crazy idea :) but what do you think about setting up something like Froxlor or some kind of management software. I am learning all the commands and even got the HTTP/HTTPS set up fine but this one has been crazy! Just thinking software that will do it for me sounds like a good idea!! &#55357;&#56834;

---

### Post by TheFu on 2020-10-24
Look up "open relay".

I suspect that is not your goal. Open relays on the internet get into block lists very,very quickly and can be hard to get removed.  OTOH, allowing email from specific subnets that you control.

There are multiple opinions about using front-ends to any configuration.  I don't mind, provided there is someone involved who can manually manage the config files. The problems arise when someone running things doesn't have sufficient expertise to fix things when the config tools fail.  They always fail. Always.  Basically, they have to start over, learn the things they didn't learn the first time, but under production failures, usually with lots of unhappy people waiting.

---

### Post by SeijiSensei on 2020-10-24
> **hungrygeneration said:**
> Well how can I set it up to not require authentication?

If you want to accept mail from anywhere, you need to use authentication.  [http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html)

If you can restrict the set of hosts permitted to send mail through the server, you can impose limits by IP address or network. Read that ACCESS readme again.

I'm pretty sure the perpetrators of the recent "Proud Boys" [email spoof]("https://www.zdnet.com/article/us-blames-iran-for-spoofed-proud-boys-emails-threatening-democrat-voters/") used open relays (allegedly in Estonia) to try and hide their tracks.

---

