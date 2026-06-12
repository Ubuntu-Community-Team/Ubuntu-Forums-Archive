---
title: "How to use custom layout under 14.04 ?"
date: 2014-07-04
forum: General Help
---

### Post by mathieubmddehouck on 2014-07-04
Hi folks,

I have troubles using custom layouts under Lubuntu 14.04.
I know that there are plenty of threads all over this forum and the whole internet dealing with custom layouts, but nothing worked.

I was before on ubuntu 12.10 with a custom french layout, and everything was fine. 
I followed this, and everything worked : [http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

But for some reasons, I switch to Lubuntu 14.04, and then surprise, the languages are handled in a completely different way.

I first install anthy for japanese, then m17n for extending the languages I could use.

But then, when I tried to make a custom layout, I couldn't find out how to.

I change the /usr/share/X11/xkb/  symbols/fr and few characteres seemed to change but not all I changed. 
Then I followed some other threads, changing rules/evdev.lst and evdev.xml ...

Nothing worked, so after a while I found the xmb trick, so went to /var/lib/xbk/ and ... surprise, the file is empty, nothing to delete...

I don't know what to do, and I don't understand how Lubuntu deals with keyboards and so on.

Could someone help me ?

Thanks

Math

---

### Post by sudodus on 2014-07-04
Maybe these tips can help (I'm not sure if the released 14.04 acts exactly like Trusty pre-bets)

***Install a new language***

The end user is given the opportunity to select language, but it will not be installed properly at the installation via the OEM dialogue (at least not Swedish, that I tested). But when the user selects (from the main menu in Lubuntu)

Preferences--Language Support

and installs the relevant language, it will work after the next reboot.

The Trusty pre-beta versions need the keyboard layout to be set separately: 'add language' in Xubuntu and 'select input method' (and select your language) in Lubuntu.

---

### Post by mathieubmddehouck on 2014-07-04
Thanks for the answer, saddly, it does not help much.

I have no difficulties to access languages, that's working ok.

The problem is : when I make my own layout, it does not appear anywhere in the select input method panel, and as /var/lib/xbk/ is empty, I guess Lubuntu as a different way of dealing with layouts than Ubuntu, but I cannot figure out which one.

If someone knew, it would really help me.

---

