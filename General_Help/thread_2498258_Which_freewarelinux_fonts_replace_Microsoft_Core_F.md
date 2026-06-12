---
title: "Which freeware/linux fonts replace Microsoft Core Fonts?"
date: 2024-06-06
forum: General Help
---

### Post by 909mjolnir on 2024-06-06
Which freeware/linux fonts replace Microsoft Core Fonts?

I just want to use replacements, websafe substitutes instead of the microsoft fonts.

---

### Post by psychohermit on 2024-06-07
sudo apt install ttf-mscorefonts-installer

--glenn

---

### Post by grahammechanical on 2024-06-07
> I just want to use replacements, websafe substitutes instead of the microsoft fonts.

Just use the fonts that come with Ubuntu anyway. The developers of Ubuntu have even provided a Ubuntu font family.

[https://design.ubuntu.com/font](https://design.ubuntu.com/font)

In applications like LibreOffice Writer and Calc you will find a long list of free and open source font families. Microsoft TrueType fonts will only appear in that list if we have deliberately installed the free to download and install ttf-mscorefonts. These are old font families that Microsoft mistaken removed the copyright to and then regretted it but could not reclaim them as copyright. I do not think that more modern MS font families are free to download and use. We would only get access to the modern fonts if we install a Microsoft application that uses MS fonts. And to do that we would need to purchase a MS licience.

Regards

---

### Post by speartip on 2024-06-08
If I understand what you're asking correctly, I replace with the following, which I think are correct:
Times New Roman - Dejavu Serif
Arial - Dejavu Sans
Calibri - Carlito
Cambria - Caladea
Those are the common ones. Although in LibreOffice you can replace them with whatever you want via the replacement table.

---

### Post by HermanAB on 2024-06-08
The Redhat Liberation fonts were designed to fix the font compatibility issues: [https://www.redhat.com/en/blog/liberation-fonts](https://www.redhat.com/en/blog/liberation-fonts)

---

### Post by kamennedev on 2024-06-08
Italo Vignoli of The Document Foundation published a LibreOffice HOWTO explaining how he configures font substitution when a document needs to be shared with a Word user. It's quite a handy little tutorial, I keep it bookmarked:

[https://blog.documentfoundation.org/blog/2020/09/08/libreoffice-tt-replacing-microsoft-fonts/](https://blog.documentfoundation.org/blog/2020/09/08/libreoffice-tt-replacing-microsoft-fonts/)

Good luck.

---

### Post by 909mjolnir on 2024-06-11
> **speartip said:**
> If I understand what you're asking correctly, I replace with the following, which I think are correct:
Times New Roman - Dejavu Serif
Arial - Dejavu Sans
Calibri - Carlito
Cambria - Caladea
Those are the common ones. Although in LibreOffice you can replace them with whatever you want via the replacement table.

Thanks, that's what I was looking for!  

I remember Caladea and Carlito.  Thanks also HermanAB.

---

