---
title: "No Funny Symbols in Linux?"
date: 2007-08-24
forum: General Help
---

### Post by Noodels on 2007-08-24
Okay, when I had windows there was (amazingly enough) one thing windows could do that linux can't. When I converted to linux I lost the ability to do this. And I am wondering if I can get it back.

When you were in windows it was possible to open notepad, ensure num lock was on and then press a number on the num pad while you held the alt key down, when you released the alt key then an odd symbol would come up. 1 would give you a smiley face, and 2 would give you one of inverted colour, and 3 to 6 would give you hearts, clubs, diamonds and spades symbols from playing cards, eventually if you carried on you got to letters.

In ubuntu, the same code exists, because I've been hampering with basic C programs I've noticed that all the symbols don't come up, only letters, and you can't enter it, you have to make a program generate it in the terminal. The program I use is this :

```
#include <stdio.h>

int main()
{
 int num;
 num = 0;
 while (num <= 255) {
   printf("%d = %c\n", num, num);
   num ++;
 }
 num --;
 printf("Printed up to char %d.\n", num);
 return 0;
}
```

It shows you all of them for linux, except linux doesn't have the symbols.

Is there a way to somehow add the symbols to linux or an explanation as to why linux doesn't have them?

P.S. Explanation may be a bit botched. I'm rather tired.

---

### Post by jamvegan on 2007-08-24
I'm not sure that I understand what you want.  If it's just the ability to enter the sorts of characters you mention into documents, you can do so by opening Applications->Accessories->Character Map, then View->By Unicode Block, then scroll down in the left pane to Miscellaneous Symbols and click on it, then scroll the right pane until you find the symbol you want, double click it, click copy, and then go paste it into your document.  Isn't that easy? ;-)

Yeah, I wish there were some easy way to do this through the keyboard, too (personally, for me, it's being able to easily type ñ or ö with a key combination, like I can on my Mac, that I miss).  I'll be watching this thread to see if someone knows how to enter Unicode characters via the keyboard...

---

### Post by glotz on 2007-08-24
Hold Ctrl+Shift and punch in them majick numbers. From e.g. [http://www.unicode.org/charts/](http://www.unicode.org/charts/)

(Most of the stuff you'll probably want is under latin-1) :D

E.g. Ctrl+Shift+ 0 0 E 7 equals ç
and Ctrl+Shift + 0 0 E 9 equals é

Or, if you by some strange powers know their pervert names, see this list [http://www.adobe.com/devnet/opentype/archives/glyphlist.txt](http://www.adobe.com/devnet/opentype/archives/glyphlist.txt)

---

### Post by mssever on 2007-08-24
The Ctrl+Shift trick doesn't work for me. Maybe because I'm on a laptop without a numeric keypad?

My solution is to use the US English International keyboard layout (available from the keyboard prefs). You use the right Alt key as the modifier key. One gotcha is that in this layout you have to type right alt + ' or " to get those characters. The key by itself is a dead key.

---

### Post by glotz on 2007-08-24
It's a GNOME thing. Works for me both on numpad and the other numbas.

---

### Post by mssever on 2007-08-24
Hmm... I'm running Gnome (the version that comes with Feisty), but no luck.

---

### Post by purplenite on 2007-08-24
There is a "character palette" you can add to a panel. Right click on a panel > Add to panel > utilities > character palette. You can customize the palette with the "funny symbols" you use most often, so they are just one click away.

---

### Post by jamvegan on 2007-08-24
> **mssever said:**
> The Ctrl+Shift trick doesn't work for me. Maybe because I'm on a laptop without a numeric keypad?

My solution is to use the US English International keyboard layout (available from the keyboard prefs). You use the right Alt key as the modifier key. One gotcha is that in this layout you have to type right alt + ' or " to get those characters. The key by itself is a dead key.

Yeah, didn't work for me either, but then I tried putting a "u" before the number and, voilà (v - o - i - l - Ctrl+Shift-u-0-0-e-0), it works!  Hooray!

---

### Post by Noodels on 2007-08-25
Alright, to see what I'm talking about copy and paste the code I gave earlier into a linux C compiler and then a windows C compiler. You should be able to see the difference right away.

---

### Post by Lord Illidan on 2007-08-25
> **jamvegan said:**
> Yeah, didn't work for me either, but then I tried putting a "u" before the number and, voilà (v - o - i - l - Ctrl+Shift-u-0-0-e-0), it works!  Hooray!

Works here too

---

### Post by mssever on 2007-08-25
> **Noodels said:**
> Alright, to see what I'm talking about copy and paste the code I gave earlier into a linux C compiler and then a windows C compiler. You should be able to see the difference right away.

The difference is likely one of character set. Windows and Linux both default to a different character set, which means that the character codes produce different numbers. The solution here is to use Unicode.

---

### Post by dominicd on 2008-02-20
The way I type those characters is by using the compose key. Which is set under System >> Preference >> Keyboard. When you hold your compse key and type ' or " or whatever and then release and type your letter you get it modified like é ë è

Notice that if I set right alt (Alt Gr)  to compose key I'm unable to type the 3rd symbol on certain keys like &#8364; on 5 in my case, it might be the same for you.

---

