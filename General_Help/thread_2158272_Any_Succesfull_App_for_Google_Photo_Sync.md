---
title: "Any Succesfull App for Google Photo Sync?"
date: 2013-06-28
forum: General Help
---

### Post by agritux on 2013-06-28
I want to use google photo sync with my android phone.
I am using dropbox for this now. Because i can use it on my phone, tablet and pc. But i want to switch google photo sync.
But there is a problem. I tried shotwell (not making two way sync, it makes manuel one way sync), conduit (making two way sync but fails and must start app for sync). 
They dont successful as dropbox.
I am looking for any app working on ubuntu or linux as succesfull as dropbox?
thnx

---

### Post by SeijiSensei on 2013-06-28
What precisely are you trying to do?  Do you want to download the photos from your Google account and edit them in something like GIMP?  I just use the [native downloading tool at Google+]("https://support.google.com/plus/answer/2710716?hl=en").

---

### Post by agritux on 2013-06-28
No. I want only  download and upload automaticaly like dropbox app for ubuntu. (Two way sync)

---

### Post by agritux on 2013-07-01
no apps for google photo sync? :confused:

---

### Post by sirkubax2 on 2014-05-26
Did anyone solved this issue?
Since Ubuntu One Files is closing, it become an issue for me...


I did quick research, And I did fail to find solution of accessing Google+ Photo
Here is my unanwserd topic  [https://groups.google.com/forum/#!topic/google-feature-suggestions/x1QjkEeijq0](https://groups.google.com/forum/#!topic/google-feature-suggestions/x1QjkEeijq0)


Anyway, I did use DropBox for the moment, it works well, except filename renaming, that is inconvinient for me;
I made quick script to fix that

```

#!/usr/bin/env python


import os


files=(os.listdir('.'))


#Current file format: 2014-03-22 14.32.49.jpg
#Expected file format: 2014-03-22_143249.jpg


for myFile in files:
    if " " in myFile:
        date,hour = myFile.split(" ")
        if len(hour.split('.')) == 4:
            hourNew = hour.split('.')[0] + hour.split('.')[1] + hour.split('.')[2] + '.jpg'
            print "%s %s %s" % (date,hour,hourNew)
            newName = date + '_' + hourNew
            print newName
            os.rename(myFile, newName)

```


Anyway, U guess I'm moving to OwnCloud
[https://github.com/owncloud/core/wiki/Ubuntu-One-Migration](https://github.com/owncloud/core/wiki/Ubuntu-One-Migration)
[http://www.muktware.com/2014/04/ubuntu-one-users-can-migrate-open-source-owncloud/25020](http://www.muktware.com/2014/04/ubuntu-one-users-can-migrate-open-source-owncloud/25020)

---

### Post by dragonfly41 on 2014-05-26
spideroak might suit your requirements

[https://play.google.com/store/apps/details?id=com.spideroak.android](https://play.google.com/store/apps/details?id=com.spideroak.android)

---

