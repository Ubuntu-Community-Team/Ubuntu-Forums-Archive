---
title: "Evince + Firefox = nothing happens"
date: 2007-10-21
forum: General Help
---

### Post by Nonno Bassotto on 2007-10-21
I'm using firefox and evince with mozplugger. I updated to Gutsy and now this combination doesn't work anymore. WheneverI try to open a pdf, ps or dvi file inside the browser, evince  only displays "loading..." forever and does not load the document.

I may mention that Evince without firefox works fine.

The relevant section in /etc/mozpluggerrc reads:
```

application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
	repeat noisy swallow(evince) fill: evince "$file"
	repeat swallow(acroread) fill: acroread7 -openInNewWindow "$file"
	repeat swallow(documentShell) fill: acroread5 -geometry +9000+9000 +useFrontEndProgram "$file"
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	GV()

application/x-dvi:dvi:DVI file
	repeat noisy swallow(evince) fill: evince "$file"
        repeat swallow(kdvi) fill: kdvi "$file"
	repeat swallow(xdvi) fill: xdvi -safer -hush -geometry +9000+9000 "$file"

application/x-postscript:ps:PostScript file
application/postscript:ps:PostScript file
	repeat noisy swallow(evince) fill: evince "$file"
	GV()

```

---

### Post by chrisccoulson on 2007-10-21
I get exactly the same behaviour...

---

### Post by Nonno Bassotto on 2007-10-21
Wow, already on page 12. Better bump it...

---

### Post by pietro_spina on 2007-10-21
I don't know about your mozplugger settings but for me if I use Evince to open say a 9MB file it decides to use about 375MB ram... and man I do not have much to spare...

-p

yeah.. I'm a little off topic, but look, you are back at the top :-)

---

### Post by LanDan on 2007-10-21
i can't open anything either with mozplugger.

think its time to file a bug on launchpad

---

### Post by stewpac on 2007-10-22
For me clicking on pdfs pops up a choice to open in evince or save then crashes firefox. Someone help

---

### Post by Nonno Bassotto on 2007-10-23
I should add that sometimes (rarely) Evince is actually able to open the file, but in a smaller frame than the full firefox window. If I reload to have it rendered at the correct dimension I get the "Loading..." message again

---

### Post by Nonno Bassotto on 2007-10-23
Let me mention that I tried to replace evince with evince-gtk, and also tried to delete both ~/.config/evince and ~/.gnome2/evince, with no results...

---

### Post by songshu on 2007-10-24
EDIT::::::::NEVERMIND DOESN'T WORK AFTER ALL!!!!

please people, i need you guys to verify this so we can file a bug in launchpad

when you edit the file /etc/mozpluggerrc as root and you change

```
application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
        repeat swallow(acroread) fill: acroread7 -openInNewWindow "$file"
        repeat swallow(documentShell) fill: acroread5 -geometry +9000+9000 +useFrontEndProgram "$file"
        repeat noisy swallow(evince) fill: evince  "$file"
        repeat noisy swallow(kpdf) fill: kpdf "$file"
        repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
        GV()
```

INTO

```
application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
        repeat swallow(acroread) fill: acroread7 -openInNewWindow "$file"
        repeat swallow(documentShell) fill: acroread5 -geometry +9000+9000 +useFrontEndProgram "$file"
        repeat noisy swallow(evince) fill: evince -f "$file"
        repeat noisy swallow(kpdf) fill: kpdf "$file"
        repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
        GV()
```

so adding the -f value to evince to open full screen it sudenly does work with me here.

PLEASE let me know if this also works for you

---

### Post by songshu on 2007-10-24
please discard previous post, after changing it it did work all of a sudden but this happened only once ;)

have been searching launchpad for this and it is suggested to install evince instead of evince-gtk.....
this does work for me.

is everybody here with this problem using Xubuntu?

---

### Post by Nonno Bassotto on 2007-10-24
No, I use Ubuntu. I tried to remove ~/.mozilla ~/.config/evince and ~/.gnome2/evince folders, but this had no effect whatsoever. I don't know what to do.

Just to know, is there anyone for which evince + firefox works?

---

### Post by John Jason Jordan on 2007-10-25
I had Evince working fine with Firefox in Feisty amd64. Due to a deteriorating computer, I bought a new computer and installed Gutsy amd64 as a fresh install. I have just about finished installing all the programs that I used to have, including Adobe Reader 8.1. However, I used to keep Evince for Firefox because it was faster than Adobe Reader and didn't have all the clutter. I was about to try to get Evince working with Firefox until I read this thread. Now I don't know what to do. I have Firefox working great with flash, so I don't want to mess it up. I don't have mozplugger installed. If I do, could I use Adobe Reader instead of Evince? Are the problems I read here caused by mozplugger or by Evince?

---

### Post by Nonno Bassotto on 2007-10-25
Well, just try to install mozplugger and tell us the result. I think you need it to embed Adobe Reader too, anyway. I can't use Adobe Reader, because I need Evince to open ps and dvi files too.

By the way, I also tried with Epiphany and I got the same problem.

---

### Post by Nonno Bassotto on 2007-10-25
I deleted again both ~/.config/evince and ~/.gnome2/evince, and now it worked: I can embed evince again. Still I have a little problem: evince opens in a window which take one half of the available space, so I'm left with tiny documents...

---

### Post by Mothinator on 2007-10-26
I can confirm this using ubuntu gutsy.

Deleting ~/.gnome2/evince allows embedded evince to open a PDF in about a quarter of the browser window (framed?). EDIT: Some PDFs open in full browser the first time, some only after reload.

Using the Firefox reload button, the PDF will then open in the full browser window.

---

### Post by Nonno Bassotto on 2007-10-26
I wish it was that easy. For me Evince appears in full size only 1 time out of 20 or less that I reload. Moreover sometimes the "loading..." bug appears again and I have to delete ~/.gnome2/evince again.  :(

---

### Post by Mothinator on 2007-10-26
Nonno, it appears you are correct. I am having the same "Loading..." behavior as before.

Deleting ~/.gnome2/evince does fix the problem but only temporarily.

---

### Post by srturner47 on 2007-10-27
I can confirm this problem.  When I open a PDF file it just says "Loading..."

Has anyone reported this to launchpad yet?

By the way, considering the fact that some websites will ONLY show PDFs embedded into the web page, shouldn't mozplugger be on the default installation of Ubuntu?  (After this problem gets fixed of course.)  I was sure confused when I couldn't view my checks on my online bank anymore using Ubuntu.  (I recently switched from another distro.)  And, the ubuntu firefox plug-in manager didn't know that I had to install mozplugger.  For the average user, this could be a huge bump in the road.

---

### Post by songshu on 2007-10-27
it is on launchpad

in the meanwhile i will just use acroread

---

### Post by silhouette on 2007-10-27
> **songshu said:**
> it is on launchpad
So, er... where is it on Launchpad? I'm having the same problem and I'd like to know if any of the devs have noticed it.

---

### Post by songshu on 2007-10-27
> **silhouette said:**
> So, er... where is it on Launchpad? I'm having the same problem and I'd like to know if any of the devs have noticed it.

search and you will find ;)

---

### Post by silhouette on 2007-10-27
> **songshu said:**
> search and you will find ;)
Yeah, [found it](https://bugs.launchpad.net/ubuntu/+source/mozplugger/+bug/145064).

---

### Post by mchikia on 2007-10-27
For me the pdf shows up if you resize firefox.
This is hardly a fix, but useful in the meantime.

---

### Post by Nonno Bassotto on 2007-10-27
> **mchikia said:**
> For me the pdf shows up if you resize firefox.
This is hardly a fix, but useful in the meantime.

Wow, it works! This is the best temporary solution up to now. :)

---

### Post by dberg on 2007-11-01
I'm having the same problem as everyone else here, has a fix been found yet?

---

