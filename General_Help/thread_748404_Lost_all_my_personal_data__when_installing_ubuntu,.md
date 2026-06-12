---
title: "Lost all my personal data  when installing ubuntu, HELP please!"
date: 2008-04-07
forum: General Help
---

### Post by beodo0 on 2008-04-07
Tired of windows, yesterday I decided finally to install ubuntu for first time. When installing I choose "use all drive..." Why? I have a stupid day I think..becouse what I wanted to do is dual boot xp/ubuntu, and as you can know, all my xp data is lost now.

 I have ALL my personal data in the ntfs partition from xp (persnal pictures, works...) irrecuperable data :(.

Could somebody tell me the best way to recover the biggest part of data that is possible??

Thanks ind advice, and regards from Spain!

PD: Sorry If posted already, but searching I cant find anybody whit the same problem. (Maybe I was the only so prick to do this lol)

---

### Post by HermanAB on 2008-04-07
You'll need to send it to a data recovery expert house with special equipment and it will cost thousands of dollars.

Soooo, enjoy your nice clean system...

---

### Post by cdenley on 2008-04-07
You can try photorec.

```

sudo apt-get install testdisk

```

Of course, you shouldn't boot to the drive you are trying to recover from.

---

### Post by Terry S on 2008-04-07
If you have access to a Windows PC you could try this site [http://datarecoverysofware.com/datarecovery/general_recovery.php?m=119&gclid=CLvntI3gyZICFSY1aAodZn58bA](http://datarecoverysofware.com/datarecovery/general_recovery.php?m=119&gclid=CLvntI3gyZICFSY1aAodZn58bA).

You may have to connect your hard drive to the Windows PC to recover the date

Or

Take the Hard Disk out and take it to a data recovery specialist. Here in the UK that will cost about £140 per disk.

or 

Surf the net for alternative data recovery options they are out there.

You are not alone in making mistakes like that. Good Luck.

---

### Post by cdenley on 2008-04-07
That first link looks like the windows, closed-source equivalent to ntfsundelete, so it probably won't help you. I tested photorec, and it will recover some files from an ntfs filesystem reformatted with ext3.

---

### Post by beodo0 on 2008-04-07
I have recovered almost all my pictures and mp3s, with easy recovery professional using a pc with xp, but I have lost the directory estructure.

Recover the files whit her original file estructure. it´s impossible?
Maybe with ntfsundelete??
thanks

---

### Post by cdenley on 2008-04-07
ntfsundelete will only read valid ntfs filesystems. If it has been reformatted as ext3, it cannot read it.

---

