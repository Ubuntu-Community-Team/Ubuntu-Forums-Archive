---
title: "Japanese input for English speakers"
date: 2024-05-09
forum: General Help
---

### Post by goemonburo on 2024-05-09
I swear I have had this happen every time I upgrade save for one or two versions:  I am an English speaker and want an English environment, but I want to be able to switch into Japanese and type romaji (for example, "ka" becoming "&#12363;" and then kanji options showing in a pulldown list to choose from).  

I have tried umpteen supposed Howtos, tried installing ibus-anthy, ibus-fcitx, fiddled with IME and Keyboards and added "Japanese" and "Japanese-kana" into my Input Method switcher (which shows "JA" when I'm in Japanese and "EN" when I'm in English).  BUT NOTHING HAS WORKED.

I'm on Lubuntu 22.04LTS, which may affect the directions, and is part of (perhaps) why this isn't working.  Instructions are often for Ubuntu and the same preference options aren't there.  But still...they're close.  

I would love to have someone out there who has this working tell me what they did.  I don't know why this is such a chore, either.  It seems like it should be a one click option to add an Input language instead of this myriad of choices, different jigsaw pieces, and so on.  

Again, the goal is to be able to have an English keyboard and yet be able to send email or post comments in Japanese.  

Thank you in advance for any help with this.

---

### Post by dragonfly41 on 2024-05-09
I am not a language expert. But I offer two ideas.
(1) there are translation services such as DeepL.com
(2) Join a discussion group managed by Professor Laurence Anthony (based in Japan)
who offers antconc
and other like language tools .. which run in Ubuntu

[https://groups.google.com/g/antconc/c/XRy7Tbjq9k0?pli=1](https://groups.google.com/g/antconc/c/XRy7Tbjq9k0?pli=1)

[https://www.laurenceanthony.net/software/antconc/](https://www.laurenceanthony.net/software/antconc/)

---

### Post by goemonburo on 2024-05-09
@dragonfly41, thanks, but this is totally not the right direction I'm going for.  Japanese input is a supported thing, it's been possible to shift into it with Cntrl-Enter since my very early Red Hat 6.1 days.  It's just somehow unbelievably challenging to get working, yet...also simple.  It's about 3 steps:  Get the input method, get the language modules loaded, and make sure they link up.  But despite months of fiddling I'm still coming up short in this.  

Translation is a horror show, still, in non-Western languages and doesn't remotely answer the question to the point that I'm wondering if this is a spam reply.  I speak Japanese, so the "translation" part isn't the issue.  It's just the physical input of a "k" and an "a" becoming "&#12363;" as I said above, and so on.  I want to write Japanese, not English.  It shouldn't be this hard.

---

### Post by Rubi1200 on 2024-05-09
> I'm wondering if this is a spam reply
**dragonfly41 **is a well-respected member of the forums who has spent many years helping users.

Perhaps we misunderstood what you want to do, I know I had to read your post a couple of times and I am still not sure how you want to achieve the goal.

Have you tried installing the package ibus-mozc? Would this help with what you want?

---

### Post by dragonfly41 on 2024-05-10
Apology for the "translation" red herring (but not for citing Professor's work in Japan on antconc).

Sometimes I tend to "shoot from the hip" with ideas.

Studying expanded context, perhaps this link below helps. Related to ibus-mozc suggestion above.
I note that you write that it has worked but upgrades throw a spanner in the works. This is a common affliction with other settings unrelated to languages. Bleeding edge.

But as I wrote I learn as I write.

[https://help.ubuntu.com/community/JapaneseInput](https://help.ubuntu.com/community/JapaneseInput)

---

### Post by goemonburo on 2024-05-10
@dragonfly41, thank you for the additional help and I'm sorry, it probably sounded harsh, I didn't mean to be...and "from the hip" is fine, just somehow with the links, I guess I took it the wrong way.  Anyway, I appreciate the help and the Japanese Input link, here's where it gets tricky because I'm using Lubuntu, not Ubuntu.  So this is where I started and it hasn't worked.  But I think it's PROBABLY something small that I'm doing wrong.  Thank you for trying, even if the "translation" issue wasn't where I needed to go.

But the issue of foreign language input shouldn't be hard to understand:  With many languages the characters are not a Latin alphabet.  Cyrillic, Korean, Thai, Japanese, Chinese, etc., all use non-Latin characters and the latter two are pictorial, non-alphabetic.  So one needs to use an "input method" that allows you to type in something using latin characters, but have it render in the correct foreign language.  It's not an issue of translation, but of input.

To say "Where's the bathroom?" in Japanese, you first translate, which can be done by the user if they know the language.  But to type in &#12362;&#25163;&#27927;&#12356;&#12399;&#12393;&#12371;&#12391;&#12377;&#12363; using a Western keyboard, one would type:  "otearai ha doko desu ka" and the computer will turn that from the western letters first into the alphabetic phonemes, "&#12362;&#12390;&#12354;&#12425;&#12356; &#12399; &#12393;&#12371; &#12391;&#12377; &#12363;" and then, using drop down choices, the user selects a proper pictogram (kanji, in Japanese) if needed.  So "&#12390;&#12354;&#12425;&#12356;" becomes "&#25163;&#27927;." 

It's essentially four different parts:
A language selector (are we writing Japanese?  Chinese?  Spanish?)
(for Japanese, Korean, Cyrillic) A Latin-char to phoneme component ("o" to "&#12362;" etc.)
(for Japanese, Chinese) A Phoneme to Pictogram dictionary ("&#12390;&#12354;&#12425;&#12356;" to "&#25163;&#27927;")
And a library that ensures all these Unicode chars exist on the system for the target language.

There's OFTEN the assumption in documentation that someone is Japanese and wants the entire system to switch from English to Japanese, so that all the docs, all the currency prefs, etc., are in Japanese.  Here, that's not the case.  I want to keep English as my environment but be able to hit "Cntl-Space" and switch into Japanese.

To answer the "ibus-mozc" question, no, I didn't install it because I was using "ibus-anthy" and I think (again, just think, not sure!) that they conflict.  But I could be wrong about that.

---

### Post by goemonburo on 2024-05-10
So here's the problem with this Howto linked to above:
In the "Region & Language" window, click the plus sign (+) below "Input Sources" [COLOR="#FF0000"] **There is no "Region & Language" window in Lubuntu 22.04LTS.**  And thus, things stop here.[/COLOR]
In the "Add an Input Source" window, select "Japanese",then "Japanese (Mozc)", and then "Add".
Select Japanese (Mozc) from the drop-down language input menu in the upper-right corner.
Click "Input Mode" and select "Hiragana."
After typing desired word, press space bar to select desired kana, kanji, or romaaji then press Enter. (Alternatively, use the function keys to convert entered word: hiragana F6, katakana F7, hankaku-katakana F8, zenkaku-romaaji F9, hankaku-romaaji F10.)

---

### Post by dragonfly41 on 2024-05-10
Often OP's write and omit important context clues.
I admit I have zero knowledge of Japanese. But that doesn't dampen my curiosity.
We now learn "I'm using Lubuntu, not Ubuntu".
Now thinking out of the usual box if I were approaching this I would map my translation through the English keyboard to compile Japanese.
So that keyboard combinations will generate Japanese.
As I see the issue you need some front end translation layer between your translator mind and the English keyboard. Your 4th paragraph defines the requirement in good system engineering terms I think I can understand.
I remember years back responding to an Atom forum discussion on mapping Inuit language. But then I have always taken an interest in pattern recognition.
There is another powerful workflow tool I would suggest. Albert.
[https://albertlauncher.github.io/](https://albertlauncher.github.io/)
Basically Albert looks for key combinations and triggers Python scripts to run any task required.
This site suggests translation using Albert but you make clear that you are studying key mapping.
[https://github.com/dshoreman/albert-translate](https://github.com/dshoreman/albert-translate)
[https://askubuntu.com/questions/1482455/how-can-i-write-japanese-characters](https://askubuntu.com/questions/1482455/how-can-i-write-japanese-characters)
Now this is using just engineering intuition. Define the composing workflow using a toolchain. Tools such as xdotool, Albert, pyautogui, AutoHotKey, Input KeyMapper  come to mind.  Look for key combinations and convert to Japanese (on an English keyboard).
This approach I read was interesting.
[https://codereview.stackexchange.com/questions/268331/python-3-script-to-phonetically-transliterate-written-english-to-cyrillic-and-or](https://codereview.stackexchange.com/questions/268331/python-3-script-to-phonetically-transliterate-written-english-to-cyrillic-and-or)
Just intuition again .. but the principles might apply to other languages such as Japanese.
Perhaps I am down a rabbit hole.

[P.S.] And this link just found makes it appear easy.

[https://moritzmolch.com/blog/2503.html](https://moritzmolch.com/blog/2503.html)

[h=2]Other flavors of Ubuntu (Xubuntu...)[/h]

[COLOR=#34393F][FONT=Helvetica-Neue][/FONT][/COLOR]

---

### Post by bobunderwood99 on 2024-05-10
Does this help?

[https://discourse.lubuntu.me/t/how-to-enable-japanese-input-on-lubuntu-22-04lts/4894](https://discourse.lubuntu.me/t/how-to-enable-japanese-input-on-lubuntu-22-04lts/4894)

---

