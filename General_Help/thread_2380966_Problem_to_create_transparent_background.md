---
title: "Problem to create transparent background"
date: 2017-12-24
forum: General Help
---

### Post by satimis on 2017-12-24
Hi all,

I have a logo with pale blue colour background.  Please see attached file.  I ran following command line trying to change the backgroung as transparend
```

$ convert reynoldstocks_logo35.png -transparent '#CCDCE7' reynoldstocks_logo35_transp.png 

```

```

$ convert reynoldstocks_logo35.png -transparent 'color=#CCDCE7' reynoldstocks_logo35_transp.png 

```

```

$ convert reynoldstocks_logo35.png -transparent 'rgba(0,0,0,0)' reynoldstocks_logo35_transp.png 

```

```

$ convert reynoldstocks_logo35.png -background 'rgba(0,0,0,0)' reynoldstocks_logo35_transp.png 

```

Non of them can work

The color code #CCDCE7 was found by Gcolor2.  Please help.

[COLOR="#FF0000"]**Merry Christmas and Happy New Year 2018 !!!**[/COLOR]

Thanks
satimis

---

### Post by Frogs Hair on 2017-12-24
I opened the image in gimp and selected color to alpha under the layer/transparency options.

---

### Post by again? on 2017-12-24
Use a fuzz option with this command as well.
Try 5%.
```
convert reynoldstocks_logo35.png -fuzz 5% -transparent '#CCDCE7' reynoldstocks_logo35_transp.png
```

---

### Post by satimis on 2017-12-25
> **Frogs Hair said:**
> I opened the image in gimp and selected color to alpha under the layer/transparency options.
Thanks for your advice.

Performed following steps;

1)
Open the file with GIMP

On top menu bar
-> click -> Colors
-> select -> Color to Alpha...
-> check -> Preview
From: [white color as default] to alpha
-> click - OK

Transparent background created

2)
On top menu bar
-File -> Export as

Export the file as .png format
-> Export```

(uncheck) Save background color
(check) Save resolution (default)
(check) Save creation time (default)
(check) Save color values from transparent pixels (default)
Compression level: [9] (default)
-> Export

```

That is all.

Regards
satimis

---

### Post by satimis on 2017-12-25
> **guber2 said:**
> Use a fuzz option with this command as well.
Try 5%.
```
convert reynoldstocks_logo35.png -fuzz 5% -transparent '#CCDCE7' reynoldstocks_logo35_transp.png
```
Thanks for your advice.

I left out -fuzz

5% did the job.  Increasing its value made no different.  Reducing its value a trace of blue color remained.

Regards
satimis

---

