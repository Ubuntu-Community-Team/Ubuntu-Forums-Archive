---
title: "Zenkaku key not working since upgrade to 13.10"
date: 2013-11-15
forum: General Help
---

### Post by osarusan on 2013-11-15
I'm having issues with language input since upgrading to 13.10. I never had trouble in previous versions of Ubuntu.

I use ibus to switch between Japanese and English inputs. Normally this is done by hitting a special key on a Japanese keyboard called "zenkaku," which is located above tab.

Since upgrading to 13.10, zenkaku no longer works to switch languages.

I have set zenkaku in the keyboard settings as the key to switch to "next language," but hitting the key never changes the language. The keyswitch for previous language (super shift space) works fine, but for some reason zenkaku does not.

I've tried this on 2 different PCs, same result. I have tried in Gnome Shell and Unity, still no change. Is this a bug or am I missing something entirely?

---

### Post by colinssil48 on 2013-12-02
I am having the same problem. Previously it was possible to select the input method from the various options available (e.g. hiragana, katakana, zenkaku, hankaku etc) but now the input methods available via Anthy seem to be locked to either English or Japanese and when Japanese, only Hiragana (which can be converted to Kanji or Katakana from a rather labourious drop down menu). There used to be a language bar that popped up when the IME was set to Japanese. That seems to have vanished since 13.10.

The only way around this I have found is to use the "F" function keys to convert whilst typing. Have a look in the "key binding" section of the Anthy settings for a reference of these functions. F6 through to F10 will convert the inputted text to one of the character types. So for example, you can type "tesuto" and get either "&#12390;&#12377;&#12392;", or "&#12486;&#12473;&#12488;" (just through using the space bar for conversion), or "&#65364;&#65349;&#65363;&#65365;&#65364;&#65359;" by pressing F9 instead of the space bar.

---

