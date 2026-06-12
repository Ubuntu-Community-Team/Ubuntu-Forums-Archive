---
title: "Unable to type or view &#9660;&#9650; in Ubuntu"
date: 2019-06-04
forum: General Help
---

### Post by mrm22 on 2019-06-04
typing u+001F or u+001E just shows an empty space in text editor or browser.
Opera browser shows only empty boxes for fonts.

Tried to change locale and installed new fonts, but still cannot view or type this.

---

### Post by LwIh%*7 on 2019-06-04
What of this?

[https://ubuntuforums.org/showthread.php?t=1921248&page=2](https://ubuntuforums.org/showthread.php?t=1921248&page=2)
[https://askubuntu.com/questions/982443/invisible-fonts-in-opera-12](https://askubuntu.com/questions/982443/invisible-fonts-in-opera-12)

Are these related?

---

### Post by CatKiller on 2019-06-04
You've got your numbers wrong. The numbers you're using are from the control code block; they aren't supposed to display anything.

The numbers you need are U+25B2 for &#9650; and U+25BC for &#9660;, both of which worked perfectly fine here in Firefox.

---

### Post by mrm22 on 2019-06-04
But the same unicode shows like this in windows 7 Opera Browser 
[https://ibb.co/txWnqyd](https://ibb.co/txWnqyd)

But in ubuntu it shows like this
[https://ibb.co/9vRXHWD](https://ibb.co/9vRXHWD)

After installing a font named LastResort it looked like this
[https://ibb.co/VMsxbVx](https://ibb.co/VMsxbVx)

When i copied it to text editor it was like this
[https://ibb.co/rtFcpnQ](https://ibb.co/rtFcpnQ)

I'm just trying to figure out if I made any mistake in the fonts or locales settings.
Sorry for my bad english.

---

### Post by CatKiller on 2019-06-04
> **mrm22 said:**
> I'm just trying to figure out if I made any mistake in the fonts or locales settings.

No, you're definitely using the wrong numbers. You can check [here](https://en.wikipedia.org/wiki/List_of_Unicode_characters) if you like.

---

### Post by Impavidus on 2019-06-05
According to standards like ASCII, Unicode and the Windows-1252 encoding, u+001e and u+001f belong to the C0 control characters. They stand for <record separator> and <unit separator>, respectively. These control characters may have been useful when ASCII was introduced in the 1960s, but were rarely used by computers in the 1980s or '90s.

ASCII is not enough for most languages other than english and lacks various useful symbols other than letters. In order to squeeze more graphical characters in an 8-bit encoding, with room for 256 characters including control characters, many different encodings were designed. These often replaced the less common control characters with graphical characters and added various sets of characters in the 0x80–0xff range, only trying to keep the printing ASCII characters and the most common control characters in place. Every encoding was useful for a number of related languages.

The resulting mess was only cleaned up when in the 1990s Unicode came with multi-byte encodings. This allowed for the first time to encode all languages in a single encoding. It has been widely accepted since the 2000s

On Windows you probably use [alt codes]("https://en.wikipedia.org/wiki/Alt_code") to enter these characters. The alt codes however don't use the numbers assigned to the characters in Unicode, but instead use [CP437]("https://en.wikipedia.org/wiki/Code_page_437"), which is one of those old character sets. Windows then replaces those numbers from CP437 by the numbers for the same characters in Unicode. It's all for compatibility, so that people can type the same alt codes as they did 35 years ago.

Ubuntu doesn't make this translation and just assumes you enter Unicode numbers.

---

