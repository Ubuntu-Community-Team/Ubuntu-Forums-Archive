---
title: "How can I convert UTF-8 csv file to EUC-JP?"
date: 2015-09-16
forum: General Help
---

### Post by Daisuke_Minagawa on 2015-09-16
Hi, everybody. Please give me an advise.

I'd like to convert big file size(about 300+Mbyte) UTF-8 of .csv file to EUC-JP .csv file.
Could you kindly tell me how can to convert to EUC-JP?

I have tried 
nkf -e --overwrite daisuke.csv
But it convert the csv file to CP51932 encoding. I need to convert .csv to EUC-JP.

Best regarsd, 
Daisuke

---

### Post by SeijiSensei on 2015-09-16
Use **iconv**:

```
iconv -f UTF-8 -t EUC-JP -o newfile.csv oldfile.csv
```

I checked with "iconv -l" and EUC-JP is a supported encoding.

---

### Post by Daisuke_Minagawa on 2015-09-17
Thank you, SeijiSensei!
But I have failed to convert it. The file is too big?

---

### Post by SeijiSensei on 2015-09-18
Is that the error message you get?  File too big?

I wouldn't think the size of the file matters.  My guess is that iconv reads each byte from the source file converting on-the-fly and writing the output.  Are you running out of file space on your computer?  It seems unlikely that you wouldn't have another 300 MB free, but you never know.

---

