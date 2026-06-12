---
title: "fonts in Eterm"
date: 2005-05-11
forum: General Help
---

### Post by 23meg on 2005-05-11
i haven't managed to get Eterm to recognize truetype fonts and use them. its -f parameter won't accept actual font names; i suspect it requires a complete font name with font family, name, style, size, etc. , but the documentation doesn't state what format this should be in. i've googled for example name strings and found some, but since those fonts don't exist in my system, they haven't worked, and i haven't been able to adopt the format to those on my system. 

so what i'm looking for is exact strings needed for the -f parameter to get, say, bitstream vera sans mono or verdana or andale mono tt fonts working with eterm. any help much appreciated.

---

### Post by lt_kije on 2005-05-11
I'd use ```
xfontsel
``` -- it gives you a menu of choices, and you end up with a font name that (I think) Eterm'll be happy with. I used Eterm almost exclusively for the past year or so, but I'm moving to Aterm due to some weird conflicts between GNU Screen, the systems I maintain and Eterm itself. That said, it's a great term...

HTH,
lt_kije

---

### Post by 23meg on 2005-05-11
thank you, this looks really useful. it produces the kind of font definition i've seen in other examples, but i still haven't got aterm to accept the combinations i've given it.. will report if i have any success.

eterm is one feature short of the perfect terminal for me, and that feature is drag and drop support for filenames in gnome.

---

### Post by lt_kije on 2005-05-11
I did a bit of digging, cause I thought that Eterm should take font names provided by xfontsel. In the default theme.cfg provided by Eterm (/usr/share/Eterm/themes/Eterm/theme.cfg), font definitions look like so:

```
font "-adobe-helvetica-medium-r-normal--10-100-75-75-p-56-iso8859-1"
```

I can reproduce that using xfontsel; could it be that the -f switch doesn't like that format, but theme.cfg does?

lt_kije

---

### Post by 23meg on 2005-05-12
hmm, possible. i'll try that. and for the record, it was the -F switch, not to be confused with -f, which sets font color.

---

### Post by lt_kije on 2005-05-13
I just tried it:
```
Eterm -F "-bitstream-bitstream vera serif-bold-r-normal--17-120-100-100-p-0-iso8859-*"
```

Worked fine for me. Eterm came up with a pretty gross (non-default) font. Without the quotes, it gets frustrated because of the space in the font name.

lt_kije

---

### Post by 23meg on 2005-05-13
ok, that worked for me as well, but it's obviously unusable. why is it that only two sizes are selectable for most fonts in xfontsel? isn't there any possible workaround for Eterm? many other options are very limited too.

---

### Post by tread on 2005-05-13
I don't know, I always felt xfontsel doesn't show all the fonts. Have you tried gtkfontsel?

---

### Post by lt_kije on 2005-05-13
[QUOTE=23meg]ok, that worked for me as well, but it's obviously unusable. why is it that only two sizes are selectable for most fonts in xfontsel? isn't there any possible workaround for Eterm? many other options are very limited too.[/QUOTE]
 Which font are you having trouble with? As far as sizes go, my understanding is that most X fonts are generated at specific, fixed sizes (as is evident in xfontsel). They can be scaled up or down, but you'll get pixelization. Eterm (from anecdotes found in a couple mailing list threads) should support true type; I just can't find how...

lt_kije

---

### Post by 23meg on 2005-05-13
i'm having trouble with bitstream vera sans mono and andale mono. two sizes are available for them: 0 and 17.

---

### Post by 23meg on 2005-05-13
[QUOTE=tread]I don't know, I always felt xfontsel doesn't show all the fonts. Have you tried gtkfontsel?[/QUOTE]

wow, i just installed gtkfontsel and now i've got it working with andale mono! will try with bitstream vera sans mono in a moment. here's the magic string for andale mono (yes, i like small fonts):

```
 F "-monotype-andale mono-medium-r-normal-*-*-75-*-*-m-*-iso8859-*"
```

thanks a million times, tread..

---

### Post by tread on 2005-05-13
you be welkom .. am glad it wokked :)

---

### Post by 23meg on 2005-05-13
here's bitstream vera sans mono:

```
-F "-bitstream-bitstream vera sans mono-medium-r-normal-*-10-*-*-*-m-*-iso8859-1"
```

but one more problem: the 10 pixel bitstream sans mono is displayed bigger than in gnome-terminal, plus edges of letters are very jagged. does Eterm not use font smoothing? 

here's a screenshot: Eterm on the left side, gnome-terminal on the right.

---

### Post by 23meg on 2005-05-13
actually, the way Eterm displays these fonts is the way they appear in gtkfontsel, which is unsmoothed and jagged, as opposed to how truetype fonts look in the usual gnome font selector..

---

### Post by tread on 2005-05-13
I think that may be because gtkfontsel uses gtk 1.3, which is not antialiased .. and Eterm doesn't support antialiasing (afaik). Guess I will be sticking to gnome-terminal :)

---

### Post by 23meg on 2005-05-13
but Eterm's default font looks quite smooth, right? maybe it's kind of native to it, and it can't smooth tt fonts? time to dig into the docs..

---

### Post by vladuz976 on 2005-08-21
anybody know the app that shows the full names of fonts to use when let's say trying to modify a terminal?
it's similar to xfontsel

---

