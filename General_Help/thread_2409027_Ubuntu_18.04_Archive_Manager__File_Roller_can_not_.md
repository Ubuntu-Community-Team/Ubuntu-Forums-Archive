---
title: "Ubuntu 18.04 Archive Manager / File Roller can not open APK files"
date: 2018-12-26
forum: General Help
---

### Post by feartheterrapin on 2018-12-26
Under Ubuntu 16.04 there was no issue opening an APK file.  I believe Archive Manager / File Roller was used to open these files.  Under 18.04, I have not found any archive applications that can open an APK file.  Is there a way that Ubuntu 18.04  can open APK files.  And why was this capability removed in 18.04.

---

### Post by ajgreeny on 2018-12-27
Never tried this but see if the info at [https://askubuntu.com/questions/1045082/how-to-open-an-apk-file-in-ubuntu-18-04](https://askubuntu.com/questions/1045082/how-to-open-an-apk-file-in-ubuntu-18-04) helps; basically you need to run command ```
cp file.apk file.zip
```
I do not know if changing the filetype suffix would work instead of copying the file, but that may also be worth a try.

---

### Post by feartheterrapin on 2018-12-27
@ajgreeny  Thanks.  Yeah, renaming the file to a zip file works as a work around and in some situations more convenient than booting to Ubuntu 16.04.  I still do not understand the reasoning for removing the capability from Ubuntu 18.04.  I would think some sort of  tweak in file-roller could accomplish it.

---

### Post by Irihapeti on 2018-12-28
Xarchiver will open an APK file. No alteration of the filename extension is needed.

---

### Post by feartheterrapin on 2018-12-28
> **Irihapeti said:**
> Xarchiver will open an APK file. No alteration of the filename extension is needed.

Thank you.  That is exactly what I was looking for.  I still do not understand why that capability was removed from the Ubuntu default archive applications.

---

