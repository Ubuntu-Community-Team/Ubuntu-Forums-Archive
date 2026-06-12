---
title: "Regex issue"
date: 2013-09-21
forum: General Help
---

### Post by alfirdaous on 2013-09-21
Hello everybody

I've got a mp3 file, and I am looking to check if some metadata fields contain a word except "alfirdaous"

```

$ mediainfo 001-Done.mp3 
General
Complete name                            : 001-Done.mp3
Format                                   : MPEG Audio
File size                                : 590 KiB
Duration                                 : 37s 746ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 128 Kbps
Album                                    : album_tag
Album/Performer                          : per_tag
Part/Position                            : 1
Track name                               : title
Track name/Position                      : 001
Performer                                : per
Composer                                 : Any Name
Conductor                                : alfirdaou
Encoded by                               : alfirdaous
Publisher                                : alfirdaous
Genre                                    : Jazz
Released date                            : 2013
Encoded date                             : now
Writing library                          : Lavf53.21.1
Copyright                                : alfirdaous
comment                                  : alfirdaous
File type                                : audio/mp3
filename                                 : 001.mp3
service_name                             : alfirdaous
service_provider                         : alfirdaous
variant_bitrate                          : 128
TYER                                     : 0

```

I am looking forward to check these fields: comment, Composer, Conductor, Encoded by, Publisher, Copyright, service_name and service_provider. If you noticed ONLY "Composer" has a different name, how can I perform this check?

I've heard about something like:

```

mediainfo file.mp3 | grep \'comment\|Composer\|Conductor\|Encoded by\|Publisher\|Copyright\|service_name\|service_provider\'';

```

if one of the fields above does NOT contain the name "alfirdaous" it should print something:

```

File "file.mp3", field "Composer" has a wrong sentence

```

Thanks in advance

---

### Post by steeldriver on 2013-09-21
I'd suggest 'awk' for something like this e.g.

```

$ cat mediainfo | awk -F: '$1 ~ /comment|Composer|Conductor|Encoded by|Publisher|Copyright|service_name|service_provider/ && $2 !~ /alfirdaous/ {print}'
Composer                                 : Any Name
Conductor                                : alfirdaou

```

---

### Post by alfirdaous on 2013-09-22
The above command line does not contain any file name

```

mediainfo cat 001.mp3 | awk ...

```

---

### Post by CaptainMark on 2013-09-22
Remove cat and try again with just ```
mediainfo 001.mp3 | awk....
```

---

### Post by steeldriver on 2013-09-22
Thanks Mark - @alfirdaous since I didn't have your mp3 file, I copied your mediainfo text into a file (hence the cat) in order to test the awk expression

---

### Post by alfirdaous on 2013-09-25
Thx everybody

---

