---
title: "How Do You Revert Back to Firefox 24.7esr from Firefox 31?"
date: 2014-08-12
forum: General Help
---

### Post by OffelNice on 2014-08-12
Recently I sent my pc in for warranty repair.  They had to wipe the harddrive and start anew.  So I had to reinstall Ubuntu and I was using and LIKED (important keyword there) 12.04.  So I reinstalled it using WUBI.  I have been using Firefox 24esr for a long time now on all my machines.  I HATE HATE HATE Firefox 31 and the interface forcing tabs on top, the inability to properly customize the location and other bars like one used to.  (I like being able to see the backwards, forwards, reload and stop buttons all in the same place)  I am also able to customize my firefox in order to save screen real estate so the argument they changed firefox to look more like Chrome with more screen space is a bad one - since firefox 31 takes up more space than ever.  What I'd do is cram the Location bar onto the menu bar with extention icons surrounding it. I'd then combine the bookmark bar with the navigation buttons bar. This way I'd only have 2 bars showing, being very slim.  With 31 I am stuck with 4 bars and a small screen.  Even changing the about:config settings does nothing to change this. I have no idea why Mozilla is going down the road Internet Explorer did.  This is why I quit using IE in Windows years ago because your inability to properly customize it.  Ok so I have been tinkering around with Ubuntu for a couple years now but I never figured out how to install a package after I downloaded and extracted it.  I have downloaded firefox-24.7.0esr.tar.bz2  and extracted it into an /opt folder.   From there I get stuck.  I was able to purge Firefox 31 but when I tried to move the forefox 24 folder over to the /etc folder, I recieved the error: "Error moving file: Permission denied".  So how do I reinstall Firefox 24.  (Please don't attempt to convince me that 31 is better you'll will be wasting both our time.  I have no idea why they are making software less and less user friendly and less customizable.)  I did do a search on this topic but turned up nothing that seemed to work.  Thanks.

If Ubuntu continues down this road of making the interface less attractive, less customizable and less versatile/more likely to censor some kinds of software I am likely to give up on it too.  This philosophy is likely to turn people away from using Linux, the opposite of the Linux community's desired result.  The Unity bar in 12.04 works fine and so shouldn't be changed.  Also with my recent installation I was unable to properly install cinnamon for my user account.  I installed it but some of the icons are missing labels, like restart and shutdown on the icons that do such respective functions.

---

### Post by Frogs Hair on 2014-08-12
Though I can't recommend using an old browser for security reasons there are .deb packages available. What versions will work on newer Ubuntu releases is unknown to me. Make sure you download the correct 32 or 64 bit version. You might have to lock the package version using the synaptic package manager. [http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/f/firefox-mozilla-build/](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/f/firefox-mozilla-build/)

---

### Post by ibjsb4 on 2014-08-12
Sounds like a bad idea to me too, but ..

[https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)

---

### Post by Karlchen on 2014-08-13
Hello, OffelNice.

Though you explicitly instructed us not to do so I will advise to keep Firefox 31.0. Add ClassicThemeRestorer to it. CTR will allow you to customize Firefox 31.0 in the way you want. 

Kind regards,
Karl

---

### Post by claracc on 2014-08-13
Very bad idea to install an obsolete firefox.

In order to "customize" firefox 31, please read: [https://support.mozilla.org/en-US/kb/how-to-make-new-firefox-look-like-old-firefox](https://support.mozilla.org/en-US/kb/how-to-make-new-firefox-look-like-old-firefox)

---

### Post by OffelNice on 2014-08-13
> **Frogs Hair said:**
> Though I can't recommend using an old browser  for security reasons... What versions  will work on newer Ubuntu releases is unknown to me. Make sure you  download the correct 32 or 64 bit version. ... [http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/f/firefox-mozilla-build/](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/f/firefox-mozilla-build/)

24.7esr was working just fine before I updated Ubuntu.  Firefox is an extended support release, and Ubuntu 12.04 is a long term support release which according to documentation will be good at least until 2017.   I have downloaded the correct version.

If firefox 24 isn't the most secure then why is it being used in two of the most secure configurations there are, TAILS and Tor? One can't assume just because something is newer and debateably prettier then it must be more secure.  For example, 2000 year old Roman Architecture is superior to modern architecture which could last 50 years if we are lucky.

> **claracc said:**
> Very bad idea to install an obsolete firefox.

In order to "customize" firefox 31, please read: [https://support.mozilla.org/en-US/kb/how-to-make-new-firefox-look-like-old-firefox](https://support.mozilla.org/en-US/kb/how-to-make-new-firefox-look-like-old-firefox)

Ok I tried this.  It improved things a little but addressed none of my concerns.  Still can't get the tab bar back where it belongs, below the url bar nor can I do anything with the navigation buttons, they are stuck where someone arbitrarily decided they would be stuck.  (And now I can't double click on the tabbar to open a new tab and spellcheck isn't working - this is getting ridiculous).  Is the word "customize" old-speak now?  Before long people won't  even know how to communicate with one another because they won't be able  to agree on any definitions of any words.   The phrase "user friendly"  seems to be an relic of the ancient Greek language by now simply because  that was the main goal of software in the 80s and 90s.  Now the main  goal is take this crap and deal with it, tough luck if you don't like  it.

It's not obsolete, it's an extended support release and it continues to  update.  Where is the evidence that 31 is more "secure" than 24? In a few months we'll be at 35 and they'll tell us 31 was not  secure. It's never ending and it's getting ridiculous.  Each new release  means less function, more bugs, less user friendly, more MEMORY USAGE, a  slower browser and more annoying.  It is very hard to  believe they are getting more secure.  Why haven't they got it right by  now?  Why didn't they get it right last year, 5 years ago?  Well I'm  happy with what they had 6 months ago, 24.  
-----------------------
So to repeat, I have downloaded firefox-24.7.0esr.tar.bz2  and extracted  it into its own folder.  All the files are there.    From there I get stuck.  I know how to delete  the faulty firefox 31.  I just never figured out how to manually install software in Linux because I could never get a straight answer, so I just tend to give up on it then try to take a crack at it a few months later.  What does an executable file look like in Linux?

How do I install it and get past the "Error moving file: Permission denied"?

---

### Post by vasa1 on 2014-08-13
> **OffelNice said:**
> .
...
So to repeat I have downloaded firefox-24.7.0esr.tar.bz2  and extracted  it into an /opt folder.   From there I get stuck.  I know how to delete  the faulty firefox 31
...
There's nothing wrong with Firefox 31.

---

### Post by QIII on 2014-08-13
"User friendly" = "familiar".  It is as simple as that.  There is no other inherent definitive quantifiable measure.

If you find the GUI changes unacceptable, then your complaint should be directed to Mozilla and not visited on the members of the forums.

Firefox is changed frequently because the security environment changes all the time.  That is a good practice.

A suggestion was made for how to install the older version.  If you have difficulty with that, please keep your questions in that direction and avoid the editorial commentary.

---

### Post by OffelNice on 2014-08-13
> **vasa1 said:**
> There's nothing wrong with Firefox 31.
 I'll list the problems again.  Can't move tab bar back to where it belongs below URL bar. Can't combine buttons and bars on two rows so am losing real estate.  Spell check is not working.  Can't doubleclick on tabbar to open a new tab.  Can't customize navigation buttons and move them to where you want them. - and + toolbar takes up more real estate, can't customize it. Less options and more annoying interface in the rightclick-toolbar-customize interface.  Firefox 31 is less secure or they'd be using it in TAILS and Tor.  This is just from a short cursory examination of Firefox 31. There will be more bugs and annoyances no doubt.

---

### Post by QIII on 2014-08-13
Again:  keep this to a discussion of how to install the older version.

Nobody here can answer for Mozilla's design policies and practices.

---

### Post by OffelNice on 2014-08-13
> **QIII said:**
> "User friendly" = "familiar".  It is as simple as that.  There is no other inherent definitive quantifiable measure.


No "user friendly" does not = familiar.  Is that newspeak too?  Just because there may or may not be any inherently (known to you) definitive quantifiable measures does not mean there are not.  There are many.

A better, more inherent definitive quantifiable measure would be "user friendly" = faster to use. Not just faster operating, but faster and easier to use.  There is also more intuitive.  There is also more customizable.  These would all be measures that fit within "user friendly" that are far more relevant than something as vague and ambiguous as "familiar".

> If you find the GUI changes unacceptable, then your complaint should be  directed to Mozilla and not visited on the members of the forums.  A suggestion was made for how to install the older version.  If you have  difficulty with that, please keep your questions in that direction and  avoid the editorial commentary.

Like I explicitly instructed I did not want to debate any of this.  I simply would like to know how to install an extracted program in Ubuntu, getting it into the etc folder and getting it to work from the unity bar.   My question was very specific.  I did not ask for any suggestions, opinions nor editorial commentary.

---

### Post by OffelNice on 2014-08-13
> **QIII said:**
> Again:  keep this to a discussion of how to install the older version.


Yes thank you.  
Again: I have downloaded firefox-24.7.0esr.tar.bz2  and extracted  it into its  own folder.  All the files are there.    From there I get stuck.  I  know how to delete ("purge") the faulty firefox 31.  I just never figured out how  to manually install software in Linux because I could never get a  straight answer, so I just tend to give up on it then try to take a  crack at it a few months later.  What does an executable file look like  in Linux?

How do I install it and get past the "Error moving file: Permission denied"?

---

### Post by howefield on 2014-08-13
> **OffelNice said:**
> Where is the evidence that 31 is more "secure" than 24? 

[https://www.mozilla.org/security/known-vulnerabilities/firefox.html](https://www.mozilla.org/security/known-vulnerabilities/firefox.html)

Thread closed.

---

