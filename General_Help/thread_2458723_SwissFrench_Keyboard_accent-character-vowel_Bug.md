---
title: "Swiss/French Keyboard accent-character-vowel Bug"
date: 2021-03-03
forum: General Help
---

### Post by oliver-gerber on 2021-03-03
Hello Everyone :)

The following has already a forum post on linux mint forums from 2019 where I posted my thoughts on this problem.
What I'm talking about is this wrong behavior: ^o   ´i   `e.... The character signs should be put on top of the vowels, not in front of them.

This should clearly be treated as an operating system bug and is still unsolved for years. EVERYONE who chooses swiss/french keyboard layouts expects that if you press the caret symbol and afterwards o,i, or e for example, the caret symbol gets added on top of those characters, not beside them! It's a simple matter of fact and the operating system should "KNOW" that! Every other behavior here is neither what is expected nor wanted. I mean it's clear that windows' or macs behaviors are correct in this matter and ubuntu's/linux' is wrong. No matter what the caret symbol is used for in the shell, programming, where-ever else.

Best practice:
[LIST]
[*]Press caret and then any vowel and the caret should be put on top of the vowel.
[*]If it's not a vowel following, print out the caret as own symbol.
[*]If the caret symbol is pressed twice, print it out as symbol as well.
[*]This surely is also valid for all other signs that are not being put on top of vowels even though they should. Like: ´i  ^o  `a ~e -> all wrong
[/LIST]

Now: Where do I put the request to fix this behavior as it is clearly unwanted and wrong. Is this an x-system issue, some keyboard driver/application that needs adjusting? Is it a gnome/kde thing? Is it even fixable in one place alone? Who do I tell to get this fixed? 

Thanks a lot for helping out :)
Oli

---

### Post by CelticWarrior on 2021-03-03
In Ubuntu 20.04 there are several "French (Switzerland)" layouts:

- French (Switzerland)
- French (Switzerland, without dead keys)

Plus alternative, Macintosh and Sun variants with or without dead keys.
So, logically, the one without dead keys should behave the way you're complaining about. The one that supposedly work for accentuated characters should be "French (Switzerland)". Is this one you have and doesn't work? Please feel free to try others, just in case.

---

