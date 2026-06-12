---
title: "Command to compress gif file size"
date: 2018-06-01
forum: General Help
---

### Post by satimis on 2018-06-01
Hi all,

I need to compress a .gif file from 3.6Mb to 2Mb.

I ran following command without success```

$ convert image.gif -quality 80% new_image.gif 

```
But failed

Instead it increased the file size from 3.6Mb to 4.4MB

Please help.  Thanks

Regards
satimis

---

### Post by Holger_Gehrke on 2018-06-02
The option '-quality' is for jpeg, MIFF and PNG. It doesn't do anything for gif. If the .gif is a single static image, you could reduce the number of colours (gif is palette based, 256 is the maximum number of colours, legal sizes are powers of 2) or use PNG instead, which uses a more modern compression algorithm . If it's an animated gif, you can either use gifsicle (it's in the repos) or try convert with the options '-fuzz n% -layers Optimize' with different values for 'n'.

Holger

---

### Post by SeijiSensei on 2018-06-02
If it's an animated gif, you might try removing a few layers. You'd be surprised at how well our eyes and minds interpolate.

---

### Post by satimis on 2018-06-02
Hi all,

Thanks for your advice.

It is an animated gif

Following command helped me out;```

&#10219; convert input.gif -fuzz 23.5% -layers Optimize output.gif

```
The output file size is 2MB, without much sacrificing image quality 

23.5% was found by several testings not by calculation.

But I couldn't sort out using gifsicle
&#10219; gifsicle -i input.gif --optimize=3 -o output.gif

The size of output.gif is same as the input.gif

Regards
satimis

---

