---
title: "annoying problem"
date: 2008-05-17
forum: General Help
---

### Post by carterrocks on 2008-05-17
Firefox keeps randomly closing, its usually when flash is been used, like when I'm on youtube or listening to music on myspace.

I ran firefox from the terminal to see what error messages i get, i got this:

mark@mark-desktop:~$ ** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

[1]+  Segmentation fault      firefox

I'm using the new beta that came with Hardy, when it kept closing I installed 2.o  but the same thing happens.

---

### Post by pytheas22 on 2008-05-17
I had problems like this with Firefox 2 as well; on 3 in Hardy however it's fine.  I would advise you first to try a different flash plugin--there should be three of them available in Hardy.  I use the shockwave one and it works fine; I was using Adobe in Gutsy when I had problems.

If switching to a different flash player doesn't help, a last resort would be to install the Windows build of Firefox using wine.  You shouldn't have problems then.

Also keep in mind that you can search for and watch youtube videos now directly from Totem.

---

### Post by carterrocks on 2008-05-17
> **pytheas22 said:**
> I had problems like this with Firefox 2 as well; on 3 in Hardy however it's fine.  I would advise you first to try a different flash plugin--there should be three of them available in Hardy.  I use the shockwave one and it works fine; I was using Adobe in Gutsy when I had problems.

If switching to a different flash player doesn't help, a last resort would be to install the Windows build of Firefox using wine.  You shouldn't have problems then.

Also keep in mind that you can search for and watch youtube videos now directly from Totem.

Okay this may sound stupid but how do I know which flash player I'm using?

---

### Post by strabes on 2008-05-17
The extreme unstability of flash in hardy is due to pulseaudio. To fix this problem, run the following command in a terminal (Applications > Accessories > Terminal).```
sudo aptitude remove libflashsupport
```Restart firefox and you should be good to go.

---

### Post by pytheas22 on 2008-05-17
> Okay this may sound stupid but how do I know which flash player I'm using?

Sorry, I should have told you how to check before.

In Firefox 3 go to the Tools menu, then Add-ons.  Under Plugins, it should tell you which flash plugin you're using--I think the three options would be Shockwave, Adobe of Gnash.

I'm not sure exactly how to check in Firefox 2, but it should be somewhere under the Tools menu, probably under Extensions if that exists.

I would also try the pulseaudio tip posted above; that might be a better solution than playing with different flash players.

---

### Post by carterrocks on 2008-05-17
> **pytheas22 said:**
> Sorry, I should have told you how to check before.

In Firefox 3 go to the Tools menu, then Add-ons.  Under Plugins, it should tell you which flash plugin you're using--I think the three options would be Shockwave, Adobe of Gnash.

I'm not sure exactly how to check in Firefox 2, but it should be somewhere under the Tools menu, probably under Extensions if that exists.

I would also try the pulseaudio tip posted above; that might be a better solution than playing with different flash players.

Okay i did the pulseaudio thing and its hasn't crashed...yet.  I'll keep ya updated, thanks for the help guys!

---

