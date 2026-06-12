---
title: "How to create transparent backgroun on .gif file?"
date: 2018-01-19
forum: General Help
---

### Post by satimis on 2018-01-19
Hi all,

I have a .gif file (pls refers to the upload file)

I ran;```

convert gyroscope_operation150x150.gif -transparent white gyroscope_operation150x150_transp.gif

```

It can't work.  The file generated is not clear.

Please advise.

Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2018-01-19
Can you use [FONT=Courier New]gifsicle[/FONT]? -
```
gifsicle -t '#FFFFFF' --disposal bg gyroscope_operation150x150.gif > gyroscope_operation150x150-Transparent.gif
```

Refer to [FONT=Courier New]man gifsicle[/FONT] for more info

---

### Post by satimis on 2018-01-19
> **halogen2 said:**
> Can you use [FONT=Courier New]gifsicle[/FONT]? -
```
gifsicle -t '#FFFFFF' --disposal bg gyroscope_operation150x150.gif > gyroscope_operation150x150-Transparent.gif
```

Refer to [FONT=Courier New]man gifsicle[/FONT] for more info
Hi,

Thanks for your advice.

Installed gifsicle and ran;
&#10219; gifsicle -t '#FFFFFF' --disposal bg gyroscope_operation150x150.gif > gyroscope_operation150x150-Transparent.gif```

gifsicle: warning: too many colors, using local colormaps
  (You may want to try ‘--colors 256’.)

```

Again;
&#10219; gifsicle -t '#FFFFFF' --disposal bg gyroscope_operation150x150.gif --colors 256 > gyroscope_operation150x150-Transparent.gif

It works.  Please see the upload file

Regards
satimis

---

