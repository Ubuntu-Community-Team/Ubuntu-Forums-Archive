---
title: "Odd Characters in Some Text Files"
date: 2007-06-27
forum: General Help
---

### Post by Jamie Jackson on 2007-06-27
I switched to Ubuntu from Windows recently, and every once in a while, I encounter a file with weird characters in it.

Most recently, I was given a mysql dump file that was created on a Mac. If I open it in gedit, I get little squares with numbers inside. For example, in place of what is presumably an apostrophe, I see a box with 00 92 inside.

[INDENT]...the Earth&#8217;s climate and...[/INDENT]

(UPDATE: Upon posting, the weird box was converted into a curly apostrophe, so you won't be able to see the box I was describing, and will have to rely on my description of it.)

If I cat the file, I get odd numbers in highlighted brackets.

[INDENT]...of **<93>**singularities**<94>** in...[/INDENT]

So, what's going on, and what do I do about it?

Thanks
Jamie

---

### Post by Jamie Jackson on 2007-06-27
FWIW, I was able to import the dump from the command line, despite the oddities.

HOWEVER, I'm still interested in learning what these funny characters are all about, since this isn't the first time I've encountered them.

Thanks,
Jamie

---

### Post by mikeypizano on 2007-06-27
I am also getting these.

---

### Post by AlexThomson_NZ on 2007-06-27
The weird characters are likely to be UTF-8 characters your font does not support.

If gnome (and I assume KDE) can't display the character (ie. it isn't mapped) it displays the UTF-* value of it in a box.

---

### Post by Jamie Jackson on 2007-06-27
Hmm, okay.

Now, out of curiosity, I want to look up what those values mean. I'm not sure if those are hex or dec values.

I found a lookup table [here]("http://www.bebits.com/app/688#download"), and in it, it's got:
```

...
0xe28090	#  U+2010	HYPHEN
0xe28091	#  U+2011	NON-BREAKING HYPHEN
0xe28092	#  U+2012	FIGURE DASH
0xe28093	#  U+2013	EN DASH
0xe28094	#  U+2014	EM DASH
0xe28095	#  U+2015	HORIZONTAL BAR
0xe28096	#  U+2016	DOUBLE VERTICAL LINE
0xe28097	#  U+2017	DOUBLE LOW LINE
0xe28098	#  U+2018	LEFT SINGLE QUOTATION MARK
0xe28099	#  U+2019	RIGHT SINGLE QUOTATION MARK
0xe2809a	#  U+201A	SINGLE LOW-9 QUOTATION MARK
...
0xc290	#  U+0090	<control> DEVICE CONTROL STRING
0xc291	#  U+0091	<control> PRIVATE USE ONE
0xc292	#  U+0092	<control> PRIVATE USE TWO
0xc293	#  U+0093	<control> SET TRANSMIT STATE
0xc294	#  U+0094	<control> CANCEL CHARACTER
0xc295	#  U+0095	<control> MESSAGE WAITING
0xc296	#  U+0096	<control> START OF GUARDED AREA
0xc297	#  U+0097	<control> END OF GUARDED AREA
0xc298	#  U+0098	<control> START OF STRING
0xc299	#  U+0099	<control> 
0xc29a	#  U+009A	<control> SINGLE CHARACTER INTRODUCER
...

```

The 00 90 that I saw was obviously a curly apostrophe (or right single quote). That doesn't seem to jibe with the chart, though. Similarly, I can't make sense of the <93> and <94> in the cat output, either.

Also, gedit uses Monospace by default. Is there a more capable font I should be using instead? Eclipse also shows funny characters in some files, and I'm wondering the same things about that editor, too.

Thanks,
Jamie

---

### Post by AlexThomson_NZ on 2007-06-27
Yeah I noticed that in Character Map too- maybe the file isn't UTF-8 (not too sure how to check), but the hexidecimal value is "00 93", etc. and it can't map a character to it.  Does Mac use it's own variant on the ISO-8859-1 control set part like windows does?

---

### Post by michaelzap on 2007-06-27
I have been trying to figure this out myself since I installed Feisty, and so far I don't have a solution. I have a lot of files on a shared network drive that were created using XP and have accents and other extended characters in them, and I can't get them to show up properly in Ubuntu. Is there a way that I can mount this drive as something other than UTF-8, or is there a way that I can not use UTF-8 as my Ubuntu character encoding?

---

### Post by Jamie Jackson on 2007-06-27
I'm new to encodings...

I wish it were easier to figure out what the file is. I thought I found a way with "enca," but it didn't work:

```

jamie@mercury:~$ enca ~/garbage/bibliography/mgroup2.sql 
enca: Cannot determine (or understand) your language preferences.
Please use `-L language', or `-L none' if your language is not supported
(only a few multibyte encodings can be recognized then).
Run `enca --list languages' to get a list of supported languages.

jamie@mercury:~$ enca --list languages
belarussian: CP1251 IBM866 ISO-8859-5 KOI8-UNI maccyr IBM855
  bulgarian: CP1251 ISO-8859-5 IBM855 maccyr ECMA-113
      czech: ISO-8859-2 CP1250 IBM852 KEYBCS2 macce KOI-8_CS_2 CORK
   estonian: ISO-8859-4 CP1257 IBM775 ISO-8859-13 macce baltic
   croatian: CP1250 ISO-8859-2 IBM852 macce CORK
  hungarian: ISO-8859-2 CP1250 IBM852 macce CORK
 lithuanian: CP1257 ISO-8859-4 IBM775 ISO-8859-13 macce baltic
    latvian: CP1257 ISO-8859-4 IBM775 ISO-8859-13 macce baltic
     polish: ISO-8859-2 CP1250 IBM852 macce ISO-8859-13 ISO-8859-16 baltic CORK
    russian: KOI8-R CP1251 ISO-8859-5 IBM866 maccyr
     slovak: CP1250 ISO-8859-2 IBM852 KEYBCS2 macce KOI-8_CS_2 CORK
    slovene: ISO-8859-2 CP1250 IBM852 macce CORK
  ukrainian: CP1251 IBM855 ISO-8859-5 CP1125 KOI8-U maccyr
    chinese: GBK BIG5 HZ
       none:

jamie@mercury:~$ enca -L none ~/garbage/bibliography/mgroup2.sql 
Unrecognized encoding

```

Does anyone know a way to figure out what kind of file one's dealing with?

---

### Post by speaker219 on 2007-06-27
I assume you are talking about character codes that display in little boxes. (see attached screenshot) this means you haven't installed/don't have the proper fonts to see it. this only happens to me on websites in another language, so it's not really a problem for me

---

### Post by AlexThomson_NZ on 2007-06-28
> **michaelzap said:**
> I have been trying to figure this out myself since I installed Feisty, and so far I don't have a solution. I have a lot of files on a shared network drive that were created using XP and have accents and other extended characters in them, and I can't get them to show up properly in Ubuntu. Is there a way that I can mount this drive as something other than UTF-8, or is there a way that I can not use UTF-8 as my Ubuntu character encoding?

Nah, if doesn't work that way unfortunately...

GTK widgets (ie. text areas, etc.) store the text as UTF-8.  This means that unless the application you are using specifically tries to convert it (and why would it?), it will not be able to display the character if it is not specified in the font.

UTF-8 is a good standard and is not the problem- the problem as I see it is windows and mac programs using \u0091 rather than \u0027 or even \u002B to store an apostrophe.

---

### Post by michaelzap on 2007-06-28
I don't mean characters like the ones that you posted. I mean those black diamonds with question marks in them. See the attached image for an example.

---

### Post by mikeypizano on 2007-06-28
I think I may have seen one of the black diamonds once but there usually the square wih numbers for me.

---

### Post by Jamie Jackson on 2007-06-28
> **AlexThomson_NZ said:**
> Nah, if doesn't work that way unfortunately...

GTK widgets (ie. text areas, etc.) store the text as UTF-8.  This means that unless the application you are using specifically tries to convert it (and why would it?), it will not be able to display the character if it is not specified in the font.

UTF-8 is a good standard and is not the problem- the problem as I see it is windows and mac programs using \u0091 rather than \u0027 or even \u002B to store an apostrophe.

Okay, so this circles back to my question about whether there is some Ubuntu font that has fuller character set support. (Fuller than the default "Sans" font, that is.)

Because... as the only Linux desktop user at my workplace, *I'm* the one who has to make concessions to Win (and very occasionally, Mac) users. Otherwise, I could easily be forced back over to the Dark Side.

So, I'm trying to find ways to interoperate without making waves.

Thanks,
Jamie

---

### Post by SB-X on 2007-08-04
No idea how to help with regards to what font to use, except to find one that explicitely supports the language and charset you're using, possibly the same font that correctly displayed the symbols in windows.

I just wanted to add that I found one way to check the encoding of a file is by opening it in Firefox (drag from Nautilus), using the View->Character Encoding menu, and manually going through the list of encodings until you see the correct symbols in the document, instead the odd characters. This can take a while if you have no idea what the encoding is  even close to.

---

### Post by christian_johansson on 2007-08-19
I have had this same problem, and have found a fix for it. I just change the programs I use (Quanta, the gnome terminal etc) to use iso 8859-1 encoding by default. Then all characters gets displayed correctly on files both from Mac and Windows machines, and vice versa.

I thought utf-8 was used as the default encoding on at least mac machines nowdays, but I guess I was wrong. Or can someone explain to me what's really going on here?

---

### Post by michaelzap on 2007-10-04
It seems as if there ought to be a way to use UTF-8 but still be able to read emails with accents in them, browse SMB shares and see the correct characters, etc., but if there is I haven't been able to figure it out and I haven't seen anyone else explain it either.

---

