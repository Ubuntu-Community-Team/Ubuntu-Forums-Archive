---
title: "Download manager that support &quot;refresh link&quot; facility"
date: 2014-10-03
forum: General Help
---

### Post by rjochacko on 2014-10-03
Is there a download manager that support refreshing download link if it expires like IDM.
Currently I am using aria2c, does this have that facility? What about multiget and kget?

Because when I resusme some downloads after several hours of inactivity, it keep on showing 'Download aborted' , 'failed to download' or 'Bad request'.

---

### Post by abbaheart2012 on 2014-10-03
Have you tried to test your internet speed? 

Try this comand in terminal. Post the out put of this when you reply thanks.;)

```
wget -O /dev/null http://speedtest.wdc01.softlayer.com/downloads/test10.zip
```

---

### Post by vasa1 on 2014-10-03
I don't know what you mean by "support refreshing download link if it expires", but if a download aborts because of a dropped connection, the default of aria2 is to resume from where the download was interrupted. In other words, if I run```
aria2c "url"
``` and that should download a 100 MB file and the transfer is interrupted after only 49 MB have been downloaded, I just run exactly the same command again and the remaining 51 MB is downloaded.

Re.> Because when I resusme some downloads after several hours of inactivity, it keep on showing 'Download aborted' , 'failed to download' or 'Bad request'. Real examples would help.

---

### Post by ajgreeny on 2014-10-03
Depending on the browser you use you might find the downthemall add-on useful.  It's available for firefox but I'm not sure about chrome or chromium as I seldom use them, but there is a chrono-download-manager available for them.

---

