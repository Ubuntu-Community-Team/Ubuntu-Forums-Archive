---
title: "Vsftpd"
date: 2017-01-31
forum: General Help
---

### Post by lochness123 on 2017-01-31
I'm working on FTP server (Ubuntu). According to a video on the internet I configured it (sudo apt-get install vsftpd etc) and joined FTP to localhost (ftp localhost) - everything worked. After a while, I came to a point, where it was necessary to add users and console wrote my an error about permissions. 

According to another video I changed my permissions to a root permissions. I rebooted FTP and when I tried to connect FTP to localhost, it wrote me error: "FTP: connect: connection refused." Do you know how to solve this problem?

---

### Post by DuckHook on 2017-01-31
If you followed instructions from videos, please post links to those videos. In any case, it is not generally a good idea to follow advice found in videos without further researching to confirm that such instructions are safe, effective and conform to best practices. Many people post videos without the foggiest notion of what they are doing.

What commands did you actually execute to change permissions? You can display your command history with the the simple *history* command. Just copy and paste the commands you used back to this thread between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

In general, ftp directories should not be given root ownership. Moreover, for security reasons, the permissions (which are a different thing) must be set very carefully. You can show us the ownership and permission structure of any directory including all the subdirectories and files it contains with the command:```
ls -laH /name/of/directory
```Even better is to assign a full partition to nothing but ftp access, give it the proper ownership and permissions, and then confine ftp access to *only* that partition.

Perhaps it is best to start over with help from some of the experts on this forum. It has been a long time since I've set up FTP, so I am of limited help. But others here are very knowledgeable and can give you good guidance, especially on best practices. In any case, they will need the info that I've asked you for.

---

### Post by lochness123 on 2017-02-03
I followed instruction from this videos:[VSFTPD video]([https://www.youtube.com/watch?v=SiiFFy1M4jU&t=492s](https://www.youtube.com/watch?v=SiiFFy1M4jU&t=492s)) and [Root permissions video]([https://www.youtube.com/watch?v=uDhZOy1DrDo](https://www.youtube.com/watch?v=uDhZOy1DrDo)). In attachment I send the screenshots of my history commands. It would by best if you help me set the VSFTPD from beginning. Can you help me please?

---

### Post by HermanAB on 2017-02-03
Err... in my experience,vsftpd works out of the box.  You install it and it works.  Nothing to it.

---

### Post by steeldriver on 2017-02-03
Please post the results of

```

sudo netstat -nlpt

sudo ufw status verbose

```

It looks like you enabled ufw with a default rule to deny incoming connections - and didn't then open any port(s)

---

### Post by lochness123 on 2017-02-03
There are results in attachment.

---

