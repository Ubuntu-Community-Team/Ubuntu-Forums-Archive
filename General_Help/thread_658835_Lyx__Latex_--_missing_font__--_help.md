---
title: "Lyx / Latex -- missing font ? -- help"
date: 2008-01-05
forum: General Help
---

### Post by Dunhausen on 2008-01-05
I have installed just about every font package I can think of, and certainly all the lyx/latex packages... no avail.

This is the error in Lyx, in trying to compile something into a pdf:
```
 Font OT1/pcr/m/n/12=pcrr7t at 12.0pt not loadable: Metric (TFM) not found
```

And if I convert it to Latex instead, and try to compile that:
```
kpathsea: Running mktexmf pcrr7t
! I can't find file `pcrr7t'.
<*> ...:=ljfour; mag:=1; nonstopmode; input pcrr7t
                                                  
Please type another input file name
! Emergency stop.
<*> ...:=ljfour; mag:=1; nonstopmode; input pcrr7t
                                                  
Transcript written on mfput.log.
grep: pcrr7t.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input pcrr7t' failed to make pcrr7t.tfm.]
```

I am trying to use the "hollywood.lyx" template which is included with Lyx by default.  

These are the font packages "hollywood.lyx" loads
```
\font_roman default
\font_sans default
\font_typewriter default
\font_default_family default
```

As you can see, they are all standard packages.

Also
```
pimeson@narnia:~$ locate pcrr7
/usr/share/texmf-texlive/fonts/tfm/public/pslatex/pcrr7tn.tfm
/usr/share/texmf-texlive/fonts/vf/public/pslatex/pcrr7tn.vf

```

Isn't that what it's looking for? :(

---

### Post by wobster on 2008-01-20
I just had a similar issue. Installing the package texlive-latex-recommended fixed that.

---

### Post by Dunhausen on 2008-01-25
Unfortunately, having done that, I still seem to get the same error. :(

---

### Post by biodiesel-bri on 2008-03-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/157309](https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/157309) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had the same problem.  Installing latex2html and then doing a Tools -> Reconfigure in Lyx solved the issue for me.

---

### Post by hugmenot on 2008-03-02
> **Dunhausen said:**
> 
Also
```
pimeson@narnia:~$ locate pcrr7
/usr/share/texmf-texlive/fonts/tfm/public/pslatex/pcrr7tn.tfm
/usr/share/texmf-texlive/fonts/vf/public/pslatex/pcrr7tn.vf

```

Isn't that what it's looking for? :(

It's looking for pcrr7t.tfm, which is not listed above. I get this:
```
locate pcrr7
/usr/share/texmf-texlive/fonts/tfm/adobe/courier/pcrr7t.tfm
/usr/share/texmf-texlive/fonts/tfm/public/pslatex/pcrr7tn.tfm
/usr/share/texmf-texlive/fonts/vf/adobe/courier/pcrr7t.vf
/usr/share/texmf-texlive/fonts/vf/public/pslatex/pcrr7tn.vf

```
And then:
```
dlocate -S /usr/share/texmf-texlive/fonts/tfm/adobe/courier/pcrr7t.tfm
texlive-fonts-recommended: /usr/share/texmf-texlive/fonts/tfm/adobe/courier/pcrr7t.tfm
```

Do you have "texlive-fonts-recommended" installed?
nota bene: I'm on Hardy, [but it should be in Gutsy, too]("http://packages.ubuntu.com/search?mode=filename&suite=gutsy&section=all&arch=i386&searchon=contents&keywords=pcrr7t.tfm")

---

