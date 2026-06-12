---
title: "using fontconfig to deprioritize font or remove from matched fonts"
date: 2014-07-11
forum: General Help
---

### Post by l_99 on 2014-07-11
I installed the kanjistrokesorder font on my system to use with software called Anki but now it is used as the default kanji font in Chrome. I want to stop this font being used in Chrome (or everything but Anki). I noticed that if i do a [FONT=Courier New]fc-match -a Helvetica[/FONT], kanjistrokesorder is the first font with kanji to be matched. Can i change the priority of this font to below other fonts with kanji or remove it from matches completely but still let the Anki application use it?

I thought something like this in my local [FONT=Courier New]fonts.conf [/FONT]might work.
 ```
 <match target="pattern">
    <test qual="any" name="family" compare="eq">
      <string>Helvetica</string>
    </test>
    <test qual="any" name="family" compare="eq">
      <string>KanjiStrokeOrders</string>
    </test>
    <edit name="family" mode="assign_replace">
      <string>KanjiStrokes</string>
    </edit>
  </match>
```

---

