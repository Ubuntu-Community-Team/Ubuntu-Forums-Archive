---
title: "Amazon software?"
date: 2018-09-17
forum: General Help
---

### Post by Macamba on 2018-09-17
When I booted my system I saw 'Software Updater' wanted to update my software. In the list of software I saw Amazon mentioned. Generally speaking I do not want big software company's to know what I am doing. Having Amazon software installed is a big invitation to follow my keystrokes or what-ifs. It is possible to [remove (part of) the Amazon package]("https://www.lifewire.com/remove-amazon-application-from-ubuntu-4134329"). When clicking open the Amazon package to be installed I saw the following list:
```

Amazon
Common files for GLib library
Disk encryption support - shared library
GLib library of C routines

```

If I deselect the Amazon part it will not be updated. Traces of the old software still remain. What is the smartest way to continue. Remove it like suggested in the Lifewire link provided?

---

### Post by TheFu on 2018-09-17
You can remove the amazon packages.

---

### Post by 1clue on 2018-09-17
I hate to say it, but when you use the Amazon web site your searches are also tracked. Same goes with absolutely any other big business shopping web site which allows you to search and browse.

It's considered a benefit to the user in that it prioritizes things you have been interested in previously toward the front of the list. 

It's also considered an invasion of privacy by many people.

At any rate, if you're using a web site and the ads surrounding your page relate to things you or your family members have shown an interest in, then that site tracks your activity. Other sites that do this:  Facebook, youtube, google, _EVERY_ big name site for a store front (Walmart, Best Buy, Macy's, ...) and I strongly suspect many news sites as well.

---

### Post by Macamba on 2018-09-19
Thanks for the replies. Generally speaking I'm not fond from everybody tracking what I'm doing on the Internet. Hence my new and improved search engine [Duckduckgo]("https://duckduckgo.com/"). And maybe in the future I would instruct my browser to forget me when I'm done browsing (remove all cookies). I already instructed my browser to "Tell web sites I do not want to be tracked" and "Prevent tracking activities by known sites". I will be removing the Amazon software from my system.

---

### Post by TheFu on 2018-09-19
Asking sites not to track is fine, but I don't think any of them honor that request.
If you see any "Like" buttons or anything else like that from other sites, then you ARE BEING TRACKED.  
The easiest solution that I know is to run pi-hole for your internal DNS on your LAN and that isn't perfect, so some trackers still work.  Most people aren't willing to do what is necessary to avoid most tracking - disable cookies, disable javascript, disable flash and html5 "local objects" and block the 130K or so known tracking/advertising internet domains.  There are probably millions of tracking domains and they change hourly, so blocking them all is impossible.

I don't have a good solution to protect yourself outside your LAN, unless you use a VPN to your home and all traffic uses the pi-hole for DNS everywhere.

An article you might find interesting: [https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)

Any place that you login, will track you. No way around that, unless you block them at the network level always, except when you want to actually use the login.  That's too much hassle for most people.  I do it for the huge tracking of twitter, facebook, G+ ... sites I need to use 1-2 times a year, but no more than that.

---

### Post by 1clue on 2018-09-19
I might also point out that if you have an Amazon account, they store those bits of knowledge on their side. Whether they sell those bits I don't know. But I know that stuff my wife searches for shows up in side bars when I'm on the computer. Stuff related to what she buys shows up more often. Cookies or not, private browser or not.

---

