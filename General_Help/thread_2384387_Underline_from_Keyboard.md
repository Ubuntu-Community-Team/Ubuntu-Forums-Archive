---
title: "Underline from Keyboard"
date: 2018-02-06
forum: General Help
---

### Post by johano78 on 2018-02-06
I use the international English keyboard layout with dead keys altgr for typing Spanish characters. 

I often want to type and underlined e, a, or some other vowel for a specific reason, but no keyboard layout has an Alt + combination to create and underlined letter/vowel.

I actually tried to edit a copy of the layout file to create a new underline function, but lacking that knowledge of programming, I am unable to do it.

I feel sure that someone who knows a lot about these layouts could do this easily.

---

### Post by linuchsan on 2018-02-07
Ctrl+U

---

### Post by Impavidus on 2018-02-07
u, ú, û, ü are different characters. They have different code points in unicode and for example in german the words Kur and Kür are entirely different words. Underlining however is not a case of orthography, it's typography. The words Kur and K_u_r are the same and unicode has no separate code points for underlined characters (except, maybe, for languages that use a bar below some characters as a diacritical mark, but those should not be reused for normal underlining). Because of this separation between orthography and typography, it wouldn't make sense if some keystroke could directly instruct an application to insert an underlined character. Instead, this is handled by the text editor you use. This forum uses [noparse]__[/noparse] tags, somewhere else you can toggle using ctrl+u, even the terminal has escape codes to underline some characters:```
echo -e "\e[4mhello world\e[0m"
``` The result is not stored as a sequence of underlined characters, but as a sequence of characters encapsulated in some markup code.

---

### Post by johano78 on 2018-02-07
> **linuchsan said:**
> Ctrl+UThat only deletes.> **Impavidus said:**
> u, ú, û, ü are different characters. They have different code points in unicode and for example in german the words Kur and Kür are entirely different words. Underlining however is not a case of orthography, it's typography. The words Kur and K_u_r are the same and unicode has no separate code points for underlined characters (except, maybe, for languages that use a bar below some characters as a diacritical mark, but those should not be reused for normal underlining). Because of this separation between orthography and typography, it wouldn't make sense if some keystroke could directly instruct an application to insert an underlined character. Instead, this is handled by the text editor you use. This forum uses [noparse]__[/noparse] tags, somewhere else you can toggle using ctrl+u, even the terminal has escape codes to underline some characters:```
echo -e "\e[4mhello world\e[0m"
``` The result is not stored as a sequence of underlined characters, but as a sequence of characters encapsulated in some markup code.Yes, a bar underline as a diacritical mark is what I'm looking for.  I didn't want to mention it, because ubuntu doesnt seem too hip to add obscure native american language layouts, but I've been studying Choctaw or Chahta as it's called, an indian language, and the ability to type this diacritical bar quickly would be useful. There are windows and mac keyboards here, but no linux friendly ones. [http://www.languagegeek.com/se/keyboards/se_keyboards.html](http://www.languagegeek.com/se/keyboards/se_keyboards.html)   The bar changes the word meaning. It nasalizes a word like in Chinese, where the nasalized word has an altered meaning.  Thus,  pisa and pisa both are variations of  the verb "seeing".   'pisa' means to examine or study something, to watch something like tv or computer.  'pisa' with the 'i' underlined merely means to see, the plain action word relating to sight of something.

---

### Post by Impavidus on 2018-02-07
If they are diacritical marks, the proper way to enter them (as in, safe during round-trip conversions of the formatting) is either as a precomposed character (preferred) or (if not otherwise possible) using a combining diacritical mark. I can't find an i with a bar underneath in the unicode tables, but it may exist. A combining diacritical mark exists, 0x0331, Combining Macron Below, which you can enter after the character that needs it, if that's the one you need. [Have a look]("https://en.wikipedia.org/wiki/Combining_Diacritical_Marks").

Input of unicode code points in Linux is similar to Windows. Type ctrl+shift+u, type the hexadecimal value of the code point, hit enter of space. Or hold ctrl+shift, type u, hexadecimal code, release ctrl+shift. For example, to type i&#817;, use i ctrl+shift+u 3 3 1 <space>.

I think Windows uses decimal codes, so the codes may be different. My favourite method of entering uncommon characters is using the compose key: <compose> a ' &#8594; á. But I doubt a compose sequence for underlined characters exists. In principle, it should be possible to define them. If you want to try, have a look at [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey). It's a bit old though, so it may not be valid anymore.

Defining new keyboard layouts is possible, so you might be able to use AltGr+some key, but I've never done anything like that and you know how to use a search engine as well as I do.

---

### Post by johano78 on 2018-02-07
Yes, that  0x0331 combining mark looks familiar.  It's used here  [https://www.memrise.com/course/934839/basic-choctaw/](https://www.memrise.com/course/934839/basic-choctaw/) via the mouse. You type the i, e, or a, and click a marker button with 0x0331 on it. Afterwards it changes to the undescored character.   I get tired of mousing that marker button and want a keyboard move which could be faster.

---

### Post by johano78 on 2018-02-07
There is a lot of code in the US keyboard layout.  Ultimately, it seems there are four levels for each key with a possible 5th level.  The first level is direct without a modifier key.  For level 2 you push shift first. Level 3 is altgr. Level 4 is shift + altgr.  The lists run levels in order such as "grave, asciitilde, dead_grave, etc" each being named level-1, level-2, etc..I figured out the alphanumeric system such as . A means alphanumeric. C refers to the row, the spacebar row being A. Row C is therefore the Capslock row. The number refers from left to right not counting capslock the key. So the apostrophe mark is AC11.  I was thinking of killing the minus key on my number pad and reassigning it as a deadkey. Like maybe press it then press a letter and have them combine. It's tougher than it seems. I can't figure it out yet.```
partial alphanumeric_keysxkb_symbols "altgr-intl" {   include "us(intl)"   name[Group1]= "English (international AltGr dead keys)";// five dead keys moved into level3:   key  { [    grave, asciitilde,  dead_grave,   dead_tilde      ] };   key  { [apostrophe,quotedbl,    dead_acute,   dead_diaeresis  ] };// diversions from the MS Intl keyboard:   key  { [        1, exclam,      onesuperior,  exclamdown      ] };   key  { [        r, R,           ediaeresis,   Ediaeresis      ] };   key  { [        j, J,           idiaeresis,   Idiaeresis      ] };   key  { [        x, X,           oe,           OE              ] };   key  { [        v, V,           registered,   registered      ] }; 
```The thing about dead keys appears to be names like dead_acute.  I'm not sure the name for underline of a letter. Might be a unicode number.

---

### Post by again? on 2018-02-07
Don't know anything about compose keys but reading this thread I can make an xdotool(need to install) command to underline characters.
```
xdotool key ctrl+shift+u type 331 && xdotool key Return

```

I set a keyboard shortcut using this as the command to execute
```
sh -c "sleep 0.2 && xdotool key ctrl+shift+u type 331 && xdotool key Return"
```
My keyboard has a calculator key which I assigned, so it's just a single keypress to underline a character.
(*Don't think xdotool works in Wayland)

---

### Post by johano78 on 2018-02-07
> **guber2 said:**
> Don't know anything about compose keys but reading this thread I can make an xdotool(need to install) command to underline characters.```
xdotool key ctrl+shift+u type 331 && xdotool key Return
```I set a keyboard shortcut using this as the command to execute```
sh -c "sleep 0.2 && xdotool key ctrl+shift+u type 331 && xdotool key Return"
```My keyboard has a calculator key which I assigned, so it's just a single keypress to underline a character.(*Don't think xdotool works in Wayland)Awesome! Thanks a lot. It works great! Definitely easier than editing a keyboard layout.   It would be cool if ubuntu team would make an extra set of layboard layouts for native american languages, like an "Indian Pack" you could install extra from the repositories. Xdotool works good enough though.

---

