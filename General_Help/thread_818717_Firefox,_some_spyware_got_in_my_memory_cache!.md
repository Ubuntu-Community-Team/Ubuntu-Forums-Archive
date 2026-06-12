---
title: "Firefox, some spyware got in my memory cache!"
date: 2008-06-04
forum: General Help
---

### Post by Elijah on 2008-06-04
Everytime I visit a domain that returns an error instead I get a spam page with a search box and some spam keywords below. 

I had a feeling this spammy thing is meant for windows because it's not working very well when I click on it. 

After checking out the page info I see that's loaded up from my memory cache and the only clue I have is from the description of the page 'Relevancy searcher'

Here is what it looks like: 
[IMG]http://i259.photobucket.com/albums/hh286/pinoguin/pichaycom_1212176916348.png[/IMG]


Does anyone know where this came from? I tried unloading all my addons but it's still bugging me. 

If all else fails I decided to install a fresh copy of firefox but how can I backup all my settings, passwords, etc? I don't want to take that annoying thing with me.

---

### Post by lisati on 2008-06-04
This looks like a "pop-up".

Firefox has an option in both the Windows and Ubuntu versions that might be of help - "Clear private data" - which is found on Firefox's Tools menu.

---

### Post by Elijah on 2008-06-04
What do you mean by a 'pop-up'? this didn't pop-up at all. It happens on nonexisting domains or from server errors.

---

### Post by lisati on 2008-06-04
Another possibility occurred to me after I'd typed in my initial response, which is kinda related to the OP's comments. As you say, it could be something to do with the way your setup copes with non-existent domain names: I've occasionally made typos when putting in the URLs of web sites, and sometimes get sent to a dummy website which is really a parking place until someone actually buys the domain and sets things up with real infomation - anything could come on screen. Beyond that, I'm stuck for suggestions.

Anyone else?

---

### Post by Elijah on 2008-06-04
Hmm... nope, I've thought about it before, but I don't think so. Some of the domains I tested are mine and it reveals the proper error message from a friend's browser. But strangely displays differently on mine with that page. 

It's like my firefox got hijacked or something.

---

### Post by kerry_s on 2008-06-04
some isp's do that to, it's part of there dns service.
example:
say your using opendns, it will reroute you to there search page which will have similar suggestions.

in any case try changing your dns server.
[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by Elijah on 2008-06-04
Thanks for the reply guys, but I don't think it's the ISP. 

My friend's laptop is using the same ISP I'm in. She's using windows & also using firefox.

---

### Post by werries on 2008-06-04
just use the Tools > Clear Private Data. should be able to clear up your cache

---

### Post by Elijah on 2008-06-04
oh shoot, now it's appearing in my konqueror and opera! this must've affected my ubuntu installation instead of firefox.

---

### Post by danwood76 on 2008-06-04
Considering these browsers use different engines and so on I bet its a DNS issue.
A piece of adware wouldnt load only when a domain error occured.

Change your DNS and see if its that.

---

### Post by kerry_s on 2008-06-04
your not running any web programs as root are you?

---

### Post by Elijah on 2008-06-04
> **danwood76 said:**
> Considering these browsers use different engines and so on I bet its a DNS issue.
A piece of adware wouldnt load only when a domain error occured.

Change your DNS and see if its that.


I only know how to change those settings from System > Administration > Network Settings. 

But after clearing those entries out it regenerates after I restart the network. Is there a file anywhere that I need to edit? 

And why is it that my friend wasn't affected?


@kerry_s: No not really, but it's starting to feel like a dns issue after all.

---

### Post by kerry_s on 2008-06-04
i told you try changing your dns, the instructions for ubuntu are here->
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by Elijah on 2008-06-04
Hmmm... I don't get it, I edited my resolv.conf, restarted the network... the entries regenerated again from resolv.conf and yet somehow I do not get that spam page anymore.... :-/

---

### Post by kerry_s on 2008-06-04
> **Elijah said:**
> Hmmm... I don't get it, I edited my resolv.conf, restarted the network... the entries regenerated again from resolv.conf and yet somehow I do not get that spam page anymore.... :-/

so your all good then?
it must have been your isp's dns servers.

make sure you make the change permanent.

i never use my isp's dns, it's slow, sometimes buggy.
i use both level3 and opendns.

my /etc/dhcp3/dhclient.conf:

```
prepend domain-name-servers 127.0.0.1, 4.2.2.1, 4.2.2.2, 4.2.2.3, 4.2.2.4, 4.2.2.5, 4.2.2.6, 208.67.222.222, 208.67.220.220;

```

---

### Post by Elijah on 2008-07-21
GRRR! it came back!

I made the changes from that link and yet my dns still has some added servers in there. Do you think my ISP is forcefully putting up those dns?

---

