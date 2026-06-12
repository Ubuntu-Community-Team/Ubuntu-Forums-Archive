---
title: "How long until flash is fixed?!"
date: 2008-04-13
forum: General Help
---

### Post by Afkpuz on 2008-04-13
Ok, I'm extremely tired of firefox crashing on flash pages.  I know that some of you have firefox work great without crashing, but I know ALOT of my fellow ubuntuers are having trouble with flash player.  My symptoms are that firefox will crash whenever navigating around sites with lots of flash stuff, like youtube.  I've had this problem in both firefox 2 and firefox 3B.  Firefox just closes.  Sometimes, it locks up and compiz turns it grey.  What can I do about this?!  It's driving me nuts and I feel like this problem has been around as long as I've been using gutsy.  How can I fix this?  Sorry for the anger.

---

### Post by 1/0 on 2008-04-13
Wait for Adobe to get working... It is irritating, I know.

I ditched gnome and went for xfce instead so the computer don't turn grey and freeze anymore. I've also got swiftweasel installed instead of firefox. That helped a lot. Also check what version of flash you are using.

---

### Post by hartleyshc on 2008-04-13
so far my solution has been to uninstall ff3, and go back to firefox2.

edit: this *seemed* to work, but as i went back to some of the flash video sites, it would crash.
it seemed to me that the first video i come across will play fine, but if i browse to another site *and come back* or just load another video, it would crash.

---

### Post by imtheguru on 2008-04-13
My solution has been, NoScript. Let flash items wait to be clicked.
Flashblock is another option.

Cheers.

---

### Post by apo00 on 2008-04-13
> **imtheguru said:**
> My solution has been, NoScript. Let flash items wait to be clicked.

Can you give more details about your solution? How can you do that?

---

### Post by 1/0 on 2008-04-13
> **apo00 said:**
> Can you give more details about your solution? How can you do that?

Its addons for firefox. Just type addons in the url and hit enter and you'll get to the addons page. Just search for Noscript.

---

### Post by SIO_ on 2008-04-13
**1/0**
You gave a bad advice... When you type 'addons' and hit enter, Firefox goes to page, that google finds... This is equal to type it in google and press "I'm Feeling Lucky"

The correct url is [http://addons.mozilla.org](http://addons.mozilla.org)

---

### Post by Istonian on 2008-04-13
> **SIO_ said:**
> **1/0**
You gave a bad advise... When you type 'addons' and hit enter, Firefox goes to page, that google finds... This is equal to type it in google and press "I'm Feeling Lucky"

The correct url is [http://addons.mozilla.org](http://addons.mozilla.org)

It takes me straight to the URL when I type addons in the address bar.

---

### Post by Bendrx on 2008-04-13
Never knew you could type in the address bar, works great. Thanks for the tip. I always went to the tools to get them. Also I've always used Noscript and have never had Firefox crash due to flash items, so it might work as a long term fix for you.Best of luck.

---

### Post by sekinto on 2008-04-13
Firefox used to crash a ton for me, I uninstalled the flash extension I added using Synaptic and added it using Adobe's official installer and now it works MUCH BETTER! : )

---

### Post by 1/0 on 2008-04-21
I searched and found a solution. I added the following to the firefox.

```
export XLIB_SKIP_ARGB_VISUALS=1
```

It seems to help. Anyone else?

---

### Post by galv on 2008-04-21
> **1/0 said:**
> I searched and found a solution. I added the following to the firefox.

```
export XLIB_SKIP_ARGB_VISUALS=1
```

It seems to help. Anyone else?

What does this do?

---

### Post by 1/0 on 2008-04-21
It sends me your bank account details ;-p

Nah, only kidding. It turns off transparency in xorg which could be the cause. I remember that I used that line in Gentoo a while back. Also commenting out composite could help.

---

### Post by 1/0 on 2008-04-22
Firefox just crashed again on youtube, so I guess this is not a solution...

---

