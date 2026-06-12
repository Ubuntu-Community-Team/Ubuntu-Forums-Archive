---
title: "Unrar"
date: 2008-02-11
forum: General Help
---

### Post by thealphamale05 on 2008-02-11
I downloaded redhat 4 from torrent and in the dir it has 10 or so .rar files named RHEL4-U5-i386-AS-disc1.iso.part1.rar  where of course there are several discs and multiple parts. Inside each .rar file are parts of the iso named RHEL4-U5-i386-AS-disc1.iso but there are multiple .rar files with different parts of the iso.... so how do i combine the different ISOs? i have tried unrar e RHEL4-U5-i386-AS-disc1.iso.part1.rar and untar x RHEL4-U5-i386-AS-disc1.iso.part1.rar which works to extract that one .rar archive but i need to combine the isos..... please help i have googled for half an hour

---

### Post by doorknob60 on 2008-02-11
I don't remember how to do that in Ubuntu (I think there's a way though), but the Windows version of WinRAR works perfect in wine :D That's what I use for split rar's.

---

### Post by nemilar on 2008-02-11
I'm not entirely sure I understand you.  If I hear you correctly, you're saying that "unrar e *" works to extract the ISO files fine, but there are multiple ISOs, and you want to combine them into one big ISO?  I don't think it works like that... you have to burn a disk per ISO.

---

### Post by qpieus on 2008-02-11
Not sure what you mean by "combine the isos", but as far as unrar goes - do you have unrar or unrar-free installed? unrar-free may not extract the multipart archives properly. I use plain old unrar (which is the non-free version, located in the multiverse repo) and it extracts multipart archives just fine with the command syntax you are using. You tell unrar the filename of the "part1" file and it should do the rest. I suspect you have the unrar-free version installed and that is why it's not working.

---

### Post by thealphamale05 on 2008-02-11
I am using the regular unrar 

here is the dir that i downloaded from torrent


blackbox:/slave/temp/torrent/complete/RedHat-RHEL4-U5-i386-AS # ls
md5sums.txt                           RHEL4-U5-i386-AS-disc3.iso.part4.rar
RHEL4-U5-i386-AS-disc1.iso.part1.rar  RHEL4-U5-i386-AS-disc3.iso.part5.rar
RHEL4-U5-i386-AS-disc1.iso.part2.rar  RHEL4-U5-i386-AS-disc3.iso.part6.rar
RHEL4-U5-i386-AS-disc2.iso.part1.rar  RHEL4-U5-i386-AS-disc3.iso.part7.rar
RHEL4-U5-i386-AS-disc2.iso.part2.rar  RHEL4-U5-i386-AS-disc4.iso.part1.rar
RHEL4-U5-i386-AS-disc2.iso.part3.rar  RHEL4-U5-i386-AS-disc4.iso.part2.rar
RHEL4-U5-i386-AS-disc2.iso.part4.rar  RHEL4-U5-i386-AS-disc4.iso.part3.rar
RHEL4-U5-i386-AS-disc2.iso.part5.rar  RHEL4-U5-i386-AS-disc4.iso.part4.rar
RHEL4-U5-i386-AS-disc2.iso.part6.rar  RHEL4-U5-i386-AS-disc4.iso.part5.rar
RHEL4-U5-i386-AS-disc2.iso.part7.rar  RHEL4-U5-i386-AS-disc4.iso.part6.rar
RHEL4-U5-i386-AS-disc3.iso.part1.rar  RHEL4-U5-i386-AS-disc4.iso.part7.rar
RHEL4-U5-i386-AS-disc3.iso.part2.rar  RHEL4-U5-i386-AS-disc5.iso.rar
RHEL4-U5-i386-AS-disc3.iso.part3.rar  _ThePirateBay



ok and inside for instance RHEL4-U5-i386-AS-disc1.iso.part1.rar 
is
RHEL4-U5-i386-AS-disc1.iso
and inside  
RHEL4-U5-i386-AS-disc1.iso.part2.rar 
is also 
RHEL4-U5-i386-AS-disc1.iso
but they are different sizes 179 Mb and 178 Mb

---

### Post by qpieus on 2008-02-11
try this in a terminal in the directory containing the parts:

unrar x RHEL4-U5-i386-AS-disc1.iso.part1.rar

pay attention to the output - look for errors, etc.

BTW, you have only 2 parts for disc 1? That doesn't seem enough (note that discs 2,3,and 4 have 7 parts). Try the same unrar x command with the other disc's part1 file too.

Here's the output from a multipart rar set on my computer:
```
unrar x testfile.part1.rar

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal


Extracting from testfile.part1.rar

Extracting  testfile.avi                                 

Extracting from testfile.part2.rar

...         testfile.avi                                 

Extracting from testfile.part3.rar

...         testfile.avi                                 

Extracting from testfile.part4.rar

...         testfile.avi                                 

Extracting from testfile.part5.rar

...         testfile.avi                                 

Extracting from testfile.part6.rar

...         testfile.avi                                 

Extracting from testfile.part7.rar

...         testfile.avi                                 

Extracting from testfile.part8.rar

...         testfile.avi                                   OK
All OK

```

---

### Post by thealphamale05 on 2008-02-12
Qpieus you get the props on this post, although i was doing it right all along... disc 1 comes to a total of 178 Mb so there was a bit of confusion in that regard. Anyway the rest of the cds are coming out  to right under 700 Mb. 


Thanks

---

