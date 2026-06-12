---
title: "Folder not deleted"
date: 2008-03-30
forum: General Help
---

### Post by gastoncs on 2008-03-30
Hi delete a file on a folder and when I type locate on the command line it appear even though is not on the folder.

can some one tell me way is that

thanks in advance

---

### Post by HermanAB on 2008-03-30
The locate database hasn't been updated yet:
[http://www.gsp.com/cgi-bin/man.cgi?section=8&topic=locate.updatedb](http://www.gsp.com/cgi-bin/man.cgi?section=8&topic=locate.updatedb)

Cheers,

Herman

---

### Post by gastoncs on 2008-03-30
Thanks!
 I have a folder in this path [email]root@gaston:~/.wine[/email]/drive_c#
but when i try to access "root@gaston:~/.wine/drive_c# cd  Program Files this message"  appear "bash: cd: /root/.wine/drive_c/Program: No such file or directory". 
and the file is there because i see it when do the ls -l, but I cant access do you know way?

thanks

---

### Post by drs305 on 2008-03-30
cd "Program Files"

You have to put it in quotes since there is a space in the folder name.  Notice how the error message it stops after ...drive_c/Program  because it thinks it's reached the end of the folder name.

---

### Post by pbpersson on 2008-03-30
> **gastoncs said:**
> Thanks!
 I have a folder in this path [email]root@gaston:~/.wine[/email]/drive_c#
but when i try to access "root@gaston:~/.wine/drive_c# cd  Program Files this message"  appear "bash: cd: /root/.wine/drive_c/Program: No such file or directory". 
and the file is there because i see it when do the ls -l, but I cant access do you know way?

thanks

In Windows if you have a folder called "C:\Program Files" and you do to a DOS prompt and at the root type "CD Program Files"  it will tell you that "C:\Program" does not exist because it stops reading the parameters once it hits the fiirst space

In Windows you need to put quotes around the filename such as CD "Program Files"

---

### Post by gastoncs on 2008-03-30
wow thanks the fast response

---

