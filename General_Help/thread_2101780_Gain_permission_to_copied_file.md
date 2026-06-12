---
title: "Gain permission to copied file"
date: 2013-01-05
forum: General Help
---

### Post by seacher on 2013-01-05
I copied a file yesterday and when trying to access it through the command line I find out I can't gain access to it.

The file path is '/usr/share/Surge-View' and when I reach '/share' I get the message:

'bash: cd: /share: No such file or directory'

I need this to interface with the Wireless Sensor Network I use for research.

---

### Post by t0p on 2013-01-05
Put these commands into a terminal and post output:

```
cd /usr
``````
ls
```**EDIT:** Re-reading your post, it looks like you are trying to access a directory called /share (which does not exist), whereas you should be accessing directory called /usr/share.  So command should be

```
cd /usr/share
```

---

### Post by 2F4U on 2013-01-05
There is a difference between 

/usr/share

and 

/share

If you enter /share, it is assumed that it is located under the root filesystem (/), while your post suggests it is a subfolder of /usr.

---

### Post by seacher on 2013-01-05
Thanks guys! 

That helped!

---

