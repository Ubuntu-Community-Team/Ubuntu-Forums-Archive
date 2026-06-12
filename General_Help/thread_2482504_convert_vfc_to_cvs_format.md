---
title: "convert vfc to cvs format"
date: 2023-01-02
forum: General Help
---

### Post by Old Jimma on 2023-01-02
Hello Ubuntuers:

Cell phone contact data can often be downloaded as a vfc formated file.

THese are pretty hard to use.

Does anybody know of an Ubuntu app to convert vfc to csv format?

Thanks,
Old

---

### Post by MAFoElffen on 2023-01-02
> **Old Jimma said:**
> Does anybody know of an Ubuntu app to convert vfc to csv format?
I think this is what you meant: '[vcf2csv]("https://vcf2csv.sourceforge.net/")'

---

### Post by Old Jimma on 2023-01-03
Thanks.  I downloaded it and don't know what to do with it. Do I need to compile it?

---

### Post by #&amp;thj^% on 2023-01-03
Yes, you will need to extract it, then "" cd to the path where downloaded.
There is a read me, or there should be one.
If you run into problems let us know.

---

### Post by Old Jimma on 2023-01-03
I issued the following commands:

> 
sudo apt install  vcftools

vcf2csv -i protonContacts-2023-01-01.vcf > protonContacts-2023-01-01.csv

vcf2tsv -i protonContacts-2023-01-01.vcf > protonContacts-2023-01-01.csv


Neither of these worked.

---

### Post by #&amp;thj^% on 2023-01-03
Not how you install this with "apt"
Before moving on though show me this please:
```
vcf2csv -v

```

---

