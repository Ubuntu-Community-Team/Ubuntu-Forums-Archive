---
title: "firefox imitating ie?"
date: 2008-05-27
forum: General Help
---

### Post by crazyfuturamanoob on 2008-05-27
how do I make firefox imitating internet explorer?
I remember there was an option for that but I cant
remember where it was. please tell me how to do it.
I have to do it because a certain web site wont let
me in if I have firefox. and thats a bank's site.

---

### Post by prince_niceguy on 2008-05-27
As far as I recall the plugin works only in windows as the extension uses windows libraries.

You can check out ies4linux, it will install IE for you in linux and you can use that for browsing those specific sites. 

Also, I will ask the bank site to make it compatible with HTML standards which will ensure it works with firefox.

---

### Post by gug@fnal.gov on 2008-05-27
I found the following trick for changing the agent firefox reports as to a server. Note: it is from 2 years ago...

* Go To -> about:config
* right click on Value and follow to new and then string
* type in -> general.useragent.override
* type in something like Netscape/7.0(X11, en) or whatever

---

### Post by nikogawa on 2008-05-27
You can use the User Agent Switcher Addon
[https://addons.mozilla.org/nl/firefox/addon/59]("https://addons.mozilla.org/nl/firefox/addon/59")

---

### Post by yaknowwat on 2008-05-27
Yeah i use ies4linux and User agent switcher.

At first its kind of tricky to install ies4linux but its actually very easy.

With ies4linux i use IE view to easily pull up a page with IE if needed.
[https://addons.mozilla.org/en-US/firefox/addon/35](https://addons.mozilla.org/en-US/firefox/addon/35)

Though honestly I only ever need to use User Agent Switcher rarely a need for IE View.

---

### Post by crazyfuturamanoob on 2008-05-28
well, the site has a real reason to deny customers
using linux: [COLOR="DarkRed"]_microsoft_[/COLOR]. microsoft pays for them
to not serve linux clients. Of course, this is just
my theory, but why else that site works
on windows, but not on linux? Or perhaps
microsoft made the bank software, and the bank
officers dont even know about the whole thing!

Whoooops, off-topic.:oops:
Anyway it works now, thanks.

---

### Post by sufyan on 2008-05-31
I tried the User Agent Switcher on firefox to use the Outlook web access full version. Now I can log on using the full version but, the links don't work and signing out is an issue. Any idea how I could fix that?

---

### Post by yaknowwat on 2008-05-31
> **sufyan said:**
> I tried the User Agent Switcher on firefox to use the Outlook web access full version. Now I can log on using the full version but, the links don't work and signing out is an issue. Any idea how I could fix that?

a different thread for this might be better but the issue is how the site was designed (which it was designed non-w3c standards compliant). you could possibly create a greasemonkey script to fix the issue's but that can be very complex unless you know javascripting quite well.

---

