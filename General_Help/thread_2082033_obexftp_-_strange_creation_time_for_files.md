---
title: "obexftp - strange creation time for files"
date: 2012-11-08
forum: General Help
---

### Post by vlad2005 on 2012-11-08
I want to transfer files to my Nokia phone using an USB cable.
I make necesarly permision in udev and used obexftp. File are transfered to my phone, but strange, modified time is somewhere in year 2047 so my phone not listing, and cannot see in my phone, only with obexftp.
Here is content listed with obexftp. File "beautiful ..m4a" have an modified date at 20471231. That is 12/31/2047. Another file here, transfered via bluetooth have correct time (was transfered some time ago)
```

<file name="iphone2.mp3" size="53969" modified="20110313T063428Z" user-perm="RWD"/>
<file name="Beautiful Smile.m4a" size="5295011" modified="20471231T220000Z" user-perm="RWD"/>

```

What is the problem with this date, and how can be resolved?

---

### Post by vlad2005 on 2012-11-08
Sorry!!!
I found the problem. Is with file itself not with obexftp. I transfer another file and everything work well.
Anyway, still strange creation date for file transfered on phone with obexftp.

---

