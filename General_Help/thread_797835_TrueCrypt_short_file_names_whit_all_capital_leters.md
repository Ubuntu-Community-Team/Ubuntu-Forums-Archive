---
title: "TrueCrypt: short file names whit all capital leters are displayed with small letters."
date: 2008-05-17
forum: General Help
---

### Post by sal-e on 2008-05-17
Hi Everybody,
I have a sticky situation here. I am using Ubuntu 8.04LTS, I installed TrueCrypt 5.1a. It works, but I run into small problem with the filenames. It may be bug in Ubuntu, TrueCrypt or most likely lack of my knowledge.

Here is the situation. I have a TC file container stored on USB flash drive. I am running PortableApps that I need when I am away from my PC. Those apps are Windows programs. When I get home I would like to make a unencrypted backup. I just switch to Ubuntu as my primary OS. My sync process fails because the files with short names ( <=8 ) all capital letters are displayed with all small letters. Here are the tests done so far.

1. I did mount TC file in Windows with TrueCrypt 5.1a and the file names are displayed correctly.

2. I went back to my Linux PC and created two new files with all capital names. The first one was only 8 letters long and the second 9 letters. After I refreshed my window the file with 8 chars was displayed again in all small letters, but the longer name was just fine. Then I went back to Windows and both files was shown in all caps.

3. I went back to my Linux PC and tried to rename the short name back to all caps but it failed because the file with that name all ready exist. At this point I was sure that it is bug in Nautilis file browser.

4. To confirm my suspicion I repeated the test on unencrypted partition and I found out it is not the case. The file with short names and all caps are displayed correctly. To make sure I went to Terminal and ran 'ls -al' the result was the same. On the regular FAT partition there is no problem, but on FAT truecrypt mounted the problem is persistent.

5. I have examined other file names and I notice some other problems. For example some chars like " ' " are displayed as " ? " and etc. This give me the idea that may be the problem is the way TC mount the volume. I try to pass parameters like 'shortname=mixed utf8' but truecrypt did not accept that.

Any suggestions please? 

Thank you,
SAL-e

---

### Post by Caribdis on 2008-09-17
Almost the same problem here. I have Truecrypt 6.0 in Ubuntu 8.04.

In the TC file container, when I create a folder with **all** capital letters in its name, it became "automatically" to small letters when I try to open it.
But when I create a file with all capital letters in its name, or a folder with at least one small letter in its name, these names are preserved.

¿Someone knows what's happening?

---

### Post by sal-e on 2008-09-20
Hi Caribdis,

Back then I posted the same message on TrueCrypt's forum and I have received only one suggestion that did not work for me.

[INDENT]Try forcing your filesystem to mount as vfat instead of msdos.
Command line would be something like:

```
truecrypt --filesystem=vfat <volumefilepath> <mountpath>
```

If that doesn't work, recreate it as vfat first then mount it as vfat.
[/INDENT]

You can try it with TrueCrypt 6.0 again.
I believe that it is bug in TrueCrypt, but I don't have the skills to trace it down. I am using TrueCrypt to encrypt my PortableApp.com and Windows doesn't care about the file name very much. But now I am almost fully switched to Linux and this problem will become a pain for me.

SAL-e

---

