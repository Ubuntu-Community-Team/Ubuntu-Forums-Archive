---
title: "how to extract a lzma file"
date: 2007-07-06
forum: General Help
---

### Post by owl on 2007-07-06
hello :)

I got a very huge file (33 go!) compressed in .tar.lzma
I searched how to handle this but still could not extract it. I installed the P7zip package who is supposed to do the job, but i get this error:

lambda@lambda:/media/sda4/36G-wpa-psk-hash-tablesh1kari/wpa_psk-h1kari_renderman$ 7z e wpa_tables.tar.lzma wpa-tables/bigtables

7-Zip 4.43 beta  Copyright (c) 1999-2006 Igor Pavlov  2006-09-15
p7zip Version 4.43 (locale=fr_FR.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Processing archive: wpa_tables.tar.lzma

Error: wpa_tables.tar.lzma is not supported archive
lambda@lambda:/media/sda4/36G-wpa-psk-hash-tablesh1kari/wpa_psk-h1kari_renderman$


Any idea about that and how to handle properly this lzma file? I had a look a the man page for 7z, but may be i don't use the right command?

---

### Post by Ex-Cyber on 2007-07-06
It sounds like you need the "lzma" package, which provides "unlzma".

---

### Post by grryf on 2007-10-25
To unpack/uncompress wpa_tables.tar.lzma archive you will need lzma from website: [http://tukaani.org/lzma/download](http://tukaani.org/lzma/download)
Download
unpack tar -zxf lzma*
cd lzma*
./configure
make
make install

Read help, I think it should be: 
lzma -dv wpa_tables.tar.lzma
tar -xf wpa_tables.tar

Or.. you can connect the two commands in one eg:
lzma -cd wpa_tables.tar.lzma | tar -xf

but I'm not sure of it...

Best Regards!
Hope it will help..many individuals...

---

