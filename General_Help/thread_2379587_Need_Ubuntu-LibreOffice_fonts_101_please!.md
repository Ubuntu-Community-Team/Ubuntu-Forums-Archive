---
title: "Need Ubuntu-LibreOffice fonts 101 please!"
date: 2017-12-07
forum: General Help
---

### Post by 2CV67 on 2017-12-07
Recently (with LibO 5.3?) the fonts available to me in LibO got screwed up.

I now have any number of exotic eastern (farsi, khmer etc) fonts which I will never need & which clutter up the drop-down options.
Can I safely remove these & if so - how?
I suppose by Synapt, I can remove stuff like:
fonts-nanum
fonts-guru-extra
fonts-kacst
fonts-guru
fonts-takao-pgothic
fonts-khmeros-core
fonts-thai-tlwg
fonts-lao
fonts-tlwg-garuda
fonts-tlwg-garuda-ttf
fonts-tlwg-kinnari
fonts-tlwg-kinnari-ttf
fonts-tlwg-laksaman
fonts-tlwg-laksaman-ttf
fonts-tlwg-loma
fonts-tlwg-loma-ttf
fonts-tlwg-mono
fonts-tlwg-mono-ttf
fonts-tlwg-norasi
fonts-tlwg-norasi-ttf
fonts-tlwg-purisa
fonts-tlwg-purisa-ttf
fonts-tlwg-sawasdi
fonts-tlwg-sawasdi-ttf
etc etc etc...
fonts-lohit-guru
fonts-kacst-one
fonts-sil-padauk
fonts-iklug-sinhala
fonts-noto-cjk
fonts-tibetan-machine
fonts-noto-mono
fonts-sil-abassinica...

Can I?
But should that be necessary?
Is there an easier way?

On the other hand & more annoying, lots of my previous fonts (URW Chancery...) are no longer available.
This results in exising documents losing their desired appearance & formating.
How to deal with that?

There seem to be hundreds of font packages available in SynApt, but I don't see how to tell which packages provide which fonts & what those fonts actually look like.
How can I get a preview of fonts so I know which to install?

Thanks for any guidance!

---

### Post by vasa1 on 2017-12-07
What happens if you close LibreOffice completely, rename *~/.config/libreoffice* to something else and restart LibreOffice? Do your fonts reappear?

And, in the past, I've removed most of the fonts you've listed without any apparent harm.

BTW, [Bug 104701 - PS Type 1 URW fonts missing in LibreOffice 5.3.0.0.beta1 and 5.3.0.0.beta2]("https://bugs.documentfoundation.org/show_bug.cgi?id=104701") has the dreaded "RESOLVED WONTFIX".

---

### Post by 2CV67 on 2017-12-07
> **vasa1 said:**
> What happens if you close LibreOffice completely, rename *~/.config/libreoffice* to something else and restart LibreOffice? Do your fonts reappear?

No change.

Yes - I had found the bug report & assumed that was the origin of my lost fonts.

I am still interested in finding out how to fix the situation with least risk & least effort!
EDIT - I also assume other people may be interested...

Thanks for your help!

---

### Post by vasa1 on 2017-12-07
I just checked in 18.04 which has LibreOffice 5.4.3. No URW Chancery in the dropdown even though the *gsfonts* package is installed and the URW Chancery font is available to other applications.

---

### Post by 2CV67 on 2017-12-07
Yes - I am quite out of my depth with these fonts.
It seems that fonts are installed via Ubuntu (SynApt) but not handled by LibO?

So I suppose I need to find fonts which are installable via Ubuntu & accepted by LibO...
But I don't know how.

---

### Post by vasa1 on 2017-12-07
Comment #17 in the bug suggests getting fonts from [http://practicaltypography.com/charter.html](http://practicaltypography.com/charter.html)

Does that help?

---

### Post by 2CV67 on 2017-12-07
Thanks, but I want to stick to content from the repos, not download wildly, Windows-style! :)

---

### Post by vasa1 on 2017-12-07
> **2CV67 said:**
> Thanks, but I want to stick to content from the repos, not download wildly, Windows-style! :)
In that case, I wish you all the best :)

---

