---
title: "education resources about languages in Ubuntu/PCs?"
date: 2022-11-18
forum: General Help
---

### Post by anotherChris on 2022-11-18
I want to learn about languages (English, Spanish, Chinese, Indian, etc...) in OSs/computing at a level more basic than "how to".  When I try Googling for education sources on this topic, I get lots of pages about "computer programming languages" or how to pages on installing language packs.  I want to know things like how OSs deal with different keyboard layouts, how Chinese characters are inputed during word processing, etc.  I hope there is some thorough introduction to the subject.  Videos, books, websites all are okay.  What are your recommendations for learning about how Operating Systems deal with languages?

---

### Post by TheFu on 2022-11-18
Unicode - aka utf8.

Before Unicode, we had all sorts of terrible work-arounds.  Not all languages support unicode well, so stick with languages that have a clear method for dealing with unicode for the UI and all user input.

---

### Post by anotherChris on 2022-11-18
I think I found my answer.  The search term "computer localization" brings up lots of information I am looking for rather than using the term "language" to search.

@TheFu - thanks

---

### Post by TheFu on 2022-11-19
> **anotherChris said:**
> I think I found my answer.  The search term "computer localization" brings up lots of information I am looking for rather than using the term "language" to search.

@TheFu - thanks

Ah ... I thought you wanted to create programs that supported as many languages as possible, not just looking for ways to use different languages in a normal desktop.  Localization and setting the language for input has been possible on Unix for decades.  I know my editor has handled it using digraphs for a long time.  <cntl>-k begins the digraph input. Á í ó é ñ ç are quick examples, but lots of other characters can be input too ... fractions ¾, ½, &#8531;, subscripts H&#8322;O, superscripts ³ (cubed), lots and lots of interesting characters.   ß if you are learning German. Greek, Arabic, and Cyrillic characters.   There's nearly an &#8734; number of possible choices.  Ok, there's definitely a limit, but math is covered. &#8747;   &#8748;  

&#8992;
&#8993;
&#9787;
I seldom need other characters, but when I do, the most common are available.  If I needed a completely different character set, then I'd know more about changing the inputs and would likely have a different keyboard.  When I was working in Asia, it was amazing how they typed in their native languages. Each key had 4 symbols and as they typed, a little list of commonly used words would be shown that could be selected.  All I knew how to do was to set the LANG to En_US so I could work. ;)

---

