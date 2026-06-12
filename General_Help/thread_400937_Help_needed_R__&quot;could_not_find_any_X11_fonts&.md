---
title: "Help needed: R:  &quot;could not find any X11 fonts&quot;"
date: 2007-04-04
forum: General Help
---

### Post by fsando on 2007-04-04
Help is badly needed. 

I'm using R on ubuntu 6.10
I'm making some plotting functions and am now having problems  
- the function in question is 'title()'. This function prints titles (ie text) to a plot.
I get this error:```
Error in title(...) : could not find any X11 fonts
Check that the Font Path is correct.
```
It prevents me from adding titles, annotations etc. to my plots effectively rendering plotting unusable under Linux - and I need it badly.

I 'googled' and found here 
[http://tolstoy.newcastle.edu.au/R/e2/help/07/02/10712.html]("http://tolstoy.newcastle.edu.au/R/e2/help/07/02/10712.html")
A suggestion to change font paths in xorg.conf:
```
Section "Files"

        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/TTF"
        FontPath        "/usr/share/fonts/X11/OTF"
        FontPath        "/usr/share/fonts/X11/CID"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

EndSection
```
I changed my xorg.conf so it now looks like this - it didn't help, though.
```
Section "Files"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

        FontPath        "/usr/share/fonts/truetype"
        FontPath        "/usr/share/fonts/type1"

# old
	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```
Thanks in advance

EDIT:
I've also posted this question [here]("http://ubuntuforums.org/showthread.php?t=401874")

---

### Post by bertalan on 2007-04-10
Hi fsando,

I am having the same problem... Did you resolve the problem ?

Many thanks.

Marcelo

---

### Post by fsando on 2007-04-21
> **bertalan said:**
> Hi fsando,

I am having the same problem... Did you resolve the problem ?

Many thanks.

Marcelo

Hi bertalan
So you are using R aswell :). What are you doing with it? And sorry for not seing your post earlier.

Yes I solved it 'sort of': I upgraded to Feisty (so essentially I didn't solve the root problem, only my own) - I also posted on the r-help list. I didn't fully understand the answers I got, though. But it appears that fonts are far more complicated than fonts in Windows let one believe.
So I am going to investigate this in more detail. I now have problems with fonts in graphs not being antialias'ed - and I also want to control which fonts are used in graphs - but don't know yet how to do that.

Now in Feisty R works but my scanner doesn't (but R is more important to me than the scanner)

---

