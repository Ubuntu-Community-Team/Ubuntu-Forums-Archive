---
title: "RAR packages"
date: 2021-03-21
forum: General Help
---

### Post by lordgallen on 2021-03-21
I am looking for a gui based package that will allow me to archive and encrypt rar files using AES-256. Is there such a package? I have seen this installed in linux before, I don't know how they did it. Thank- you.

---

### Post by CelticWarrior on 2021-03-21
Not an answer but something you should know: [https://www.xmodulo.com/how-to-create-encrypted-zip-file-on-linux.html](https://www.xmodulo.com/how-to-create-encrypted-zip-file-on-linux.html)

---

### Post by lordgallen on 2021-03-21
> **CelticWarrior said:**
> Not an answer but something you should know: [https://www.xmodulo.com/how-to-create-encrypted-zip-file-on-linux.html](https://www.xmodulo.com/how-to-create-encrypted-zip-file-on-linux.html)


great thanks!

---

### Post by lordgallen on 2021-03-21
I am attempting to do it with nautilus, however, it does not give me the other options, hence, I am unable to set password.

---

### Post by CelticWarrior on 2021-03-21
It was possible before but now only the basic features remain in the right-click menu function.
Nemo, a fork of Nautilus, retains that same functionality you might remember from years ago. It's available in the Ubuntu repositories.
That said I don't know the default encryption strength - I think it's AES-128 - but the 7Zip format (.7z) certainly supports AES-256.

---

### Post by Frogs Hair on 2021-03-21
The following my be helpful.

[https://www.tecmint.com/how-to-open-extract-and-create-rar-files-in-linux/](https://www.tecmint.com/how-to-open-extract-and-create-rar-files-in-linux/)

---

### Post by ActionParsnip on 2021-03-21
Why do you have to use rar?

---

### Post by lordgallen on 2021-03-22
> **ActionParsnip said:**
> Why do you have to use rar?


I don't actually, it could be 7zip or something that can be opened in both Linux and Windows, and if possible android.

---

### Post by lordgallen on 2021-03-22
O.K. I decided to install 7zip from Ubuntu repositories since it has good password protection. I will just have to use it from the command line, I think I can manage. When there is an update, will this auto update? Thank-you

---

