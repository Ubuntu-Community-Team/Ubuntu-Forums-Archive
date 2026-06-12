---
title: "Command line to convert negative image to positive"
date: 2022-05-18
forum: General Help
---

### Post by satimis on 2022-05-18
Hi all,

Please advise the command of ImageMagick to convert negative image to positive.

Thanks 

Regards

---

### Post by mIk3_08 on 2022-05-18
Please run this command below and paste your result here in this thread so that the community may know your Linux Ubuntu Operating System. Regards and cheers.
```
hostnamectl status
```

---

### Post by Holger_Gehrke on 2022-05-18
The option you're looking for is '-negate'. So

```

convert -negate source.png target.png

```

will read source.png and write the color-inverted image to target.png. As with most options for the ImageMagick family of tools, the option can be used with most if not all of them. Even 'display' accepts it and will give you a preview of what the results will be.

Holger

---

### Post by satimis on 2022-05-18
> **Holger_Gehrke said:**
> The option you're looking for is '-negate'. So

```

convert -negate source.png target.png

```

will read source.png and write the color-inverted image to target.png. As with most options for the ImageMagick family of tools, the option can be used with most if not all of them. Even 'display' accepts it and will give you a preview of what the results will be.

Holger
Hi,

Thanks.

I have tried before posting but made a mistake;

$ convert -negative germany.png germany_positive.png ```

convert-im6.q16: unrecognized option `-negative' @ error/convert.c/ConvertImageCommand/2277.
```

It should be -negate NOT -negative.

Then what will be the command converting negative to positive ?

Regards

---

### Post by Holger_Gehrke on 2022-05-18
The very same option. Run 'convert -negate' on a positive image and you will get a negative, run it on a negative and you'll get a positive.

Holger

---

### Post by satimis on 2022-05-18
> **Holger_Gehrke said:**
> The very same option. Run 'convert -negate' on a positive image and you will get a negative, run it on a negative and you'll get a positive.

Holger
I see.

I have been searching on
Annotated List of Command-line Options
[https://imagemagick.org/script/command-line-options.php](https://imagemagick.org/script/command-line-options.php)

but couldn't find it.

Thanks

Regards

---

### Post by Holger_Gehrke on 2022-05-18
> **satimis said:**
> 
I have been searching on
Annotated List of Command-line Options
[https://imagemagick.org/script/command-line-options.php](https://imagemagick.org/script/command-line-options.php)
but couldn't find it.


Uhmm, ....
[https://imagemagick.org/script/command-line-options.php#negate](https://imagemagick.org/script/command-line-options.php#negate)

Holger

---

### Post by satimis on 2022-05-18
> **Holger_Gehrke said:**
> Uhmm, ....
[https://imagemagick.org/script/command-line-options.php#negate](https://imagemagick.org/script/command-line-options.php#negate)

Holger
Sorry, I meant "positive"

Edit
==
What will be the command lines to reset RGB?  I believe I found them before but unable to locate them now.

---

### Post by #&amp;thj^% on 2022-05-18
> **satimis said:**
> 
What will be the command lines to reset RGB?  I believe I found them before but unable to locate them now.

Is this what your after?
The terminal has a colour scheme which is makes available to various applications like bash and vim. 
There are several colours within the colour scheme available as follows:

```

    0 - Black
    1 - Red
    2 - Green
    3 - Brown/yellow
    4 - Blue
    5 - Purple
    6 - Cyan
    7 - Light grey/white
    9 - Default

```
Sorry for my drive-by.

---

### Post by Impavidus on 2022-05-18
This is basic mathematics: -1×-1=1. The negative of a negative is a positive. convert doesn't care and doesn't know which of the two you consider negative.

---

### Post by TheFu on 2022-05-18
> **satimis said:**
> I see.

I have been searching on
Annotated List of Command-line Options
[https://imagemagick.org/script/command-line-options.php](https://imagemagick.org/script/command-line-options.php)

but couldn't find it.

Thanks

Regards

Is there a reason that someone with your Linux experience doesn't use the manpages for stuff like this? I'd like to understand.
```
         -negate              replace each pixel with its complementary color
```
Ah ... even if you did use the manpage, **that isn't a very clear description**. *I wouldn't have know it either.*  ;)  My scanning software handles negatives. It is a toggle in the options, somewhere.

But, by using the manpages on your system, you'll not see options that don't apply or are for newer versions of the program that may not be any Canonical repos.

Interesting question asked. Thanks.

---

### Post by satimis on 2022-05-18
> **1fallen said:**
> Is this what your after?
The terminal has a colour scheme which is makes available to various applications like bash and vim. 
There are several colours within the colour scheme available as follows:

```

    0 - Black
    1 - Red
    2 - Green
    3 - Brown/yellow
    4 - Blue
    5 - Purple
    6 - Cyan
    7 - Light grey/white
    9 - Default

```
Sorry for my drive-by.

Hi,

I found it here;

Accurate Color Management
[https://imagemagick.org/script/color-management.php](https://imagemagick.org/script/color-management.php)

Remark: On Ubuntu 20.04 magick=convert

Before I came across its command lines to improve the quality of a negative image.  The negative image is scanned on film negative with Smart Phone.

I'm now searching for the command lines.  Can you help?

Thanks

Regards

---

