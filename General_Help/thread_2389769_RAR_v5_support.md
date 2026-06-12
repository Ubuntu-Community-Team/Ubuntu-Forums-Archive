---
title: "RAR v5 support?"
date: 2018-04-21
forum: General Help
---

### Post by dewdrop_world on 2018-04-21
Ubuntu Studio 16.04 here.

I work in mainland China. For some reason I can't figure out, they *love* RAR archives here. I have terrible problems extracting them in Linux.

The latest one I got -- "unar" says it's "Embedded RAR 5" and then proceeds to fail to extract any of the files. I also tried installing p7zip-rar, but then "p7zip -d the_file" just says RAR is an unrecognized suffix.

```
$ unar 201510055.rar 
201510055.rar: 2018-04-21 16:30:52.425 unar[31012] Archive header
Embedded RAR 5
  SNT 11.mp3  (480762 B)... Failed! (File is not fully supported)
  K.L.11.mp3  (480762 B)... Failed! (File is not fully supported)
  K.O.11.mp3  (480762 B)... Failed! (File is not fully supported)
  SNB 11.mp3  (480762 B)... Failed! (File is not fully supported)
Extraction to directory "201510055" failed (4 files failed.)

$ p7zip -d 201510055.rar 
/usr/bin/p7zip: 201510055.rar: unknown suffix -- ignored
```

I don't mind doing commandline gymnastics to extract these things -- I just want something that works.

Thanks,
James

---

### Post by dragonfly41 on 2018-04-21
Searching .. seems you can install **unrar** package in Ubuntu 16.04..

[https://askubuntu.com/questions/566407/whats-the-easiest-way-to-unrar-a-file-on-ubuntu-12-04/566409](https://askubuntu.com/questions/566407/whats-the-easiest-way-to-unrar-a-file-on-ubuntu-12-04/566409)

---

### Post by jimmy-frydkaer on 2018-04-21
Just install P7Zip via Synaptic and then install p7zip-rar

---

### Post by Holger_Gehrke on 2018-04-21
You are using the wrong tool. 'p7zip' is a wrapper for 7zip meant mainly for use as a filter in pipelines. It expects files to have the extension '.7z' and balks at anything which doesn't have that extension. The executable for normal use of 7zip is named '7z' and is called with the 'x' (extract with directory structure) or 'e' (extract all files into current directory) command to unpack a file.
Example:
```

7z x testfile.rar

```

Or you can install the (non-free) unrar, which should be in the repositories.

Holger

---

