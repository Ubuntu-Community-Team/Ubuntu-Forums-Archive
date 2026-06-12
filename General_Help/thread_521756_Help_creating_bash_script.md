---
title: "Help creating bash script"
date: 2007-08-09
forum: General Help
---

### Post by hamstersquasher on 2007-08-09
I have a DSL line with a dymanic IP and want to email my gmail account a notification every time my IP address changes.  ( I do a lot of remote work to my home computer at work).  I don't have much started but basically I know i can use the "wget www.whatismyip.com" to get the index.html.  This includes the outsite IP address in the "<title></title>"  section.  I can then compare that to a previous download using wget with the "diff" command.  after that I know I need to be able to parse the file somehow and then email the address.  I have mutt installed currently but may move to pine instead since I have used it more.  Any help on this would be awesome.

---

### Post by ross9885 on 2007-08-10
I just tried writing a shell script to make alpine mail me but it didn't work. When I put 'ctrl-x, y' in the end of a here document to make Alpine send the email, it inserted it into the text instead of respecting my authoritee.
However, I see there is a perl tutorial for sending text with sendmail at [http://www.willmaster.com/possibilities/archives/wmp20020709001.shtml]("http://www.willmaster.com/possibilities/archives/wmp20020709001.shtml")

---

### Post by UltraMathMan on 2007-08-11
You could do something like ```
#!/bin/bash
rm index.html
wget www.whatismyip.com
myip=$(grep WhatIsMyIP.com\ - index.html)
```


Then find out how to use sendmail, mailx, or some other cli mail program to send $myip to your email address.

---

### Post by hamstersquasher on 2007-08-23
thanks for the leads!!

---

### Post by UltraMathMan on 2007-08-23
no problem - happy scripting!

---

### Post by jusmurph on 2007-08-23
ley us know what you come up with... this is very interesting

---

