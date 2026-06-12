---
title: "what do I do with a QR code in chrome?"
date: 2021-05-16
forum: General Help
---

### Post by david503 on 2021-05-16
My chrome doesn't have this, but apparently the windows version does:

[https://www.mobigyaan.com/wp-content/uploads/2021/03/How-to-create-QR-Code-using-Google-Chrome-on-your-PC-or-Mac-2.jpg](https://www.mobigyaan.com/wp-content/uploads/2021/03/How-to-create-QR-Code-using-Google-Chrome-on-your-PC-or-Mac-2.jpg)

Anyway, what do I do if someone (a form) gave me a QR code, how do I go to it in chrome in ubuntu? All the sites talk about how to *make* a qr code, not go to one. 

18.04
chrome: Version 90.0.4430.212 (Official Build) (64-bit)

thanks

---

### Post by him610 on 2021-05-16
Maybe this will help. It has a section on generating a qr code, as well as, a section on scanning a qr code.
[https://linuxcommando.blogspot.com/2020/07/how-to-generate-and-read-qr-code-on.html]("https://linuxcommando.blogspot.com/2020/07/how-to-generate-and-read-qr-code-on.html")

---

### Post by david503 on 2021-05-16
> **him610 said:**
> Maybe this will help. It has a section on generating a qr code, as well as, a section on scanning a qr code.
[https://linuxcommando.blogspot.com/2020/07/how-to-generate-and-read-qr-code-on.html](https://linuxcommando.blogspot.com/2020/07/how-to-generate-and-read-qr-code-on.html)

Thanks, I'm looking for a way to do it in chrome.  Or how to get that icon in the address bar in the linux version.

---

### Post by Holger_Gehrke on 2021-05-17
I think you misunderstood the [article]("https://www.mobigyaan.com/create-qr-code-using-google-chrome-pc-mac") that image is in. It's about creating QR-codes, mostly so you can quickly open the same page on your phone by taking a picture of the screen using the phone. **Q**uick **R**esponse codes are really meant for mobile devices. If you absolutely have to use a QR-code on your PC, something like
```

xdg-open $(zbarcam --raw)

```
will read in a QR-code from the camera and open the URL from it in your default browser. For using QR codes directly in your browser there are extensions you can install, for example [this one]("https://chrome.google.com/webstore/detail/qr-code-reader-for-google/gmloihcgbhbonllenincdakeijmikcne").

Holger

---

### Post by him610 on 2021-05-17
Ok, seems to be more trouble than it's worth. It can be done though.
Using Chrome browser...
I went to the referenced webpage in post#1, generated the qr code, downloaded it to my desktop - it's a png file.
If one right-clicks on the qr-code.png, a drop down list will appear, second option down is, 'Open with', click on browser (FireFox), it then opens up to the original webpage. This is the qr-code I just created.

[ATTACH=CONFIG]288486[/ATTACH]

I can see where this might be helpful when one wants to send the generated webpage qr-code to a friend or acquaintance. I suppose one could send the qr-code to one's phone using email or sms message  Why not just send the webpage link?

---

### Post by him610 on 2021-05-17
Got to thinking that my reply (#5) was like a snake eating its tail, or what was the term we used in the past, recursion?
So here is another newly (Chrome) generated qr-code...

[ATTACH=CONFIG]288487[/ATTACH]

Hmmm, opening it with FireFox did not work this time except as a png file. Maybe I was wrong in my earlier post. 
Scan it with your phone to see where it takes you. Hint: It is a safe website.

---

### Post by ActionParsnip on 2021-05-17
[https://askubuntu.com/questions/22871/software-to-read-a-qr-code#22899](https://askubuntu.com/questions/22871/software-to-read-a-qr-code#22899)

Reads a QR code in the terminal

---

### Post by him610 on 2021-05-17
An article on scanning qr-codes using Chrome, 
[https://www.cnet.com/how-to/chrome-iphone-qr-codes-barcodes/]("https://www.cnet.com/how-to/chrome-iphone-qr-codes-barcodes/")

or
I intended to post the qr-code to the referenced webpage in this space, but I could not do it. Maybe there is a forum limit as to how many images one can post daily.

---

