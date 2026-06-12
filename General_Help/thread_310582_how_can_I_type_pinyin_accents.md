---
title: "how can I type pinyin accents?"
date: 2006-12-01
forum: General Help
---

### Post by precinto on 2006-12-01
Hello.

Does someone know how can I easily type the pinyin accents for the 1st and 3rd intonation? (That is an horizontal trace "-" and a downwards bended one "v").

Since there is a bug that wont let me preview keyboard layouts I don't know how to look for it and I found nothing on the forums.

Thanks.

---

### Post by precinto on 2006-12-02
Second day googling, much better results. Now it's solved.

I've modified my keyboard layout so that now it lets me mark all the tones. 

All the process is very well explained on [this thread]("http://ubuntuforums.org/showthread.php?t=188761") by henriquemaia. I just followed the process described there:

1. edit '/etc/X11/xkb/symbols/xx' [xx is the language code you want to modify, in my case 'es', for Spanish, but you should back it up first]

2. find the apropriate section ['basic' or whatever variation you are using]

```
partial alphanumeric_keys
xkb_symbols "basic" {
```

3. add a line specifying keycode (name of the key) and symbols (result of pressing the key). You can specify four symbols: a) key, b) Shift+key, c)AltGr+key, d)AltGr+Shift+key). A map with the keycodes, as well as a complete list of symbols you can use, can be found in the above mentioned thread.

Example of line:

```
key <BKSL> { [dead_acute, dead_grave, dead_macron, dead_caron] };

```

This makes the key named 'BKSL' produce the following:

key+vowel: ´ áéíóú
shift+key+vowel: ` àèìòù
AltGr+key+vowel: ¯ &#257;&#275;&#299;&#333;&#363;
AltGr+shift+key+vowel: &#711; &#462;&#283;&#464;&#466;&#468;

This way we have the four mandarin tones in a single key. Of course you can distribute them as you think the fit best (it's not that comfortable to press three keys simultaneously to produce a tone mark, so it's better if you use those keys you just never use).

For ü you can use the symbol: 'udiaeresis' and assign it to a key or AltGr key. Or you can use another dead key so that you will be able to type things like äëïöü, and not just ü. For the latter use 'dead_diaeresis'.

Since I haven't found a way of creating new entries in System>Preferences>Keyboard>Layout>Add, you can either change your default layout, or, if you want to keep it separate, edit any other existing symbol file (back it up), delete its content and paste in your modified layout. This way you'll be able to change between layouts with the gnome interface using that layout.

---

