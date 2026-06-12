---
title: "Firefox' Peculiar Behavior"
date: 2018-04-26
forum: General Help
---

### Post by Mike_Andrews on 2018-04-26
Searching, just on a whim to find Melania Trump's birth date, Firefox/DuckDuckGo produced a blank page. Looking at the url in the browser bar I noted where the name Canonical was the last word: [https://duckduckgo.com/?q=melania+trump+birth+date+&t=canonical](https://duckduckgo.com/?q=melania+trump+birth+date+&t=canonical). Copy-paste.
No amount of waiting would load a reply; the page remained blank but when I commented-out the word 'Canonical' and entered the word 'info' the page I sought quickly loaded, with this url: [https://duckduckgo.com/?q=melania+trump+birth+date+&t=info&ia=web](https://duckduckgo.com/?q=melania+trump+birth+date+&t=info&ia=web).
Can anyone acquainted with Firefox and html, etc., tell me why this is happening?
In re probable query as to whether I tried Google, I don't use Google as a matter of principle. I began using DuckDuckGo several years ago, with no problems until this.
Does this mean Canonical is somehow able to restrict my search results?
How did Canonical even know I was running a search?
Anybody?

---

### Post by speartip on 2018-04-26
Can't help with your problem, other than tell you that both links loaded instantly for me, indicating it's a problem at your end, not with Canonical.

---

### Post by lisati on 2018-04-26
> **speartip said:**
> Can't help with your problem, other than tell you that both links loaded instantly for me, indicating it's a problem at your end, not with Canonical.

The links opened near instantly for me too. I'd suggest clearing your browser cache to see if that helps.

---

### Post by QIII on 2018-04-26
Which release of Ubuntu are you using?

No, canonical is not restricting your browsing.  No,  Canonical is not tracking your browsing.

If you installed Firefox from the repo, that token may be added automatically by some extra code Canonical added so that websites get tickled for a couple of pennies to go to Canonical.

If it concerns you, uninstall the version in the repo and install directly from Mozilla.  You may have to have another browser installed to use after you have removed the repo version so you can get to Mozilla's download.

As for why the page did not load, it's anybody's guess.  It worked for me on a Windows machine and my cell phone.

---

### Post by Holger_Gehrke on 2018-04-26
I don't think the value "canonical' (lower case 'c') of the parameter t at the end of the URL has anything to do with the company Canonical (upper case 'C'). In IT the word 'canonical' has the general meaning of "the preferred way of doing something". There is such a thing as a canonical URL (content can have more than one URL; the canonical one is the one the server admins prefer people to use to access this content) and I believe (although without a look at the source code of the search engine I can't be sure) that it's some kind of option to prefer showing canonical URLs if known / found.

Holger

---

### Post by QIII on 2018-04-26
According to DuckDuckGo, it is a token to represent Canonical, Ltd., to generate revenue.  Other distros do the same.

Canonical can, and does, modify the code for compatibility in the packaged version in the repo.  Uninstall it (if it doesn't take dependencies with it, so be careful) and install directly from Mozilla's website.

It's doing no harm.  Canonical is generating revenue from someone else but you.

---

