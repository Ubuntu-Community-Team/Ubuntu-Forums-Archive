---
title: "Japanese text in pdf is gibberish"
date: 2006-12-11
forum: General Help
---

### Post by Nuggit on 2006-12-11
I got Ubuntu 6.10 a few days ago for my dad. I installed Anthy so he can type Japanese and do his translation work. I did that with the Synaptic Package Installer so I'm assuming that it installed other Japanese stuff on here too.

So one of the PDFs that he needs to work with, the Japanese text shows up as gibberish (math symbols, random english letters, etc) and I cannot figure out what to do to make it show up right.

Please help?

---

### Post by organica on 2006-12-11
Strange, I've seen that before.  Can you see that PDF on any other computer?   It may be corrupt.  Or perhaps the Japanese font installed on your system is not being pulled up by the PDF viewer.  Sorry I can't help any further.

---

### Post by engla on 2006-12-11
Have you tried both acrobat reader (install acroread if you can) and evince? If that doesn't work, you can try to talk to the people who develop evince, they know tons about pdfs -- [http://www.gnome.org/projects/evince/](http://www.gnome.org/projects/evince/) .

---

### Post by drphilngood on 2006-12-11
See here:
 
[Japanese In Adobe Reader How to]("https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto")

---

### Post by Nuggit on 2006-12-12
Thank you all for your responses.
The pdf printed out fine from another computer. I will keep Evince in mind.
I followed your link, drphilngood, and ran into trouble on their first question, make sure Acrobat 7.0 is installed. I tried to install it through Applications>Add/Remove, and it did not work. I did not keep track of the error messages :oops:, so I can't tell you what it said during the process, but now, when I click on the checkbox next to Adobe Reader, it says "Adobe Reader cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."](*,)

---

### Post by drphilngood on 2006-12-12
> **Nuggit said:**
> Thank you all for your responses.
The pdf printed out fine from another computer. I will keep Evince in mind.
I followed your link, drphilngood, and ran into trouble on their first question, make sure Acrobat 7.0 is installed. I tried to install it through Applications>Add/Remove, and it did not work. I did not keep track of the error messages :oops:, so I can't tell you what it said during the process, but now, when I click on the checkbox next to Adobe Reader, it says "Adobe Reader cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."](*,)

It is a [bug]("https://launchpad.net/distros/ubuntu/+source/gnome-app-install/+bug/57981").  You just need to add the multiverse repositories to your sources.list.  Here is a link to show you how to do this:

[psychocats-sources]("http://www.psychocats.net/ubuntu/sources")

Post back if you need further assistance.

---

### Post by rajeshgautam on 2007-03-13
I had a similar problem. Although I couldnt get evince and kghostview to show japanese font. But kpdf shows the japanese fonts correctly afte installing xpdf-japanese package

---

### Post by rajeshgautam on 2007-03-14
Later Iinstalled all the (seemingly) relevant packages which were returned by searching "CJK font" in synaptic. After this Evince also started showing the fonts properly.

---

### Post by paulvbrown on 2008-05-26
> **rajeshgautam said:**
> I had a similar problem. Although I couldnt get evince and kghostview to show japanese font. But kpdf shows the japanese fonts correctly afte installing xpdf-japanese package

Sweet -- installing xpdf-japanese package did it for me in Evince.  THANKS!

---

