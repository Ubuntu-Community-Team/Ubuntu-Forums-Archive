---
title: "Filename encoding of ext3 partition"
date: 2007-12-29
forum: General Help
---

### Post by jorgepeixoto on 2007-12-29
Hi. I have an ext3 partition for sharing data between Ubuntu and Windows (I installed an ext2 driver for windows from fs-driver.org).

The problem is that special characters like ú (I'm Brazilian) are misrepresented. 

As I understand, Ubuntu stores the filenames with UTF-8, while Windows seemed to use a single-byte encoding. When I created a file from Ubuntu which name had a special character, Windows saw the special character as two funny characters.

I thought Windows used ISO-8859-1, so I tried changing the Ubuntu locale to pt_BR.ISO-8859-1. It still didn't work. I noticed that when I create in Windows a file whose name contains 'ú', Ubuntu sees it as '£', which is byte 163 in ISO-8859-1. I looked what encoding puts 'ú' on byte 163, and I think it is codepage 850. So it seems Windows stores the filenames with codepage 850.

1) I don't know how to change the windows encoding; and if I change, it would affect all windows partitions (AFAIK), including windows' C: , which already has a lot of files with names encoded with codepage 850.

2) I don't know if I can set Ubuntu to use codapage 850 (it seems that only UTF-8 and ISO-8859-1 are available), nor do I know if that would be wise.

3) I looked for a mount option for ext3 that would affect only the ext3 filenames, like the mount options for fat. It seems ext3 does not have such options.

How can I solve this problem?

---

