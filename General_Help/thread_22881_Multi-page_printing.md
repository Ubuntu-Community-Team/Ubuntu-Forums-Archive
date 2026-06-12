---
title: "Multi-page printing"
date: 2005-03-30
forum: General Help
---

### Post by core on 2005-03-30
I'm not sure if this has been posted somewhere around here. I think not.

Using windows i could easily mess around advanced printing options to get my school documents being printed 2 pages at a time. I mean, 2 document pages per face. Yesterday I was to print some documents from mozilla (web docs) and there was no options for it. Also, even/odd page printing was not an option anywhere.

Isn't there some more advanced printing manager I could use in ubuntu? thanks.

---

### Post by Happy on 2005-03-30
Here is what I do.
I print to file
save it as a .ps file
and than use psnup -2up filename.ps filename.ps to make a 2up version of the file

You will need the psutils package for that (I think that's the name)
sudo apt-get install psutils

---

### Post by kagou on 2005-03-30
Under evince
Choose print
Select printer
go to paper
configure the "agencement"( in french) : normal/2 pages in 1/4 pages in 1 ...

---

### Post by istoyanov on 2005-03-30
You may use lpr from the console:
```
lpr -o number-up=2 the_file_to_be_printed.pdf
```

HTH!

---

### Post by WW on 2005-03-30
Take a look at the command **gtklp**,  it might do what you want.

---

### Post by core on 2005-03-30
> Under evince
Choose print
Select printer
go to paper
configure the "agencement"( in french) : normal/2 pages in 1/4 pages in 1 ... 

that option is greyed out here.. something printer-specific maybe. something about the drivers (?)

Happy: your option might work but istoyanov's solution seems more pratical, and it works. Also, firefox remembers the option, so i just edit it once. too bad xpdf doesn't. I know, I can always use command line option :)

Btw, WW, thumbs up for gtklp, very nice. For now command line option is fine, but gtklp is a must have ;)

But.. what does HTH mean, istoyanov? :p

thanks for all the info guys.

---

### Post by core on 2005-04-03
another doubt about printing: how can i switch the order the 2 pages appear? I mean, using lpr command-line options. I can't find anything at the main pages. Probabily because I'm not sure how to use them. All I did was "man lpr" but I found nothing relevant.

Thanks.

---

### Post by bigzak on 2005-04-03
[QUOTE=core]Btw, WW, thumbs up for gtklp, very nice. For now command line option is fine, but gtklp is a must have ;)

But.. what does HTH mean, istoyanov? :p
[/QUOTE]

I have used GTKLP for some time now. It's great, and I think that the only thing missing is a gimp-print style draggable preview on the graphics tab to make sizing easier (I don't want to have to calculate DPI!).

HTH means Hope This Helps, BTW :)

---

### Post by core on 2005-04-03
I googled around a little bit and I found some site about all the options of lpr, and what I wanted was right-to-left layout (no matter top or bottom since i'm getting no more than 2 doc pages for printed page). And I also figured out gtklp to be really useful with all those options. awesome tool.

Still, anyone can tell me if there was any other way to get deep detailed info on every single option of the lpr command? Or, on any other commands? Thanks.

Oh and, thanks for the info bigzak.. not used to forum code yet :p

---

### Post by bigzak on 2005-04-03
[QUOTE=core]Still, anyone can tell me if there was any other way to get deep detailed info on every single option of the lpr command? Or, on any other commands? Thanks.

Oh and, thanks for the info bigzak.. not used to forum code yet :p[/QUOTE]

This is what you want:

[http://cups.org/doc-1.1/sum.html#STANDARD_OPTIONS](http://cups.org/doc-1.1/sum.html#STANDARD_OPTIONS)

You'll want something like:

lpr -o number-up=2 -o number-up-layout=rltb *filename*

that is, 2 sheets per page, going right to left, top to bottom.

---

### Post by Franko30 on 2005-08-26
Hi,

and how do I use GtkLP from with OpenOffice?

Thanks

Franko30

---

