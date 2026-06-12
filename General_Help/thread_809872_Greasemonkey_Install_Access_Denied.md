---
title: "Greasemonkey Install: Access Denied"
date: 2008-05-27
forum: General Help
---

### Post by ragflan on 2008-05-27
Hi, I'm using Firefox 3 Beta 5 on Hardy Heron, and I have this error coming up every time I try to install a Greasemonkey script through the Greasemonkey addon in Firefox. Something about NS_ERROR_FILE_ACCESS_DENIED. I'm the only user on this computer and I know the root password. The error is below:


[IMG]http://s02.divshare.com/athena2/thumbs/2008/05/27/4598682/4598682-b91_display.jpg[/IMG]

Please help. Thank you! Also, I always wanted to know if it is okay that I have the same root password and account password.

---

### Post by y-lee on 2008-05-27
Sounds like a permissions issue. After you install Greasemonkey, you'll see in your Firefox profile directory a folder named "gm_scripts". Inside that folder, you'll see config.xml. Note your firefox profile directory is hidden so open nautilus and click view show hidden files and assuming you only have one firefox profile navigate to 

```
/home/username/.mozilla/firefox/xxx.default/gm_scripts
```

where *username* is your ubuntu username and *xxx* is a seeming random string of characters. Right click the file **config.xml** and then choose properties, you should be the owner of this file and have both read and write privileges. If you don't have read and write privileges check these boxes. If for some odd reason root owns this file, you can not change the permissions post back or this does not help post back:)

---

### Post by ragflan on 2008-05-27
Yup! That fixed it! Thanks a lot!

---

### Post by y-lee on 2008-05-27
Well glad to hear that it was just a guess. 

Go ahead and mark this thread as solved then, click on thread tools above to do so. It makes the forums easier to use for those of us helping people people :)

---

