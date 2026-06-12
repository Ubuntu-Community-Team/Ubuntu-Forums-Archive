---
title: "Can't burn certain files to a dvd rw"
date: 2015-12-24
forum: General Help
---

### Post by cleiton-xavier on 2015-12-24
Hello, I have been trying to write certain files to a dvd rw without  sucess. It's not a generalized thing, because I have been able to write  many files to it, so it's a subset of the files/folders that are causing  the problem.

Unfortunately I don't have enough knowledge to be able to understand brasero session-log.

First I tried to burn one big directory with many files. Here is the resulting brasero session-log: [ATTACH=CONFIG]266361[/ATTACH][ATTACH=CONFIG]266361[/ATTACH] [ATTACH]266363[/ATTACH]

At the end of the log it complains about a specific file. I removed it  from the big folder and tried to burn it individually do the DVD. It  worked.

Then I removed the sub-folder that contains this file and then tried to burn the big folder without  the sub-folder. It failed and here is the new brasero session-log: [ATTACH]266364[/ATTACH]

Here it have the impression that the problem might be related to a  symbolic link, but don't know why neither what I should do to get rid of  it.
(BTW, the second log file was too big to be attached, so I removed many  of the error messages that were identical to the previous ones and putted several  ..... ...... ...... to indicate the place of removal)
(BTW2, sorry for the confused, repeated attachments, but I still wasn't able to figure out how to use the attachment options correctly. Anyway the three files that show first are the same, and the ones that shows up in the last line are repetitions)

Any suggestions?[ATTACH=CONFIG]266362[/ATTACH][ATTACH=CONFIG]266361[/ATTACH]

---

### Post by scdbackup on 2015-12-25
This is a problem with ISO 9660 producer program genisoimage:

BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/media/a/imagens/AA/old%2520post%2520card-0138 postcard.jpg' and '/media/a/imagens/AA/old%2520post%2520card-0138 postcard.jpg' have the same Rock Ridge name 'old%2520post%2520card-0138 postcard.jpg'.

Hard to say why it gets to the impression that there are two files with the same path.
If this is originally the same file on hard disk that got mappped two times into the ISO,
then i would expect that the first file gets overwritten by the second one.

Try in Brasero menu "Plugins" to disable "mkisofs" and "genisoimage" and rather enable "libisofs".
(You might have to install libisofs.)

Another possibility would to try Xfburn rather than Brasero.

---

### Post by egeezer on 2015-12-25
I second the idea to try Xfburn instead of Brasero (based on personal experience).

---

### Post by cleiton-xavier on 2015-12-25
> **scdbackup said:**
> Try in Brasero menu "Plugins" to disable "mkisofs" and "genisoimage" and rather enable "libisofs".
(You might have to install libisofs.)

Another possibility would to try Xfburn rather than Brasero.


  Hi, I can't disable genisoimage, mkisofs is not enabled and there isn't this libisofs.  You can see it here, it's the first screenshot:
[http://s72.photobucket.com/user/john_smith140/library/?view=recent&page=1](http://s72.photobucket.com/user/john_smith140/library/?view=recent&page=1)


 Anyway, if this it is an ISO 9660, should I try another filesystem, like UDF?

---

### Post by kurt18947 on 2015-12-25
I've had problems with Brasero in the past and installed k3b. It brings a bunch of KDE dependencies with it but that hasn't caused a problem to my knowledge. I'll have to try XFBurn.

---

