---
title: "Small issue with web pages loading on Ubuntu 20.04.2 LTS"
date: 2021-05-08
forum: General Help
---

### Post by ts1971 on 2021-05-08
Hi,

I am running Ubuntu 20.04.2 LTS and all of the sudden started having problems with some pages on merriam-webster.com.  I'm having the exact same issues across both firefox and chrome so I thought that it was something on their server.  But to my surprise, I tested on firefox on a Windows box and things were fine.  So, I'm not sure how to sort this out.

Consider this page for example -> [https://www.merriam-webster.com/words-at-play/usage-of-all-set-idiom?utm_campaign=newsletter&utm_medium=email&utm_source=wotd&utm_content=peoplearereading-lowerleft#](https://www.merriam-webster.com/words-at-play/usage-of-all-set-idiom?utm_campaign=newsletter&utm_medium=email&utm_source=wotd&utm_content=peoplearereading-lowerleft#)

It has the following two issues:

(1) None of the images load. For example, near the top and to the left of the text 'Wait, is this race about to begin or is it already over?,' there is an image which you can probably see, but all I see is a grey box.
(2) If you scroll down to the bottom of the page, there is a comments section.  They are hidden by default, but there is a '+ show' icon which you click on to display the comments.  When you click on it, it is supposed to (and always has) displayed the comments.  When I click on it now, it instead just scrolls back to the top of the page.

Here is an example of the other kind of page I'm having trouble with -> [https://www.merriam-webster.com/word-of-the-day/sea%20change-2020-03-07?pronunciation&lang=en_us&dir=s&file=seachange&utm_campaign=newsletter&utm_medium=email&utm_source=wotd&utm_content=pron](https://www.merriam-webster.com/word-of-the-day/sea%20change-2020-03-07?pronunciation&lang=en_us&dir=s&file=seachange&utm_campaign=newsletter&utm_medium=email&utm_source=wotd&utm_content=pron)

On this page I also have the issue with images not loading.  More troubling though is that the audio pronunciation isn't working.  When I click on the little speaker icon just to the right of the main heading ('Sea Change', in this case), an audio file with the pronunciation should play, but instead nothing happens.

Again, this has always worked fine and was working fine until this afternoon.  Any ideas what the issue could be here?

Thanks!

---

### Post by ts1971 on 2021-05-08
So, I more or less found the issue.  It turns out that if I disable the 'uBlock Origin' extension in Firefox, things start to work again (in Firefox).  This isn't an extension that I recently installed or updated (at least not intentionally), so that part is still a little bit of a mystery.  Even stranger, is that I don't have that extension installed in Chrome and I still get the wonky behavior.   I even tried disabling all of the add ons in Chrome, but not dice.  I don't particularly care as I don't normally use Chrome on the site, but I'd still like to understand what's happening.

---

### Post by dragonfly41 on 2021-05-08
I experience the same symptom in Chrome with grey objects.  It might be an ad blocker extension but if you select one of the grey objects, right click, inspect the developer tools open and you can read/inspect the error in Console.

---

