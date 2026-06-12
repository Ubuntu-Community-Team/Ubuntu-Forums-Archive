---
title: "Question about Firefox 3.0"
date: 2008-05-21
forum: General Help
---

### Post by thelugnut on 2008-05-21
I had been using Firefox browser for a few years now, and have always been satisfied with it. But today I switched over to Opera.

Is it my imagination or what, but has Firefox bloated out? It doesn't seem to work as it used to. Various functions just don't work at all, and some of the functions are pretty slow to respond.

I am just wondering if anyone else feels this way, or am I alone on the pier.

---

### Post by eeried on 2008-05-21
My short experience with Firefox 3 is satisfactory so far. I like most of the new features or improved features. 

I'm having some trouble with flash and I'm going to start a new thread as I don't want to install the flash app, just the plugin.

---

### Post by Tom--d on 2008-05-21
> **eeried said:**
> My short experience with Firefox 3 is satisfactory so far. I like most of the new features or improved features. 

I'm having some trouble with flash and I'm going to start a new thread as I don't want to install the flash app, just the plugin.


Download the flash plugin from the Adobe website. 

Get the file in there called *.so (thats the flash plugin)

do this:
```
sudo nautilus
```

Drop the flash plugin in /usr/lib/firefox-3.0b/plugins

Restart firefox.. and there you have it! flash :D
This also works with the flash player beta 10.. which is what I've got.

For flash sound support for flash player 9.
Do this:
```
sudo apt-get install libflashsupport
```

---

### Post by eeried on 2008-05-21
Many thanks Tom--d. I never thought to explore /usr/lib as i've been so used to /usr/lib/firefox/plugins -- 

/usr/lib/firefox-3.0b/plugins

I'll paste this to my new thread on Flash then.

To go back to Freifox 3b5 I've just had a freeze: I wanted to install the colorzilla extension from the actual website (not from Add-ons) and Firefox displayed a message and a button "Allow" so I clicked on it, then clicked on the install link, and nothing happened. I checked the preferences, went throughthe same steps, and after a while two popups with the install button popped up. 

So I suppose this is because of my slow dial-up connexion, and I should have waited patiently, instead of confusing Firefox. Well I did a ```
killall firefox
``` (I notice in the top output that it is no longer firefox-bin).

cheers,

---

### Post by domness on 2008-05-21
Hmm, well Firefox has always worked perfectly for me! Maybe a reinstallation? I don't know. But people have had mixed thoughts about it.

---

