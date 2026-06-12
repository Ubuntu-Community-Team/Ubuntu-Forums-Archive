---
title: "RAR archives are empty (Ubuntu 14.04 LTS)"
date: 2018-01-24
forum: General Help
---

### Post by SnuKies on 2018-01-24
Ever since I did installed Ubuntu 14.04 on my SSD I can't extract/visualize **.rar** archives. With **.zip** I have no problems, only with .rar

At first I thought it has to do something with permissions, but even after I gave execute permission to .rar file, I could not open it
I also installed **RAR **and **7zip** from Ubuntu Software Center and nothing.

What else can I do?


EDIT: if I compress a file in Ubuntu with **.rar **extensions, I can decompress them with no problem, but I still cannot decompress  **.rar **archives from Windoes

---

### Post by monkeybrain20122 on 2018-01-24
Install p7zip-rar or p7zip-full from the repo, I think either should be installed automatically if you have installed ubuntu-restricted-extras

---

### Post by SnuKies on 2018-01-25
I did and it's the same ...

---

### Post by monkeybrain20122 on 2018-01-25
How many .rar did you try? Maybe you have a corrupt .rar archive? I never have problems opening them from Windows.

---

### Post by Impavidus on 2018-01-25
From [Wikipedia]("https://en.wikipedia.org/wiki/7-Zip"):> 7-Zip v15.06 and later support extraction of files in the RAR5 format.It seems Ubuntu 14.04 somes with p7zip 9.20, so if these are the latest version of rar files, they may not be supported by your version of Ubuntu. Ubuntu 17.10 should work. Older versions of the rar format should work too.

You can tell the version of the rar file from its magic number. Try```
hexdump -n 8 filename.rar
```If you get something like```
5261 7221 1a07 00**
```it's an older version of rar, if you get something like```
5261 7221 1a07 0100
```it's the later version of the rar format.

But I have to say I never use rar format. As a proprietary format with no free compressor, it isn't very popular in de Linux world.

---

### Post by SnuKies on 2018-01-25
> **monkeybrain20122 said:**
> Install p7zip-rar or p7zip-full from the repo, I think either should be installed automatically if you have installed ubuntu-restricted-extras


Not many, but everytime I try to open one I can't see anything


@Impadivus I run the command but I get nothing

---

### Post by Impavidus on 2018-01-25
Nothing at all? Not even an error message like "file or directory doesn't exist", "command not found" or "permission denied"? I only get no output at all if the file is empty. And I don't mean an archive with no files in it, but a file of zero bytes. That isn't even an archive, as it has no file format at all. (In Linux, file formats are only defined by the contents of the file, the extension is just a useful convention for humans and some applications.)

It seems something went wrong with copying this file to your Ubuntu system.

BTW, compressing a file in Ubuntu with the .rar extension doesn't necessarily make it a rar file, although I assume in the proprietary RAR program it does.

---

