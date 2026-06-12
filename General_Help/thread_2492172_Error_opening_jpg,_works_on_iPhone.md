---
title: "Error opening jpg, works on iPhone"
date: 2023-11-02
forum: General Help
---

### Post by connyeklow on 2023-11-02
Many jpgs on a Danish museum site can´t open because of error but works fine on my iPhone. I have tried Firefox, Opera and Chromium on Ubuntu 22.04 but same problem. This is an example where it doesn't work: [https://drive.reindex.net/DMFURT/10/RP13922.jpg](https://drive.reindex.net/DMFURT/10/RP13922.jpg)
The museum is [https://designmuseum.dk/](https://designmuseum.dk/) and the furniture database function is [https://mus.reindex.net/DMFURT/main/Landing.php](https://mus.reindex.net/DMFURT/main/Landing.php) , you can for example put "Mogensen" in the search field and then you get a lot of broken picture links.

---

### Post by ajgreeny on 2023-11-02
What happens if you try to download that linked .jpg and then open it in a dedicated image viewer and what do you get if you run a simple **file /path/to/your.jpg** command?

---

### Post by coffeecat on 2023-11-02
Support, not chat. *Thread moved to **General Help**.*

---

### Post by connyeklow on 2023-11-02
I can download it, no problem finding and viewing it. If you open the broken picture in a new window you get : Picture cannot be displayed, as it contains errors.
When I rightclick and choose Inspect I get : 
[h=2][Clickable elements must be focusable and should have interactive semantics]("https://developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Keyboard?utm_source=devtools&utm_medium=a11y-panel-checks-keyboard#clickable_elements_must_be_focusable_and_should_have_interactive_semantics")[/h]

---

### Post by Holger_Gehrke on 2023-11-02
Have you tried running 'file' on the downloaded image ? Or using 'identify' from ImageMagick ? I downloaded the first two broken images in the results for 'Mogensen' (right click, copy adress, command line wget + the copied address) and both were not actual JPEG files but TIFF renamed to jpg. There are reasons TIFF is not normally used on the web, the best one being that there's an almost infinite variety of TIFF variants. So the problem is that your phone knows how to handle that specific TIFF variant while your PC/web-browser doesn't. The fault is mostly with the web designer, he should have used any other file format than TIFF. Oh, and transmitting an 8 MB image with a resolution of 3487x2455 only to have it scaled down to 228x232 is probably a crime against humanity ...

Holger

---

### Post by MAFoElffen on 2023-11-03
+1 --

I found the same as Holger. 

If I downloaded it, resized it to display faster in a webpage, then converted from tiff to jpg, bmp, or png, I could then add it to an HTML page and it displayed fine from several browsers...

---

### Post by btindie on 2023-11-03
The file incorrectly has a *.jpg extension as it's actually a tiff.
```

$ file RP13922.jpg 
RP13922.jpg: TIFF image data, little-endian, direntries=15, height=2478, bps=8, compression=none, PhotometricIntepretation=BlackIsZero, width=3481

```
That results in apache returning the header
```
Content-Type: image/jpeg
```
Which is why the web browsers you've tried are correctly returning an error.
If you rename it
```
mv RP13922.jpg RP13922.tiff
```
you can then view it.

It looks like their website is broken along with devices that display it as it is.

---

