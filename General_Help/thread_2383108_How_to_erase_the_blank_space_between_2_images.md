---
title: "How to erase the blank space between 2 images"
date: 2018-01-21
forum: General Help
---

### Post by satimis on 2018-01-21
Hi all,

I expect erasing the space between 2 images (please refers to upload screenshot) letting the top image just sitting on top of the bottom image.

Adding; <p style="margin-bottom: initial;"> </p>```

<p style="margin-bottom: initial;"><a href="http://life.reynoldstocks.com/wp-content/uploads/2018/01/screenshot_alfi_sign_transp.png"><img class="size-full wp-image-1249 aligncenter" style="border: 0;" src="http://............/screenshot_alfi_sign_transp.png" alt="" width="159" height="149" /></a></p>

```
doesn't work.

Please help.  Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2018-01-21
Is this website publicly visible?
If so, can you please post the link?

---

### Post by SeijiSensei on 2018-01-21
Try setting padding to zero in the <img> tag:
```
<img style="padding-bottom:0" src="http://server/images/topimage.png"><img style="padding-top:0" src="http://server/images/bottomimage.png">
```
Note that I also did not include a space between the image declarations.

The other option is to create a new image in something like the GIMP with the two images juxtaposed together rather than futzing with CSS.

---

### Post by satimis on 2018-01-21
> **halogen2 said:**
> Is this website publicly visible?
If so, can you please post the link?
That webpage is still under construction

---

### Post by satimis on 2018-01-21
> **SeijiSensei said:**
> Try setting padding to zero in the <img> tag:
```
<img style="padding-bottom:0" src="http://server/images/topimage.png"><img style="padding-top:0" src="http://server/images/bottomimage.png">
```
Note that I also did not include a space between the image declarations.

The other option is to create a new image in something like the GIMP with the two images juxtaposed together rather than futzing with CSS.
Thanks for your advice.

Having tried follow:

top image```

<img class="size-full wp-image-1249 aligncenter" style="border: 0; padding-bottom: 0" src="http://path-to/screenshot_alfi_sign_transp.png" alt="" width="159" height="149"> 

```

bottom image```

<img class="size-full wp-image-1218 aligncenter" style="border: 0; padding-top: 0" src="http://path-to/traces_life_11_logo_02_60.png" alt="" width="682" height="140" 
```

Remark```

style="border: 0;"

```
was already there

I also tried "padding-bottom: -2" without effect

satimis

---

### Post by SeijiSensei on 2018-01-23
i think creating a new combined image in the GIMP is likely your easiest option, unless you've never used that program before.  Photoshop?

---

### Post by satimis on 2018-01-24
> **SeijiSensei said:**
> i think creating a new combined image in the GIMP is likely your easiest option, unless you've never used that program before.  Photoshop?
Absolutely agreed.

I ran another way, copying and pasting the images as .bitmap on Libre Writer.  After adjusting them capture the combined images as screenshot and save it as .png image.  That is all

Anyway, thanks again for your advice.

Edit:
I trust there is a coding to make it.  I ran it before.  Unfortunately I don't have recollection nor I could find the coding on my database.

Regards
satimi

---

