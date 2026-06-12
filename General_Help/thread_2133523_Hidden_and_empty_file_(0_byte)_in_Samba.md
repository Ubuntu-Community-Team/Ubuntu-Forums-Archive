---
title: "Hidden and empty file (0 byte) in Samba?"
date: 2013-04-08
forum: General Help
---

### Post by ljs_1969 on 2013-04-08
Hello,

I have Ubuntu 12.04.2 (LTS) installed as my home server and shared some folders using Samba. It was good in the beginning. 
Now there are lots of hidden and empty files (0 byte) displayed in my shared folder. For each of my existing file, there is a hidden and empty file matching it, and the name is like _WNNNJ~3.PDF. 
They aren't real files, not existing in my original folders, just the displaying wrong. I cannot delete those hidden and empty files, it is said 'Cannot find the specified file.'

Is there anything suggestion to fix my problem?

Thanks,

Richard

---

### Post by ljs_1969 on 2013-04-08
It was the problem after I installed antivirus on Ubuntu. I have removed the antivirus.

---

### Post by CharlesA on 2013-04-08
> **ljs_1969 said:**
> It was the problem after I installed antivirus on Ubuntu. I have removed the antivirus.

Which antivirus did you install?

---

### Post by dottodot on 2013-06-21
I'm having the same problem. I did install antivirus at some point but removed it again as it was causing me some issues, however the files are still there and I can't remove them. It's not too much of a problem on Windows as you can hide these files but I've not found a way to do that on mac. It's driving me a bit mad as I have loads of files to scroll past to get to the real folder content.

---

### Post by CharlesA on 2013-06-21
What message do you get when you try to remove the files?

---

### Post by dottodot on 2013-06-21
> **CharlesA said:**
> What message do you get when you try to remove the files?

I don't actually get an error the file disappears for a second then reappears

---

### Post by CharlesA on 2013-06-21
Interesting. Can you see what is using that directory?

```
sudo lsof /path/to/folder
```

---

### Post by dottodot on 2013-06-23
> **CharlesA said:**
> Interesting. Can you see what is using that directory?

```
sudo lsof /path/to/folder
```

On one of the directories where I see the problem it returns

```

bash    23942   plug  cwd    DIR    9,0     4096 3981313 /media/storage/promosmbd    24055 Marcus  cwd    DIR    9,0     4096 3981313 /media/storage/promo
smbd    24055 Marcus   36r   DIR    9,0     4096 3981313 /media/storage/promo
sudo    24058   root  cwd    DIR    9,0     4096 3981313 /media/storage/promo
lsof    24059   root  cwd    DIR    9,0     4096 3981313 /media/storage/promo
lsof    24060   root  cwd    DIR    9,0     4096 3981313 /media/storage/promo

```

so there doesn't seem like anything out of place to me

---

