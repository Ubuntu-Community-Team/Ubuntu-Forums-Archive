---
title: "Internet Security"
date: 2007-03-02
forum: General Help
---

### Post by cj100570 on 2007-03-02
Back when I was a Windows user I had a program called Internet Guard Dog on my computer and it was a great piece of software that stopped every bit of information I didn't want leaving  my computer from going anywhere without my permission. It worked so well that I could send email out that said from [email]unknownuser@unknown.com[/email] simply by adding my email address to the blocked list. You'd be amazed at what information web sites query your pc for.

Anyway, my question is this; is there any program for Linux that can be used to block personal information (name, phone #, address, etc.) from being transmitted from a pc to the web without the users permission? [-o<

---

### Post by kidders on 2007-03-02
Hi there,

The short (glib) answer to your question is that, on a non-MS machine, *nothing* happens without permission.

Having said that, I'm sure there are some things you could try to keep accidents to a minimum. For instance, you could use a web proxy to filter information being posted to remote servers, or a local mail gateway to keep tabs on what's coming in and out that way.

As far as I'm aware, nothing quite like what you're describing exists (or needs to exist) for Linux, but I'm sure you could put something together quickly, depending on your requirements.

Is there something in particular you're concerned about?

---

### Post by cj100570 on 2007-03-02
> **kidders said:**
> Hi there,

The short (glib) answer to your question is that, on a non-MS machine, *nothing* happens without permission.

Having said that, I'm sure there are some things you could try to keep accidents to a minimum. For instance, you could use a web proxy to filter information being posted to remote servers, or a local mail gateway to keep tabs on what's coming in and out that way.

As far as I'm aware, nothing quite like what you're describing exists (or needs to exist) for Linux, but I'm sure you could put something together quickly, depending on your requirements.

Is there something in particular you're concerned about?

I agree that programs can't install without permission! But any information that has been entered into a browser such as addresses, phone #'s, etc. can be queried and sent out onto the web without your knowledge. A friend and I conducted a little test by using an Ubuntu cd to run Linux on his laptop and use the internet connection from my pc to get him online. We then set internet guard dog on my Windows box, actually it's just a hard drive that I keep windows on for emergencies, to block his name, address, phone #, etc. Then we used Firefox, on his laptop, to surf around to various sites that required his name, address and various other info. Sure enough,  internet guard dog popped up a warning that sites were trying to get the info as we surfed around the net. So that got me to wondering if any program such as internet guard dog exists for Linux.

---

### Post by kidders on 2007-03-02
> **cj100570 said:**
> any information that has been entered into a browser such as addresses, phone #'s, etc. can be queried and sent out onto the web without your knowledge.Some browsers offer to store details like that to auto-fill forms, etc. It's a daft thing to actually do though!

I'm sure you could manipulate squid into handling this for you.

---

### Post by Shatrat on 2007-03-02
Looks like crap you don't need anyway.
Also, it is not difficult at all to create emails with spoofed addresses, but they will probably get tagged as spam most of the time by any kind of filtering that checks the domain name against the originating IP address.

Sounds like this program is just a compares strings in outgoing TCP data to strings in a blacklist of personal data.  The fun implication here is that this 'guard dog' software maintains a blacklist of things you dont want other people to know in a handy location.  You could achieve the same result with firefox and the noscript plugin without the hassle.
This is a sugar pill for people who want to feel secure.

---

### Post by cj100570 on 2007-03-02
> **Shatrat said:**
> Looks like crap you don't need anyway.
Also, it is not difficult at all to create emails with spoofed addresses, but they will probably get tagged as spam most of the time by any kind of filtering that checks the domain name against the originating IP address.

Sounds like this program is just a compares strings in outgoing TCP data to strings in a blacklist of personal data.  The fun implication here is that this 'guard dog' software maintains a blacklist of things you dont want other people to know in a handy location.  You could achieve the same result with firefox and the noscript plugin without the hassle.
This is a sugar pill for people who want to feel secure.

You lost me with your response. I have noscript installed on Firefox but that has nothing to do with preventing personal information from being sent out onto the web. If it's possible for a website to query your pc for information stored in the browser I would consider any program that prevents that info from being sent to be more than a "sugar pill". I'd call it a Godsend! As I stated earlier, you'd be amazed at the information websites ask for from your pc when you visit them. I had always assumed that this wasn't an issue with Linux. But obviously it is. Although I have Firefox set to delete all information each time it closes, that doesn't change the fact that the info is accessible as long as the browser is open.

---

### Post by kidders on 2007-03-02
> **cj100570 said:**
> You lost me with your response. I have noscript installed on Firefox but that has nothing to do with preventing personal information from being sent out onto the web. If it's possible for a website to query your pc for information stored in the browser I would consider any program that prevents that info from being sent to be more than a "sugar pill". I'd call it a Godsend! As I stated earlier, you'd be amazed at the information websites ask for from your pc when you visit them. I had always assumed that this wasn't an issue with Linux. But obviously it is. Although I have Firefox set to delete all information each time it closes, that doesn't change the fact that the info is accessible as long as the browser is open.

Could you provide a specific example of how a website can "query" a web browser? I'd be interested to know exactly what you're referring to. As Shatrat mentioned, it's difficult to imagine how this could be done without JavaScript.

I'm sure we can find a satisfactory solution for you. :-)

---

### Post by cj100570 on 2007-03-02
> **kidders said:**
> Could you provide a specific example of how a website can "query" a web browser? I'd be interested to know exactly what you're referring to. As Shatrat mentioned, it's difficult to imagine how this could be done without JavaScript.

I'm sure we can find a satisfactory solution for you. :-)

I'm sure you're aware that every time you visit a website a cookie is deposited on your pc. As you travel to and fro on the web other sites can and do query your pc for stored cookies. Information in a stored cookie can be a user name, a password, etc. Here's a link to an old review of internet guard dog; [http://reviews.cnet.com/Guard_Dog_3_0_Win9X/4505-3666_7-1587666.html#more]("http://reviews.cnet.com/Guard_Dog_3_0_Win9X/4505-3666_7-1587666.html#more")
As I said in the initial post, I know it happens because back when i was a Windows user I had it on my pc and I have since tested it using a pass through connection on a pc running Ubuntu.

---

### Post by kidders on 2007-03-02
> **cj100570 said:**
> As you travel to and fro on the web other sites can and do query your pc for stored cookies.Any web browser that sets a cookie outside of the remote URI's address space is faulty and should not be used. Ever. Flaws this serious tend to crop up in MSIE more often than not. Cookies per se are, of course, harmless.

---

### Post by cj100570 on 2007-03-02
I know that cookies per se are harmless. My question is aimed more at how to prevent any personal information that may be contained in a cookie from leaving my pc without my explicit permission. People may want to stick their heads in the sand and act as if it doesn't occur in Linux but I've demonstrated that it does. As I said previously, I've been a Linux user for almost 4 years now and never concerned myself with this because I assumed it was a Windows issue.

---

### Post by kidders on 2007-03-02
Ahh. I think I understand. Despite the fact that the only way personal information could find its way off your PC in a cookie is if you permit its storage in the first place, and regardless of the fact that it can only ever be sent to the site that created it, you would *still* like to be able to block it ... even though browsers make no attempt to hide what's being tracked.

I've never heard of a reason for wanting to do this, but you still can, if you really want to. I would use Squid, personally. It's HTTP header handling is very flexible, and you could handle the cookie interception for an entire network from one place.

I imagine though, that trying to prevent the legitimate retransmission of legitimately stored information like this is likely to spend far more time impairing the normal function of reputable websites than protecting you from malicious activity.

**Edit:**
> My question is aimed more at how to prevent any personal information that may be contained in a cookie from leaving my pc without my explicit permission.The trouble with granting permission to retransmit cookies on a case-by-case basis is that, to comply with the HTTP specifications, cookies often need to be sent several times per page impression. Approving and re-approving cookie transmission could get ... well ... tedious! (Squid-based solutions would not give you the opportunity to approve or reject individual transmissions.)

---

### Post by cj100570 on 2007-03-02
You sort of get what I'm saying. If you ever have access to a Windows machine running internet guard dog you'll see that the requests not only come from the site that created the cookie but from other sites also. When I was running it it didn't hinder my web usage at all. As a matter of fact it was totally transparent. The only time it made itself visible was when information that I wanted blocked was requested by a site. I'll look into using squid to customize something. Thanks for the feedback.

---

### Post by kidders on 2007-03-02
> **cj100570 said:**
> If you ever have access to a Windows machine running internet guard dog you'll see that the requests not only come from the site that created the cookie but from other sites also.Hmm... Are you sure you're thinking of cookies? HTTP provides no mechanism for a website to *request* the contents of a cookie.

---

### Post by cj100570 on 2007-03-02
> **kidders said:**
> Hmm... Are you sure you're thinking of cookies? HTTP provides no mechanism for a website to *request* the contents of a cookie.

Taken directly from The Unofficial Cookie FAQ; "

1.3 Why do sites use Cookies?

There are many reasons a given site would wish to use cookies. These range from the ability to personalize information (like on My Yahoo or Excite), or to help with on-line sales/services (like on Amazon Books or eBay), or simply for the purposes of collecting demographic information (like DoubleClick). Cookies also provide programmers with a quick and convenient means of keeping site content fresh and relevant to the user's interests. The newest servers use cookies to help with back-end interaction as well, which can improve the utility of a site by being able to securely store any personal data that the user has shared with a site (to help with quick logins on your favorite sites, for example).

You can view more here [http://www.cookiecentral.com/faq/]("http://www.cookiecentral.com/faq/")

Cookies can be persistent across multiple sites and thus expose your information in places you never intended. Wikipedia also has some useful info here [http://en.wikipedia.org/wiki/HTTP_cookie]("http://en.wikipedia.org/wiki/HTTP_cookie")

---

### Post by kidders on 2007-03-02
Thanks for the references. Unfortunately, I have far too much HTTP experience to find them terribly useful. :( (Unfortunate, because it's not the most exciting of protocols!) Other forum users may find these handy though.

---

### Post by cj100570 on 2007-03-02
> **kidders said:**
> Thanks for the references. Unfortunately, I have far too much HTTP experience to find them terribly useful. :( (Unfortunate, because it's not the most exciting of protocols!) Other forum users may find these handy though.

Lol. I feel your pain. I was a firearms instructor in a past life and I feel the same way when people wanna show me info on firearms or ammunition. Well, I'm off to get some squid experience. Thanks for the feedback. [img]http://www.techhelpers.net/e4u/comp/comp17.gif[/img]

---

