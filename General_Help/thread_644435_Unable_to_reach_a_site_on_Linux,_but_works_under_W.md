---
title: "Unable to reach a site on Linux, but works under Windows"
date: 2007-12-18
forum: General Help
---

### Post by PrimoTurbo on 2007-12-18
Such a odd bug/problem I have.

I cannot access this url under Linux using Firefox.
[http://-kol.deviantart.com/](http://-kol.deviantart.com/)

However under Windows it works fine under Firefox, however a while back I had the same problem but it went away.

I am guessing it's the - symbol that wont let me access the url?...But why does it work under Windows and Not under Linux?

Anyone else have a similar problem

---

### Post by x0as on 2007-12-18
[http://kol.deviantart.com](http://kol.deviantart.com) works but [http://-kol.deviantart.com](http://-kol.deviantart.com) doesn't work for me either.

---

### Post by CCNA_student on 2007-12-18
As xOas said, I can get [http://kol.deviantart.com](http://kol.deviantart.com) to work but the other 
address fails. Since one address works, is this really an issue?

     Sin Cere,
   
     CCNA_student

---

### Post by Lostincyberspace on 2007-12-18
The way the programs eliminate extra letters.

---

### Post by jflaker on 2007-12-18
[http://-kol.deviantart.com/](http://-kol.deviantart.com/)

I believe that you can't have a domain starting with a special character......Remove the dash ( - )

---

### Post by PrimoTurbo on 2007-12-18
Thing is that kol and -kol are two different users.

**kol** is some random user.

While **-kol **is the famous KoL from [http://www.studiotwentyeight.net](http://www.studiotwentyeight.net), he has all of his releases on deviantart and he posts all his new stuff on there also.

Notice all of his wallpapers ( [http://www.studiotwentyeight.net/wallpapers.htm](http://www.studiotwentyeight.net/wallpapers.htm) ) or linked to -kol.

For example [http://-kol.deviantart.com/art/It-Was-a-Beautiful-Day-69875465](http://-kol.deviantart.com/art/It-Was-a-Beautiful-Day-69875465)

But I cannot access his work because of this character issue on Linux. Is anyone on Linux able to access the site???

---

### Post by ~LoKe on 2007-12-18
I thought this was on my end only.  =[

---

### Post by Vadi on 2007-12-18
I can't either in firefox or konqueror.

Heh, I guess someone made a mistake somewhere.

---

### Post by PrimoTurbo on 2007-12-18
Yeah I don't know why it doesn't work..

I mean regular dashes should be supported under domains.

You can even have a url like this - [http://xn--s3a.com](http://xn--s3a.com)

---

### Post by stunner on 2007-12-18
That's rather disturbing.  As you would expect, the google cache of -kol's page works, but that's not a great solution.

Both epiphany and lynx choked on the dash as well.  Oddly, the google cache link of -kol provided by epiphany loads just fine, images and all....but copying the address of an (already-loaded) image into the URL bar and hitting enter fails.

There is a bug filed here: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/144431](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/144431)

---

### Post by Mateo on 2007-12-19
doesn't work in elinks or dillo.

---

### Post by init1 on 2007-12-19
Failed in Firefox and in Retawq. Odd.

---

### Post by boast on 2007-12-19
doesn't work in opera either.

tried it on my mac (with firefox) and it worked.

---

### Post by ~LoKe on 2007-12-19
So...all this time linux users have been shut out?  Oouchie.

---

### Post by jinx099 on 2007-12-19
Works fine for me in Fedora 8 :confused:

---

### Post by ~LoKe on 2007-12-19
Can someone with Windows installed ping -kol.deviantart.com and give us the IP?

---

### Post by popch on 2007-12-19
Using firefox 1.5.0.1 under Windows XP I can not reach the server named in the OP. Given the kind of feedback I receive, it appears to be our local DNS service which fails to resolve the name.

A very truncated research into the syntax of URLs yields the sentence:

> each domain label starting and ending with an alphanumeric character
   and possibly also containing "-" characters.

If this really is part of the specification for a valid URL, then the URL in the OP is not valid, and neither browsers nor DNS services are required to resolve it.

---

### Post by renzokuken on 2007-12-19
> **~LoKe said:**
> Can someone with Windows installed ping -kol.deviantart.com and give us the IP?

i get 198.172.81.21

---

### Post by popch on 2007-12-19
I can not ping, but I can nslookup, with following results:

kol.deviantart.com - 198.172.81.21
kol.deviant-art.com - 63.251.92.197
-kol.deviantart.com - invalid option 'kol.deviantart.com'

i.e. the nslookup command will not resolve server names beginning with hyphens.

---

### Post by renzokuken on 2007-12-19
198.172.81.21 is just the ip for [www.deviantart.com](www.deviantart.com) it turns out

---

### Post by Vadi on 2007-12-19
Well, this is a perfect example of why should everyone follow the standards. Then that URL wouldn't exist in the first place.

---

### Post by forrestcupp on 2007-12-19
I guess the only thing you can do is type "-kol.deviantart.com" in google.  It's the first selection that comes up in a search.

---

### Post by bonzodog on 2007-12-19
What we need to do is work on this in reverse. Does it work on Firefox in Windows, if yes, why? What does FF in windows do to the address that makes it work?

---

### Post by popch on 2007-12-19
> **bonzodog said:**
> What we need to do is work on this in reverse. Does it work on Firefox in Windows, if yes, why? What does FF in windows do to the address that makes it work?

It does ***not ***work in FF in Windows in my case. It is ***probably ***nothing to do with the browser and ***probably ***much with the name server. 

I suggest that someone look up the RFC which defines the syntax for URLs. If - as I assume - that URL is invalid, contact the webmaster of the site containing that link and have them correct it.

---

### Post by aaaantoine on 2007-12-19
The deviantart website *should* (but currently doesn't) also list user sites as [http://www.deviantart.com/-kol](http://www.deviantart.com/-kol).

---

### Post by forrestcupp on 2007-12-19
> **popch said:**
> It does ***not ***work in FF in Windows in my case. It is ***probably ***nothing to do with the browser and ***probably ***much with the name server. 

I suggest that someone look up the RFC which defines the syntax for URLs. If - as I assume - that URL is invalid, contact the webmaster of the site containing that link and have them correct it.

strange.  It works in Windows FF for me.

---

### Post by jjalocha on 2007-12-19
I tried understand the same thing in the Firefox Forum some time ago, but got no solid information:
[http://forums.mozillazine.org/viewtopic.php?t=582627](http://forums.mozillazine.org/viewtopic.php?t=582627)

---

### Post by PrimoTurbo on 2007-12-19
I think it's something to do with the glibc version on Ubuntu/Linux vs other OS or versions.

We all get it's a non-standard url, but the question is if there is a way to resolve it under Ubuntu?... I tried tinyurl but it did not work, any other ways to convert it to a functional url?

---

### Post by timcredible on 2007-12-19
.

---

### Post by boast on 2007-12-19
> **popch said:**
> It does ***not ***work in FF in Windows in my case. It is ***probably ***nothing to do with the browser and ***probably ***much with the name server. 
.

when I tried it with my computers, they're both getting the address from my local tinydns server,

it has to do with linux's dns requests. 

:confused:

---

### Post by FuturePilot on 2007-12-19
Well I can't get to it from Ubuntu. I haven't tried Windows yet, however it doesn't even work in IE under Wine.

---

### Post by popch on 2007-12-19
> **boast said:**
> when I tried it with my computers, they're both getting the address from my local tinydns server,

it has to do with linux's dns requests. 

:confused:

Its the DNS server. Some process that URL, some do not. None should process it since it's a malformed (invalid) URL. All should reject it as invalid.

Send the site which links to the defective (invalid) URL a mail and ask that they fix their CMS so that they produce valid URLs only.

---

### Post by stunner on 2007-12-19
> **popch said:**
> Its the DNS server. Some process that URL, some do not. None should process it since it's a malformed (invalid) URL. All should reject it as invalid.

Send the site which links to the defective (invalid) URL a mail and ask that they fix their CMS so that they produce valid URLs only.

Pretty sure that it's at the very least gethostbyname() (check bottom of the first page of this thread for the bug report). That's not to say that some DNS servers aren't choking on it as well (although some aren't, give that there are people able to reach the site).

---

### Post by popch on 2007-12-19
> **stunner said:**
> Pretty sure that it's at the very least gethostbyname() (check bottom of the first page of this thread for the bug report). That's not to say that some DNS server's aren't choking on it as well (although some aren't, give that there are people able to reach the site).

Right you are. It's right there in the bug report. 

Why, then, does this thread go on and on?

---

### Post by jinx099 on 2007-12-19
Also works fine for me in Gutsy/Firefox and Gutsy/Iceweasel  :confused::confused:

---

