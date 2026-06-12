---
title: "Use filename extension instead of content type to choose default application ?"
date: 2012-11-16
forum: General Help
---

### Post by scotty64 on 2012-11-16
I would like to associate the default application for a certain file type "the old way" by using the filename extension (*.doc etc.) instead of the file contents. The reason for this is the increasing number of applications using the XML file format. Currently all XML type files - even if they use different filename extensions - can only be associated with one application.

---

### Post by LewisTM on 2012-11-16
Install 'File Types Editor' a.k.a. **assogiate**.
Add a new file type. You can give it a number of attributes. The most important is the filename, which should be *.<your extension here>.

File name patterns take precedence over file contents or XML elements. So even if the MIME susbsystem detects the file as XML, it should identify your file correctly. Of course, a more elegant way would be to specify XML elements for your file type but that can be tricky.

One your new file type is created, you can associate an application with it from within Thunar or Xfce4's MIME type editor.

Cheers!

---

### Post by scotty64 on 2012-11-16
Thanks a lot! That solved something that annoyed me for a long time...

> **LewisTM said:**
> Install 'File Types Editor' a.k.a. **assogiate**.
Add a new file type. You can give it a number of attributes. The most important is the filename, which should be *.<your extension here>.

File name patterns take precedence over file contents or XML elements. So even if the MIME susbsystem detects the file as XML, it should identify your file correctly. Of course, a more elegant way would be to specify XML elements for your file type but that can be tricky.

One your new file type is created, you can associate an application with it from within Thunar or Xfce4's MIME type editor.

Cheers!

---

