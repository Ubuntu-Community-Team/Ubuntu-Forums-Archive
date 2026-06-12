---
title: "NTP client update"
date: 2005-08-10
forum: General Help
---

### Post by diNunes on 2005-08-10
Hi,  i'm doing a project which consists in a comparative of several aplications which generate and analise network traffic.

I´m using a ntp server located at my school (local server)! The thing is, I need to syncronize both PC´s at every 500 ms for example!

I´m already using ntpdate to synchronize the PC's but this only syncronize when I type the command ntp -u IP  :???: 

I would like to know if any of you know any aplication that allows the costumization of the syncronization rate!

Sorry for my english!

TIA  ;-)

---

### Post by fng on 2005-08-10
maybe you could use a crontab for this?
```
crontab -e
```
Now fill-in this :
```
* * * * * ntp -u IP > /dev/null
```
exit the editor

It will sync with the given IP every second

---

### Post by diNunes on 2005-08-10
I openned the file  /etc/crontab and added this line a the end of file

```
1 * * * * 	root    ntpdate -u 192.168.100.1
``` 

But it seems that's not working  :(

How do I know it's running?

Do I need to do something else?

Thanks for your response!

---

### Post by kirsche on 2005-09-07
try to start the ntpdate with the -d switch from a terminal. it should give you an error message.

---

