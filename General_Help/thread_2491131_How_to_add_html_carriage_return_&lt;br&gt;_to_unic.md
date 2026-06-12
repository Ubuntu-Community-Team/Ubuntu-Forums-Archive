---
title: "How to add html carriage return &lt;br&gt; to unicode text file?"
date: 2023-09-27
forum: General Help
---

### Post by OracleNix on 2023-09-27
Hi there

Running qrencode generates a unicode text file - see commands below.  When calling qrencode or the "qr.out" file in HTML, it does not render correctly, as I assume that HTML does not recognise the carriage returns...  How to add html <br> at the end of each line, or how to render the text correctly in HTML?

$ qrencode -t UTF8i 1234 > qr.out
$ file qr.out 
qr.out: Unicode text, UTF-8 text
$ cat qr.out 
                             
                             
    &#9608;&#9600;&#9600;&#9600;&#9600;&#9600;&#9608;   &#9600; &#9608; &#9608;&#9600;&#9600;&#9600;&#9600;&#9600;&#9608;    
    &#9608; &#9608;&#9608;&#9608; &#9608; &#9600; &#9600; &#9604; &#9608; &#9608;&#9608;&#9608; &#9608;    
    &#9608; &#9600;&#9600;&#9600; &#9608;  &#9608;&#9604;&#9608;&#9600; &#9608; &#9600;&#9600;&#9600; &#9608;    
    &#9600;&#9600;&#9600;&#9600;&#9600;&#9600;&#9600; &#9608; &#9608; &#9600; &#9600;&#9600;&#9600;&#9600;&#9600;&#9600;&#9600;    
    &#9600;&#9600;&#9600;&#9604;&#9600;&#9600;&#9600;&#9600;&#9600; &#9608;&#9604;&#9600;&#9608;&#9600;&#9604;  &#9600; &#9604;    
    &#9600;   &#9604;&#9604;&#9600;&#9604;&#9600;&#9600; &#9608;&#9604;&#9608;&#9600;&#9608;&#9604;&#9604;&#9600; &#9604;    
    &#9600;&#9600;&#9600;&#9600;  &#9600; &#9604; &#9604;&#9600; &#9600;&#9608;&#9600;  &#9608;&#9608;&#9600;    
    &#9608;&#9600;&#9600;&#9600;&#9600;&#9600;&#9608; &#9608;&#9604;&#9604; &#9600; &#9604; &#9600; &#9604; &#9600;    
    &#9608; &#9608;&#9608;&#9608; &#9608; &#9600;&#9604; &#9604;&#9600;&#9604;&#9600;&#9604;&#9600;&#9604;&#9600;&#9604;&#9600;    
    &#9608; &#9600;&#9600;&#9600; &#9608; &#9608; &#9608;&#9608;&#9604;&#9608;&#9600;&#9608;&#9604;&#9608;&#9600; &#9600;    
    &#9600;&#9600;&#9600;&#9600;&#9600;&#9600;&#9600; &#9600; &#9600;&#9600; &#9600;&#9600;&#9600; &#9600;&#9600; &#9600;    
                             

When viewed in HTML it looks like this, which is not readable:
&#9608;&#9600;&#9600;&#9600;&#9600;&#9600;&#9608; &#9604; &#9608; &#9600;&#9608;&#9604;&#9608;&#9604;&#9604; &#9600;&#9604;&#9600; &#9604; &#9608;&#9600;&#9600;&#9600;&#9600;&#9600;&#9608; &#9608; &#9608;&#9608;&#9608; &#9608; &#9604;&#9604;&#9604; &#9608;&#9600;&#9604;&#9604; &#9608;&#9600; &#9600;&#9608;&#9600; &#9608; &#9608;&#9608;&#9608; &#9608; &#9608; &#9600;&#9600;&#9600; &#9608; &#9604;&#9608; &#9604;&#9604; &#9604;&#9608;&#9604;&#9604;&#9600;&#9608;&#9600;&#9604;&#9600;&#9600; &#9608; &#9600;&#9600;&#9600; &#9608; &#9600;&#9600;&#9600;&#9600;&#9600;&#9600;&#9600; &#9600;&#9604;&#9608;&#9604;&#9600; &#9608;&#9604;&#9600; &#9600;&#9604;&#9600;&#9604;&#9600;&#9604;&#9608; &#9600;&#9600;&#9600;&#9600;&#9600;&#9600;&#9600; &#9600;&#9600;&#9608;&#9600;&#9600; &#9600;&#9600;&#9608;&#9600;&#9604;&#9600;&#9604;&#9604;&#9604;&#9608; &#9600;&#9608;&#9604;&#9604;&#9604;&#9600; &#9604;&#9600; &#9600; &#9600;&#9604;&#9600;&#9604; &#9604;&#9600;&#9600; &#9600;&#9600;&#9600;&#9608; &#9600; &#9604;&#9608;&#9600;&#9608;&#9604;&#9600;&#9604;&#9604;&#9604;&#9604;&#9604;&#9604;&#9600;&#9604;&#9604;&#9600;&#9600; &#9604;&#9600;&#9604; &#9604; &#9608;&#9604;&#9604; &#9600;&#9600;&#9608;&#9608;&#9600; &#9600; &#9600;&#9600; &#9600;&#9600;&#9604;&#9604;&#9608;&#9600; &#9604;&#9600; &#9600; &#9608;&#9604; &#9604; &#9600; &#9600;&#9600;&#9608;&#9600;&#9600;&#9604;&#9600; &#9608;&#9600; &#9604;&#9600;&#9608;&#9600;&#9600;&#9604;&#9600;&#9604;&#9604;&#9604;&#9604;&#9604;&#9604;&#9608;&#9600;&#9608;&#9608;&#9600; &#9600; &#9604;&#9600;&#9600;&#9600; &#9608;&#9600;&#9600;&#9604;&#9604;&#9604;&#9600; &#9604; &#9600;&#9608;&#9604;&#9604;&#9604; &#9600;&#9600; &#9604;&#9604;&#9608;&#9604; &#9600;&#9608; &#9604;&#9604;&#9608;&#9600;&#9608;&#9600;&#9604;&#9608; &#9604;&#9608;&#9600;&#9600;&#9600;&#9600;&#9604;&#9608;&#9600;&#9604;&#9600;&#9604;&#9600;&#9600;&#9604;&#9608;&#9604; &#9608; &#9608; &#9600;&#9608; &#9600;&#9604;&#9608;&#9608;&#9600; &#9600; &#9600; &#9608;&#9600;&#9608; &#9608;&#9608;&#9608;&#9604;&#9608;&#9604; &#9608;&#9604;&#9600;&#9608;&#9600;&#9604; &#9608; &#9604;&#9608;&#9608;&#9600;&#9600;&#9608; &#9604;&#9608;&#9600; &#9604; &#9608;&#9600;&#9600;&#9604;&#9600;&#9604;&#9604;&#9604;&#9600;&#9600;&#9604;&#9600; &#9608;&#9600; &#9600; &#9600; &#9600;&#9600;&#9608;&#9608; &#9600;&#9604;&#9604;&#9604;&#9608;&#9608; &#9600; &#9608;&#9608;&#9608; &#9608;&#9600;&#9600;&#9600;&#9608; &#9604;&#9604; &#9608;&#9600;&#9600;&#9600;&#9600;&#9600;&#9608; &#9600;&#9604;&#9608; &#9604;&#9608;&#9600;&#9604; &#9600;&#9604;&#9604;&#9604;&#9604;&#9604;&#9608;&#9608; &#9600; &#9608;&#9600;&#9604;&#9604;&#9604; &#9608; &#9608;&#9608;&#9608; &#9608; &#9608;&#9608;&#9600; &#9600; &#9600;&#9604; &#9600; &#9608;&#9608; &#9600;&#9600;&#9600;&#9600;&#9600;&#9600; &#9600; &#9608; &#9600;&#9600;&#9600; &#9608; &#9608; &#9608;&#9608;&#9600; &#9604; &#9600;&#9604;&#9600;&#9604;&#9604;&#9608;&#9608;&#9600;&#9600;&#9604; &#9608;&#9608; &#9600;&#9600;&#9600;&#9600;&#9600;&#9600;&#9600; &#9600;&#9600; &#9600; &#9600; &#9600; &#9600;&#9600;&#9600;&#9600; &#9600; &#9600;

---

### Post by Holger_Gehrke on 2023-09-27
Why not simply enclose it in '<pre></pre>' ? That's the tag for pre-formatted text.

Holger

---

### Post by MAFoElffen on 2023-09-27
You misunderstand something... Especially for using that in an HTML page.

RE: [Ubuntu man qrencode]("https://manpages.ubuntu.com/manpages/xenial/man1/qrencode.1.html")
 
That is not how that is supposed work for what you want to do... Read the first line that explains what that utility "is"...
```

qrencode - Encode input data in a QR Code and save as a PNG or EPS image.

```
The input to it is text, the default output is a png file.

Your command was:
```

 qrencode -t UTF8i 1234 > qr.out

```
To do what you want to do and use it for, it should have been something like this:
```

 qrencode -t PNG --output=qr.png "1234"

```
Then in your HTML page, you add the image to it with image tags. PNG graphics files are universal to all browsers. They will display, and be the same for all browsers, by all users on any platform.

If you create it as UT8i, it did exactly as you told it to. It created it as symbols without any carraige returns. That is not how you would want it to add to an HTML page. Right? To do that, you would have to post-process it with sed, searching for the hex value of the line-feeds, and replacing them with either the text "\n" or the text "<BR>"" and there is no guaranty that is would display correctly in the myriad of browsers out there running on different platforms. A user that is not using UT8i in their browser settings and that would change that. See that as a problem now?

You see where you are causing yourself problems and extra work with that original command and format, right?

---

### Post by OracleNix on 2023-09-29
> **Holger_Gehrke said:**
> Why not simply enclose it in '<pre></pre>' ? That's the tag for pre-formatted text.

Holger

Hi Holger
Thanks, this helps and it works, but it squashes a bit...  Maybe I need to tweak some more.  

What does work well is when new lines and spaces are replaced with <br> and &nbsp.

$ qrencode -t UTF8 manyThanks | sed -z 's/\n/<br>/g' | sed -e 's/\\s/\&nbsp;/g'

---

