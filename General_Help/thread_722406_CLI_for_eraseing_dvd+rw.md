---
title: "CLI for eraseing dvd+rw"
date: 2008-03-12
forum: General Help
---

### Post by Ancient One on 2008-03-12
I know I have seen it here before but I can not find it. I would like the CLI for erasing dvd+rw and also for erasing cd-rw. Thanks

---

### Post by rattking on 2008-03-12
dvd+rw-format /dev/dvd
and
wodim blank=fast dev=/dev/cdrom
wodim blank=help to see all the blanking options
replace /dev/dvd with whatever your device actually is

---

### Post by Ancient One on 2008-03-12
Thanks. Let me try a slightly different approach to the same question. What would be the CLI equivalent to having Nautilus erase the disc prior to Nautilus writing to the disc. The dvd+rw-format actually does a format and not a "blank" on the disc reducing the life of the disk. I am not trying to be picky but there is a difference. The format will destroy all the data on the disc. The blanking will leave the data recoverable by expensive and fancy equipment. The reason that I have to blank is that sometime my wife Windows machine does not like the media unless it is really "clean". I know I can use Brassero for this but I do not use the software for backing up my files. Nautilus work just fine for that little project (~150 meg).

Thanks again.

---

