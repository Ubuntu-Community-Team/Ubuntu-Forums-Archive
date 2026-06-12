---
title: "Konqueror won't recognize my wireless broadband connection"
date: 2007-06-07
forum: General Help
---

### Post by Blowfly on 2007-06-07
[COLOR="Red"]This problem was affecting all KDE apps. After searching the KDE forums, I finally found a 3-year-old post that solved the problem. The caches in the individual apps must be disabled:

_Konqueror_
Settings > Configure Konqueror > Cache
Uncheck "Use cache"

_Akgregator_
Settings > Configure Akgregator > General
Uncheck "Use the browser cache"

And so on.

Thanks kuja and PointSource for your input, it's always appreciated.[/COLOR]


Hi y'all,

Kubuntu 7.04
KDE 3.5.6
kppp/Pantech PX-500 wireless

Firefox works fine.
Adept works fine.
Synaptic works fine.

Konqueror displays:

[I]An error occurred while loading [http://www.xyz.com](http://www.xyz.com)
Could not connect to host [http://www.xyz.com](http://www.xyz.com)[/I]

I know I have to configure something, write a script, or both.

I just don't know where to start.

Thanks for any assistance.

---

### Post by PointSource on 2007-06-07
Try checking all the settings for web browsing in konqueror in the settings area/control panel (I can't remember exactly where).

By the way, Xxx.com is a sexually explicit site, you probably don't want to go there in firefox or konqueror or anything.

---

### Post by Blowfly on 2007-06-08
^^^^ lol, I guess my attempt to make something generic achieved the opposite effect. Will edit it lest some innocent click on it and arrive at the gateway to HELL. Thanks.

---

### Post by PointSource on 2007-06-08
Is konqueror able to surf the internet now?

---

### Post by Blowfly on 2007-06-09
No, I don't know why. Must be I don't know how to configure the proxy settings. It should take me only about 6 months to figure it out...:D

I mean, it's just to see if I can get it to work, i.e., why won't it detect the internet connection that's already running. As far as browsers go, why would anyone use it if they have Firefox?

Thanks for the replies though.

---

### Post by Blowfly on 2007-06-19
Bump-ity-bump.

Anyone know what I need to do?

Or should we add "Konqueror won't connect to the Internet" to the list of why newbies say the hell with Linux because the simplest, most mundane things become a baffling & tortuous struggle? :p

But thanks as usual!!

---

### Post by ^master^ on 2007-06-19
I have the same problem as well. Every thing else related to Internet works fine but Konqueror is not. I also get the same error message. 
I am on dialup internet.

---

### Post by kuja on 2007-06-19
blindfolded stab #1: do normal things work fine with cli apps like apt or dig or host?

blindfolded stab #2: does it work after upgrading to kde 3.5.7?

blindfoldes stab #3: do you have problems with the internet in any other apps you can think of?

---

### Post by Blowfly on 2007-06-19
The really inexcusable thing is that the KDE documentation is absolutely worthless.

For example:

"*An error message such as Unknown Host usually means that Konqueror cannot find a connection to the Internet* or that you have entered an incorrect URL."

Well gee! Thanks for that! Might have been more helpful if they would tell *me* how to tell *it* to find the $%#@! connection to the Internet. But no, that wouldn't build character...

---

### Post by Blowfly on 2007-06-19
> **kuja said:**
> blindfolded stab #1: do normal things work fine with cli apps like apt or dig or host?

blindfolded stab #2: does it work after upgrading to kde 3.5.7?

blindfoldes stab #3: do you have problems with the internet in any other apps you can think of?

Everything's fine with Synaptic, Adept, and Firefox.

Will try the 3.5.7 upgrade.

Watch it with that knife, kuja... :)

---

### Post by Blowfly on 2007-06-19
OK, this will make it work (sheesh!!)

Go to KDE Control Center > Internet & Network > Desktop Sharing

In the "Access" tab: "Uninvited Connections" check "Allow uninvited connections."

This was found using absolutely no logic or troubleshooting skills whatsoever, merely potshots in the dark, and is something that should be in the Konqueror documentation.

---

### Post by Blowfly on 2007-06-19
Sorry. I was only able to connect to the KDE site. But even clicking on links within the site gives the error.

This is pathetic. I can't believe that they would release a piece of software like this without explaining how to make it work.

---

### Post by kuja on 2007-06-19
I would assume because developers rarely write the documentation, because if they spent their time writing the documentation they'd have hardly any time for writing the software, and as such you wouldn't really have a piece of software to complain about. 

Now here's the real kicker though, I 've got something for you to check:

blindfolded stab #4: Do other KDE apps have trouble connecting to the net? Things such as akregator (which uses the khtml kpart, just like konqueror)

blindfolded stab #5: Try backing up the ~/.kde/share/apps/konqueror folder and deleting it, also backup the ~/.kde/share/config/konquerorrc file and deleting it too. After this, re-run konqui and see if it wants to work. Don't skip up the backup part or you may find yourself regretting it.

---

### Post by Blowfly on 2007-06-20
No go on the above steps. I'll figure it out eventually and post it when I do. Kuja, until then, thanks for the input.

---

### Post by Blowfly on 2007-06-20
See post #1 for the fix.

---

