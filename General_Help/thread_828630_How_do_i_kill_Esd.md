---
title: "How do i kill Esd?"
date: 2008-06-13
forum: General Help
---

### Post by morbid_bean on 2008-06-13
I was told to kill esd to fix a problem...how is this done?

---

### Post by ibutho on 2008-06-13
Try
```
ps aux | grep -i esd
```
From the results, the process number is the first number shown after the username and thats what you use to kill the process e.g. is the process number is 1111, you would do
```
kill 1111
```
If that fails try
```
sudo killall esd
```

---

