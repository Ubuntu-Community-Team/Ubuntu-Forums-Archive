---
title: "JDK cannot install"
date: 2008-05-02
forum: General Help
---

### Post by Lord DEA on 2008-05-02
Hello everyone,
I was trying to install Sun's JDK 6 Update 6, and just downoaded it from
[here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter;pgid=yYdgaHqkkjVSR0EUPIQsoQ3D0000n4krw3zz;sid=6BmM7Qgp6SSM60AySxjE6OeBDfN2R8VsvftDLBU30xSp5g==")
I downloaded the file jdk-6u6-linux-i586-rpm.bin, but when I double click the file, i get an errorsaying:
'Couldn't display "blah/blah/blah/jdk-6u6-linux-i586-rpm.bin" there is no aplication installed for this kind of file'

I have already changed the permissions to execute the file. but still get the same error.
I have installed build-essentials.

:confused:
Any idea?

Thanks

---

### Post by Glaxed on 2008-05-02
yeah, man that's an rpm file.
I don't think Sun offers debs, so try searching some Ubuntu repositories or failing that, try alien to convert the rpm

---

