---
title: "Is there a program like GNOTIFIER for linux ?"
date: 2005-10-12
forum: General Help
---

### Post by kurtkraut on 2005-10-12
Hi,

When I use Windows I'm used to GNOTIFIER, and e-mail notifier (not client) program for GMAIL (gmail.com).

This program plays a sound and pop-up a small Window showing the last unread e-mails, its sender, its subject and its first lines.

Is there a program like this for linux ?

Thanks

---

### Post by aysiu on 2005-10-12
I see a Gmail notifier [in Synaptic](http://img296.imageshack.us/img296/2383/snapshot184hl.png).

Follow these instructions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Then type this in a terminal ```
sudo apt-get update
sudo apt-get install gmail-notify
```

---

### Post by xaverx on 2005-10-12
...or you can use **mail-notification**, support gmail, imap, pop etc. notification.

```
sudo apt-get install mail-notification
```

---

### Post by 23meg on 2005-10-12
if you'll be checking gmail only i'd use the gmail checker. mail-notification still has memory leak problems.

---

### Post by kurtkraut on 2005-10-12
[QUOTE=aysiu]I see a Gmail notifier [in Synaptic](http://img296.imageshack.us/img296/2383/snapshot184hl.png).

Follow these instructions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Then type this in a terminal ```
sudo apt-get update
sudo apt-get install gmail-notify
```[/QUOTE]

Hi,

I did exactly (expanded my sources) as it says but this gmail-notify is not found. I didn't find it in packages.ubuntu.com also.

---

### Post by 23meg on 2005-10-12
i can see it here. it's in the universe repository; make sure you've enabled it.

---

### Post by aysiu on 2005-10-12
[QUOTE=kurtkraut]
I did exactly (expanded my sources) as it says but this gmail-notify is not found. I didn't find it in packages.ubuntu.com also.[/QUOTE] I just did [a package search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gmail&searchon=names&subword=1&version=all&release=all), and you're right--apparently the package exists in only Breezy Universe, not Hoary. kcheckgmail, however, does exist in Hoary, but you're probably using Gnome, right?

---

### Post by kurtkraut on 2005-10-12
[QUOTE=aysiu]I just did [a package search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gmail&searchon=names&subword=1&version=all&release=all), and you're right--apparently the package exists in only Breezy Universe, not Hoary. kcheckgmail, however, does exist in Hoary, but you're probably using Gnome, right?[/QUOTE]

No, I'm using XFCE on an Ubuntu (not Kubuntu). So, what should I do to get this program ?

---

### Post by Mguel on 2005-12-14
I'm just installed gmail-notify and I'm pretty happy with it. Simple, small and straight forward.

I only miss a sound notification since most of the time I'm near the computer, but not looking at it.

gmail-notify hasn't implemented sound support yet (afaik from what I searched), so I wanted to ask if there is another similar app with sound notification? (or a way to make gmail-notify make some kind of noise (any kind would be fine for me ;)

Cheers,
Mguel

---

