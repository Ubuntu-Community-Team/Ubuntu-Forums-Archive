---
title: "LibreOffice 5.0 on Ubuntu 12.04"
date: 2015-08-11
forum: General Help
---

### Post by col48 on 2015-08-11
I have LibreOffice 4.4.5.2 running under 12.04 and accept updates that Synaptic offers (though not upgrading to 14.04)

In the last few days, Synaptic has automatically listed LibreOffice 5.0 among its offerings but excluded it from possible updates, offering a 'partial upgrade' of everything else instead.  It gives a standard-looking list of possible reasons (eg previous failed update), but I can't see anything which I believe applies.

1. Has anyone else encountered this?
2. Is LO 5.0 a real improvement, so that it is worth pursuing?
3. If the answer to 2 is yes, where's the roadblock likely to be?

---

### Post by dino99 on 2015-08-11
Phoronix have made a LO5 review recently; but even U+1 still use 4.4.4rc3

---

### Post by vasa1 on 2015-08-11
> **col48 said:**
> I have LibreOffice **4.4.5.2** running under 12.04 and accept updates that Synaptic offers (though not upgrading to 14.04)
...
Is that via a ppa?

---

### Post by ajgreeny on 2015-08-11
I am running LO 5.0 from the LO PPA on my 14.04 Xubuntu system and it has been very good so far with no problems that I've seen, though I admit my use of it is not very complicated, ie, I use it for letters, invoices, simple accounting spreadsheets and similar activities.  You may use it for much larger and more complicated documents and spreadsheets than I do.

It certainly starts faster than version 4.4.5.2 which I used before the upgrade, and to my eyes is better and more modern looking, though that is not very important to me.

---

### Post by kostkon on 2015-08-11
> **col48 said:**
> 1. Has anyone else encountered this?
Yep, just accept it, it wants to remove 1 libreoffice package, that's way it is offered as a dist-upgrade.
> **col48 said:**
> 3. If the answer to 2 is yes, where's the roadblock likely to be?
When the installation finishes, it may ask you if you want to remove some additional packages (that it believes are not needed anymore), just don't accept it.

---

### Post by col48 on 2015-08-12
Thanks for the responses - much appreciated.

@vasa1
The Launchpad/libreoffice PPA is in my repository list for Synaptic so presumably that's where v4.4 came from and v5.0 is offered from.  In the package list in Synaptic, it recognises that v4.4 is installed and that v5.0 is the latest (but not installed) version.  The adjacent icon is grey with a ! superimposed on it.

@ajgreeny
Thanks for your comments - rather encouraging.  I have a one spreadsheet which sometimes has tens of thousands of formula cells which v3.6 usually could cope with (although slowly enough to make bread when I ask it to do any sorting) and unpredictably breaks v4.4 (albeit 4.4 is much faster).  I've also got a couple with 350000 rows of 30 cells each (no formulae) which I'd like to combine but can't.

@kostkon
Your explanation is helpful.  It would be nice if it gave more details rather than just putting out a generic message.  But better a generic message than no message at all.



Does this mean that if I want to upgrade to v5.0 I have to instruct Synaptic explicitly somehow?  Synaptic is not offering the transition in its regular updates.  (The 'partial upgrade' is only partial because it isn't included).

Sorry to be so cautious - I don't want to lose functionality by messing up what is probably a simple transition if the right steps are taken.

---

