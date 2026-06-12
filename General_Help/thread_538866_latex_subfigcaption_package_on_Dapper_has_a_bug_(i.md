---
title: "latex: subfig/caption package on Dapper has a bug (in tetex-extra)"
date: 2007-08-30
forum: General Help
---

### Post by jrb114 on 2007-08-30
Hi,

I've just noticed a strange feature (bug?) in TeX. I'm trying to use the subfig package rather than the subfigure (which is deprecated) for my thesis, and I'm using it with caption. However the caption.sty that ships with tetex-extra in Dapper (found at)

```

/usr/share/texmf-tetex/tex/latex/caption/caption.sty

```

doesn't seem to work, and I get problems building the file. If I remove the subcaptions then the file builds. So, I tried building the latest caption.sty from ctan.org ([http://www.ctan.org/tex-archive/help/Catalogue/entries/caption.html](http://www.ctan.org/tex-archive/help/Catalogue/entries/caption.html)) and replacing the above file with the new file.

```

sudo mv /usr/share/texmf-tetex/tex/latex/caption/caption.sty /usr/share/texmf-tetex/tex/latex/caption/caption.sty.0
sudo cp caption3.sty  /usr/share/texmf-tetex/tex/latex/caption/caption.sty

```

Now the file builds fine. I don't know if this will be helpful to anyone, or not, but it sure was a PITA for me.

From a relevance stance, the old caption package was verion 3.0c, while the new one is version 3.0q. 

Does anybody else know if this has been fixed in Edgy/Feisty/Gutsy? I won't be upgrading while I'm writing up, but it'd be nice to know that they're packaging more up-to-date files in tetex-extra (texlive?).

Cheers,

J

---

### Post by mmmmpower on 2008-03-16
I am struggling with this problem right now, but I'm sure why I have it in the first place.  TeXnicCenter is asking to install caption.sty because it cannot find it.  Usually it resolves packages that need installing, but it couldn't do this one for whatever reason.  So I went and got the .sty myself and stuck it in the directory where it is getting all of the other packages I am using.  I get this message when I compile:

[ATTACH]62823[/ATTACH]

Which doesn't seem to make sense to me because here it is in the same directory as the others:

[ATTACH]62824[/ATTACH]

Any help would be appreciated.

---

### Post by hugmenot on 2008-03-17
Rebuild the filename database. 
This is not the Windows Forum, BTW.

---

### Post by mmmmpower on 2008-03-17
Rebuild the database... alright I'll see if I can get this fixed.

I realize that this isn't the windows forum, but following a google search this topic best described the problem I was having.

---

### Post by mmmmpower on 2008-03-17
All straightened out.  Thanks for the quick response. :)

---

