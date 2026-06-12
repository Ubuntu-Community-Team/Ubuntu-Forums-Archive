---
title: "ImageMagick command"
date: 2022-05-19
forum: General Help
---

### Post by satimis on 2022-05-19
Hi all,

What will be the command line to adjust the RGB color value of an image?

Thanks

Regards

---

### Post by #&amp;thj^% on 2022-05-19
Using ImageMagick.

Then you would be able to run the following command from your shell:
```

$ convert cmyk_image.jpg -colorspace rgb rgb_image.jpg
```

A guide/reference is available at the ImageMagick project wiki. [https://legacy.imagemagick.org/Usage/formats/#color_profile](https://legacy.imagemagick.org/Usage/formats/#color_profile)

---

### Post by satimis on 2022-05-20
> **1fallen said:**
> Using ImageMagick.

Then you would be able to run the following command from your shell:
```

$ convert cmyk_image.jpg -colorspace rgb rgb_image.jpg
```

A guide/reference is available at the ImageMagick project wiki. [https://legacy.imagemagick.org/Usage/formats/#color_profile](https://legacy.imagemagick.org/Usage/formats/#color_profile)
Thanks for your advice.

To adjust the value of brightness and contrast
```

$ convert -brightness-contrast 10x5 image.jpg

```
I can change the values of 10 and 5 to have a different result on the image.

I wonder whether there are similar commands on adjusting Color, Sharpness, Hue etc ?

Regards

---

### Post by #&amp;thj^% on 2022-05-20
> **satimis said:**
> 
I wonder whether there are similar commands on adjusting Color, Sharpness, Hue etc ?

Regards
Your going hard on this, lots of reading.
Study hard there will be a test tomorrow: [https://imagemagick.org/script/command-line-options.php](https://imagemagick.org/script/command-line-options.php)
 :)

---

