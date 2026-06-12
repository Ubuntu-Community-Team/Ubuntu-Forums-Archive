---
title: "Convert Tool (IMG / NRG / MDF) to ISO"
date: 2008-04-26
forum: General Help
---

### Post by Sniffer on 2008-04-26
Hi,

Finally i'm using ubuntu 100% on my laptop, without any thing to do with M$.

I'm quite happy with 8.04 version and i'm looking something like IAT to convert some image files to iso.

Anything cool with a GUI to do it or a program by terminal??

Thanks for your replys, so far haven't found any to Gnome, for what i have searched IAT is for KDE

---

### Post by Monicker on 2008-04-26
You can still run kde apps under gnome.IAT or Kiso should work fine.

---

### Post by Sniffer on 2008-04-26
Thanks for Kiso tip, excellent piece of work... i think gnome is limited in this kind of application....so far haven't found anything 100% gnome.

Nothing against KDE tough...LOL

---

### Post by kwacka on 2008-07-19
A somewhat belated reply, but hopefully of use to someone.

IMG files - just rename to xxx.img to xxx.iso and should do the job - I haven't found one that doesn't yet. (Don't read anything into the 'xxx') 8)

MDF - command line app. - mdf2iso (its in the universe repository).   ```
mdf2iso source.mdf output.iso
```
if you want bin/cue then ```
mdf2iso --cue --toc source.mdf output.iso
```

NRG - nrg2iso (universe repository again). ```
nrg2iso source.nrg output.iso
```

I suppose you could write a graphical front end but is it worth the effort?

---

### Post by Sniffer on 2008-07-22
> **kwacka said:**
> A somewhat belated reply, but hopefully of use to someone.

IMG files - just rename to xxx.img to xxx.iso and should do the job - I haven't found one that doesn't yet. (Don't read anything into the 'xxx') 8)

MDF - command line app. - mdf2iso (its in the universe repository).   ```
mdf2iso source.mdf output.iso
```
if you want bin/cue then ```
mdf2iso --cue --toc source.mdf output.iso
```

NRG - nrg2iso (universe repository again). ```
nrg2iso source.nrg output.iso
```

I suppose you could write a graphical front end but is it worth the effort?

Thanks, help is always in time my friend :)

Another AWESOME utility is ACETONEISO, try it....just great

---

### Post by Corvair on 2008-12-09
I have some mdf files that I am trying to open. I went according to your instructions and I cannot find the application to convert the file to an ISO file.
Could someone help me on this?

---

### Post by bulletxt on 2008-12-11
> **Corvair said:**
> I have some mdf files that I am trying to open. I went according to your instructions and I cannot find the application to convert the file to an ISO file.
Could someone help me on this?

download AcetoneISO:  [http://www.acetoneteam.org](http://www.acetoneteam.org)

---

### Post by Corvair on 2008-12-11
Great, I have downloaded the packag acetone ISO
I am not a whiz at installing software, now could you guide me as to install it?
Thank you

---

### Post by bulletxt on 2008-12-11
> **Corvair said:**
> Great, I have downloaded the packag acetone ISO
I am not a whiz at installing software, now could you guide me as to install it?
Thank you

did you download the Ubuntu version? If yes just click on it! don't download the sources!

---

### Post by Corvair on 2008-12-12
Great, got it right this time and it works.

Thank you.

---

