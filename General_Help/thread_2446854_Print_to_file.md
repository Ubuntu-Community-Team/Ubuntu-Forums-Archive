---
title: "Print to file"
date: 2020-07-07
forum: General Help
---

### Post by archerbob on 2020-07-07
As per the last post in [this closed thread]("https://ubuntuforums.org/showthread.php?t=1587985") I am having the issue where when I try to "print to file" it only prints the 1st page and chops everything else off for blank pages.  I have tried installing CUPS PDF and it prints to file the same way, but with a woeful font.

So far the only work around I've found is to select the text and images I want and copy/paste them to LibreOffice Writer, then export as PDF.

Does anyone know a fix or alternative to the default system print to file or the CUPS PDF?

I am currently using Ubuntu 16.04 on a Quad Core 2.0GHz (2.8GHz Turbo) system with 16GB RAM, using Firefox 78.0.1 (64-bit)

---

### Post by monkeybrain20122 on 2020-07-07
I think it is a firefox issue. [https://support.mozilla.org/en-US/questions/1277535](https://support.mozilla.org/en-US/questions/1277535)

If you do print preview first then it prints everything. Also printing works with no issue on other browsers like Chrome or Opera.

P.S I experienced this a few months ago but I can no longer reproduce the problem on FF 78.0.1 Do you have a link to the page you want to print?

---

### Post by archerbob on 2020-07-15
> **monkeybrain20122 said:**
> I think it is a firefox issue. [https://support.mozilla.org/en-US/questions/1277535](https://support.mozilla.org/en-US/questions/1277535)

If you do print preview first then it prints everything. Also printing works with no issue on other browsers like Chrome or Opera.

P.S I experienced this a few months ago but I can no longer reproduce the problem on FF 78.0.1 Do you have a link to the page you want to print?

Funnily enough I have Opera & Chrome installed too and it does it with them too, also with the print preview.

---

### Post by dino99 on 2020-07-15
is it a custom system install ? check that the metapckages are installed

---

### Post by ActionParsnip on 2020-07-15
Xenial is end of life next year, you may want to consider upgrading to Bionic before it pops.

Do other applications that aren't web browser work OK? Sounds specific to Firefox so far....

---

### Post by monkeybrain20122 on 2020-07-15
> **ActionParsnip said:**
> Xenial is end of life next year, you may want to consider upgrading to Bionic before it pops.

Do other applications that aren't web browser work OK? Sounds specific to Firefox so far....

Not everyone can update just because of a newer distro is around. I am still using xenial in my main machine and next year is just the right time to go to focal (when all bugs are ironed out and bionic would be old by then)  Everything is working top shape here, I wouldn't upgrade and throw all those hours of fine tuning out just because xenial is "old". I have the latest and greatest software that I use through compiling from source, ppa and flatpak.
 
@OP can you provide a link? Like I said it happened to me before, and only with Firefox (on both my machines, one with xenial the other with bionic) but now I can't reproduce it either on Xenial or focal (no more bionic here)

---

### Post by monkeybrain20122 on 2020-07-17
Just printed out a multiple paged document on Firefox & Ubuntu 16.04. All pages got printed, I didn't even do preview.

---

