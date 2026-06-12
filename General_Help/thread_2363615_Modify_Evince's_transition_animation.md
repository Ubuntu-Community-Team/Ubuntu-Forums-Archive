---
title: "Modify Evince's transition animation"
date: 2017-06-12
forum: General Help
---

### Post by SnuKies on 2017-06-12
I am using **Evince **as my default PDF viewer because it is very simple and has everything I need.
I only have one problem: the transition between 2 pages in presentation mode is very annoying. I think it is called **Fading in / Fading out**.
Does anybody know how can I change the settings to **NoTransition **?

I found the configure file at: **/usr/share/glib-2.0/schemas/org.gnome.Evince.gschema.xml, **but it has no tag for transitions.
Also, **dconf Editor ** has no tag for transition
And finally, **Evince **has not **Settings **&#8203;options.

---

### Post by ajgreeny on 2017-06-12
Interesting, as using it in Xubuntu 16.04 with Presentation mode, te transitions are instant from one page to the next.

What Ubuntu version and which DE are you using?

---

### Post by vasa1 on 2017-06-12
> **ajgreeny said:**
> Interesting, as using it in Xubuntu 16.04 with Presentation mode, te transitions are instant from one page to the next.

What Ubuntu version and which DE are you using?

Same here using the Openbox session of Lubuntu 16.04. No animations while moving from one page to the next in presentation mode (Evince 3.18.2).

Edit:>     - Fix fade animations in presentation mode (Carlos Garcia Campos)
    - Fix a crash when starting animations in presentation mode
      (Carlos Garcia Campos)
from [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/594967](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/594967) in 2010!

---

### Post by SnuKies on 2017-06-12
Evince's version: evince 3.10.3-0ubuntu10.2
And I am using Ubuntu 14.04 with Gnome shell.

And since I did all my updates last weekend, I it should be up-to-date ?
Maybe if I reinstall it?

---

### Post by vasa1 on 2017-06-12
> **SnuKies said:**
> Evince's version: evince 3.10.3-0ubuntu10.2
And I am using Ubuntu 14.04 with Gnome shell.

And since I did all my updates last weekend, I it should be up-to-date ?
Maybe if I reinstall it?

You can tell if you have the latest version available for 14.04 by running```
apt-cache policy evince
```

---

### Post by SnuKies on 2017-06-12
Here's a short video : [https://youtu.be/QYrKSfvvjcI](https://youtu.be/QYrKSfvvjcI)
@vasa1: it looks like my Evince is up-to-date :  
Installed: 3.10.3-0ubuntu10.2  Candidate: 3.10.3-0ubuntu10.2

---

### Post by vasa1 on 2017-06-12
> **SnuKies said:**
> Here's a short video : [https://youtu.be/QYrKSfvvjcI](https://youtu.be/QYrKSfvvjcI)
@vasa1: it looks like my Evince is up-to-date :  
Installed: 3.10.3-0ubuntu10.2  Candidate: 3.10.3-0ubuntu10.2Nice video!

Are you making a slide presentation? I just opened a multi-page pdf document. Maybe that's why I don't see any animations? I don't make slide presentations and so can't help much. *man evince* doesn't offer any clues.

BTW, [https://bugzilla.gnome.org/show_bug.cgi?id=619825](https://bugzilla.gnome.org/show_bug.cgi?id=619825) has two demo pdfs which you can download and test.

With fadedemo.pdf, I don't see any animation but with transdemo.pdf there are some effects!

Could you upload a small sample pdf file here?

---

### Post by vasa1 on 2017-06-12
Here's one pdf slideshow I found that doesn't show any animations for me: [https://www.sec.gov/news/speech/2012/spch091212sc.pdf](https://www.sec.gov/news/speech/2012/spch091212sc.pdf)

How does it appear for you?

---

### Post by SnuKies on 2017-06-12
> **vasa1 said:**
> Nice video!

Are you making a slide presentation? I just opened a multi-page pdf document. Maybe that's why I don't see any animations? I don't make slide presentations and so can't help much. *man evince* doesn't offer any clues.

BTW, [https://bugzilla.gnome.org/show_bug.cgi?id=619825](https://bugzilla.gnome.org/show_bug.cgi?id=619825) has two demo pdfs which you can download and test.

With fadedemo.pdf, I don't see any animation but with transdemo.pdf there are some effects!

Could you upload a small sample pdf file here?


Well, thank you !
Actually I'm learning for an exam. It is called "Operating Systems" (you learn UNIX and basic stuff about computers)

I see that the document has been created with** LibreOffice 5.3 ** (Evince -> File -> Properties).

PDF with fading : [http://docdro.id/Uda0k6C](http://docdro.id/Uda0k6C)
PDF without fading (4.1mb) : [http://docdro.id/LewmaPf](http://docdro.id/LewmaPf)

Maybe it depends on How it was created? (*1)
**EDIT: **No fading for your PDF :)
**EDIT 2:** I just tested my theory (*1) and I was right: it depends on the settings applied to your PDF when it was first created.

---

### Post by ajgreeny on 2017-06-12
So which particular setting is it that causes the fade transitions and is it only from LOffice?

---

### Post by SnuKies on 2017-06-15
> **ajgreeny said:**
> So which particular setting is it that causes the fade transitions and is it only from LOffice?

I do not understand very well what you're saying, but if it is what I think: I simply created a document with fade transitions in LOffice Impress. Then exported it as PDF and opened it with Evince.
For the moment, I cannot test if it is the same with MS Office.

---

### Post by ajgreeny on 2017-06-15
> **SnuKies said:**
> I do not understand very well what you're saying, but if it is what I think: I simply created a document with fade transitions in LOffice Impress. Then exported it as PDF and opened it with Evince.
For the moment, I cannot test if it is the same with MS Office.
If you created the pdf with fade transitions why are you surprised that you see those transitions when viewing the pdf? Surely that is exactly what you would expect?

---

### Post by SnuKies on 2017-06-16
> **ajgreeny said:**
> If you created the pdf with fade transitions why are you surprised that you see those transitions when viewing the pdf? Surely that is exactly what you would expect?

I thought Evinces has a setting to ignore any transition that's been put on the pdf

---

