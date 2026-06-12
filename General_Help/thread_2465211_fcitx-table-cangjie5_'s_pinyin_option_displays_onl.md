---
title: "fcitx-table-cangjie5 's pinyin option displays only simplified characters"
date: 2021-07-25
forum: General Help
---

### Post by YQ002lc2 on 2021-07-25
Does anyone know how to change the cangjie5 pinyin option to display traditional Chinese characters

or how to toggle between simplified and traditional using that tool?

If you're unfamiliar, to use it, you type ` followed by pinyin. Thanks.

---

### Post by monkeybrain20122 on 2021-07-25
In Settings > Language Support you have to add traditional Chinese by checking the box in Install/Remove Language.

---

### Post by YQ002lc2 on 2021-07-26
@monkeybrain20122  I appreciate your reply, but unfortunately this is a different issue.
 
There is no problem displaying or typing traditional Chinese characters on my computer. And, believe it or not, I never installed/removed language support. fonts-hanazono is all you need for displaying almost every Chinese character...

But when I use the pinyin option within fcitx-table-cangjie5 it prefers simplified Chinese characters. 

If you type one syllable and patiently scroll through all the options, you can eventually find the traditional character listed, but if you type more than one syllable, it will only give a simplified result and you might be lucky enough to find the traditional for the first character if you scroll through. 

I'm trying to change this so it defaults to displaying the traditional characters first and maybe the simplified afterwards or so that the &#28450; / &#27721; toggle works to select which one you're querying. 

Thanks again for your reply.

---

### Post by monkeybrain20122 on 2021-07-26
google-pinyin lets you toggle between traditional and simplified Chinese in fcitx. Not sure if that helps

---

### Post by YQ002lc2 on 2021-07-26
Thanks for your reply. 

Yeah, I'm able to toggle traditional/simplified Chinese with the native fcitx pinyin package, but I'm trying to be able to have similar functionality with the fcitx-table-cangjie5 pinyin option that starts with the " ` " character.

For example:
'hanyu 
could yield something like  
1. &#28450;&#35486; etlo yrmmr &#12559;&#12578;&#715; &#12585;&#711;  [optional definition]
2. &#27721;&#35821; ee ivmmr han4 yu3   [optional definition]
3. ...

and selecting 1 should input  &#28450;&#35486;. 

Honestly, I would be happy with just the traditional and simplified characters in the above scenario. 

And maybe there would be an option to toggle whether traditional or simplified appears first in that list. 


There's also a CTRL+ALT+E pinyin lookup option. It would be nice to have zhuyin & jyutping too.

For instance:

1. &#31925;&#35486;  CTRL+ALT+E    would give:

&#31925;&#35486;
&#12585;&#12573;&#715; &#12585;&#711;
yue4 yu3
jyut6 jyu5
Cantonese language

And you could select what phonetic systems you wanted displayed.

---

