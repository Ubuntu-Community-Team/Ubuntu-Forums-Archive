---
title: "tool to obfuscate e-mail links, URL's?"
date: 2005-06-06
forum: General Help
---

### Post by uc50_ic4more on 2005-06-06
Hello -

Is there a small utility for Ubuntu that would create hex-obfuscated links? I have a small app on Windows that does this, and have found numerous web sites that feature php or java applets that do same, but I was hoping there'd be something I could use locally.

Thank you.

---

### Post by Takis on 2005-06-06
I remember seeing a perl command on some forum somewhere that, when run, produces a valid email address. I've been trying to find that damn command for a while now cause it was a really cool thing to do. I think that's what you're looking for, but I can't remember for the life of me how the guy did it.

---

### Post by uc50_ic4more on 2005-06-06
[QUOTE=Takis]I remember seeing a perl command on some forum somewhere that, when run, produces a valid email address. I've been trying to find that damn command for a while now cause it was a really cool thing to do. I think that's what you're looking for, but I can't remember for the life of me how the guy did it.[/QUOTE]

Takis -

Thank you for your reply - I have conducted a forum search for "perl command email", "damn command" and "FRICKIN' WHERE IS THAT THING"  \\:D/ 

No dice yet, but I will keep trying. If I find anything elsewhere I will post my results here, in case anyone is following along.

---

### Post by uc50_ic4more on 2005-06-06
[QUOTE=Takis]I remember seeing a perl command on some forum somewhere that, when run, produces a valid email address. I've been trying to find that damn command for a while now cause it was a really cool thing to do. I think that's what you're looking for, but I can't remember for the life of me how the guy did it.[/QUOTE]

Takis -

Was it this?:

[http://rod.info/bin/software/addrencode](http://rod.info/bin/software/addrencode)

---

### Post by uc50_ic4more on 2005-06-06
Truth be told, now that I hold my breath, squint my eyes and get thinking really, really hard about it, all I am actually after is a ascii (er, plain text) to hex conveter... I could go manually edit all of my mailto: links using a table of characters, but that seems so workin'-harder-than-smarter.

---

### Post by Takis on 2005-06-07
[QUOTE=uc50_ic4more]Takis -

Was it this?:

[http://rod.info/bin/software/addrencode](http://rod.info/bin/software/addrencode)[/QUOTE]
Good try, but no it wasn't. It didn't need any special program to exist on your computer, it was a one-liner that you copied onto your shell and it produced the email. No downloads, compiles, or anything.

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=uc50_ic4more]Truth be told, now that I hold my breath, squint my eyes and get thinking really, really hard about it, all I am actually after is a ascii (er, plain text) to hex conveter... I could go manually edit all of my mailto: links using a table of characters, but that seems so workin'-harder-than-smarter.[/QUOTE]
 You coul try "recode", which can, e.g., convert plain text to HTML entities like this &234;

---

### Post by uc50_ic4more on 2005-06-08
[QUOTE=Alexander Kirillov]You coul try "recode", which can, e.g., convert plain text to HTML entities like this &234;[/QUOTE]

Alexander -

Thank you! I have installed recode, and I am sure it will work out fine.

Of course, if anyone can think of a good GUI app, that'd be handy too!  ;-)

---

### Post by Takis on 2005-06-08
Hmm, it works, I guess, but it's not what I had in mind myself. If you ever see that Perl one-liner somewhere, PM me right away!

---

### Post by Zifnab on 2005-06-08
I think it'd be fun to just make my own in PHP. :)

---

### Post by NickeM on 2005-06-09
encode, email:
perl -pe 's/(.)/"&#" . ord($1) . ";"/ge'

decode, email:
perl -pe 's/&#(\d+);/chr $1/ge'

Try these :)

/Nicklas

---

### Post by Takis on 2005-06-09
That's cool.
Buuuuut ultimately could be picked up because the pattern of the obfuscation still matches the exact pattern of the email. I know I'm being really picky here, but the code I'm thinking of would output total garbage, much like a hashed password, except it was reversible.

---

### Post by uc50_ic4more on 2005-06-10
Is anyone following this thread interested in the Windows program for which I was seeking a replacement? It is a 7.5KB utility called, aptly enough, "Obfuscated e-mail Link Creator" and it is easily runnable through Wine.

---

