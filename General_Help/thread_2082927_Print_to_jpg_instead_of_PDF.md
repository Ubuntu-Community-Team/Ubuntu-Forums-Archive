---
title: "Print to jpg instead of PDF"
date: 2012-11-10
forum: General Help
---

### Post by josephellengar on 2012-11-10
When I choose to print something out, I currently have the option "print to PDF." I'd like to make it so that I also have the option of "print to jpg." Is this possible? I know that I can convert PDF to jpg, but I have to do this very often, so it would be much more convenient to print directly to jpg. This question has come up on the forum before, but no one offered an answer except for conversion. I currently use PDF->gimp->jpg. Is there are more efficient way?

Thanks!

---

### Post by gerowen on 2012-11-10
There are extensions for that:

Google Chrome:
[https://chrome.google.com/webstore/detail/screen-capture-by-google/cpngackimfmofbokmjmljamhdncknpmg?hl=en](https://chrome.google.com/webstore/detail/screen-capture-by-google/cpngackimfmofbokmjmljamhdncknpmg?hl=en)

Firefox:
[https://addons.mozilla.org/en-US/firefox/addon/abduction/?src=search](https://addons.mozilla.org/en-US/firefox/addon/abduction/?src=search)

Not sure if there's any Ubuntu software available to do that for every print-capable program.

---

### Post by josephellengar on 2012-11-11
> **gerowen said:**
> There are extensions for that:

Google Chrome:
[https://chrome.google.com/webstore/detail/screen-capture-by-google/cpngackimfmofbokmjmljamhdncknpmg?hl=en](https://chrome.google.com/webstore/detail/screen-capture-by-google/cpngackimfmofbokmjmljamhdncknpmg?hl=en)

Firefox:
[https://addons.mozilla.org/en-US/firefox/addon/abduction/?src=search](https://addons.mozilla.org/en-US/firefox/addon/abduction/?src=search)

Not sure if there's any Ubuntu software available to do that for every print-capable program.

Thanks. Unfortunately all of those extensions save as png and not jpg. My company is standardized on jpg. Also, I do have to do it in other programs as well, so it would be great if there was a way, but I'm not holding my breath for that.

Never mind, just noticed that I can do screenshot for jpg with the Google extension you gave.

---

### Post by Lars Noodén on 2012-11-11
JPEG is quite bad for text documents and line art like graphs and diagrams.  The problem is that at mid- and high-level compression it leaves bad compression artifacts. They can be quite distracting.  PNG is really a better choice for 'printed' documents.  Although PDF would be even better.  It's only when you get into pictures and photographs that PNG would have much advantage over PDF.

---

### Post by Vaphell on 2012-11-11
+1
saving your docs in a lossy format doesn't sound like a good idea and on top of that JPEG is one of the worst formats to store text you can think of. Its compression works nicely when there is a natural grain (like in photos), but in case of clean, sharp black shapes on flat white surface tons of clearly visible mosaic like distortions appear (the algorithm makes sharp edges create ripple effect).
[img]http://upload.wikimedia.org/wikipedia/commons/7/72/Jpeg-text-artifacts.gif[/img]

---

### Post by josephellengar on 2012-11-11
> **Vaphell said:**
> +1
saving your docs in a lossy format doesn't sound like a good idea and on top of that JPEG is one of the worst formats to store text you can think of. Its compression works nicely when there is a natural grain (like in photos), but in case of clean, sharp black shapes on flat white surface tons of clearly visible mosaic like distortions appear (the algorithm makes sharp edges create ripple effect).
[img]http://upload.wikimedia.org/wikipedia/commons/7/72/Jpeg-text-artifacts.gif[/img]

Yeah, I agree. But I don't get to choose how I submit my expense reports. Oh well!

---

### Post by mywai on 2012-11-11
1. Install imagemagick if it is not already installed
2. Create a new folder on your desktop, name it pdf, and put the file you want to convert into pdf into this folder
3. Run Terminal (ctrl + Alt + T)
4. Type in the following command after the $ prompt

cd Desktop/pdf  <RETURN>

mogrify -format jpg *pdf   <RETURN>

:)

---

### Post by josephellengar on 2012-11-11
> **mywai said:**
> 1. Install imagemagick if it is not already installed
2. Create a new folder on your desktop, name it pdf, and put the file you want to convert into pdf into this folder
3. Run Terminal (ctrl + Alt + T)
4. Type in the following command after the $ prompt

cd Desktop/pdf  <RETURN>

mogrify -format jpg *pdf   <RETURN>

:)

I don't want to convert. I already know a million ways to do that. I want to print *directly* to jpg, instead of pdf.

---

### Post by Vaphell on 2012-11-11
write a script that will run in the background, will detect new pdf(s) appearing in a defined location and will convert them automatically. From your perspective there would be next to no difference.

---

### Post by josephellengar on 2012-11-11
> **Vaphell said:**
> write a script that will run in the background, will detect new pdf(s) appearing in a defined location and will convert them automatically. From your perspective there would be next to no difference.

Ooh, good idea. Thanks!

---

### Post by gerowen on 2012-11-11
> **josephellengar said:**
> Ooh, good idea. Thanks!

Just set it up with cron to run every few minutes, :-)

---

