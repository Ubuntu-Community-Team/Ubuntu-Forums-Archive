---
title: "Can't run Firefox Beta 2 RC1?"
date: 2006-08-22
forum: General Help
---

### Post by Rackerz on 2006-08-22
darren@darren-desktop:~$ cd ~/Desktop/firefox
darren@darren-desktop:~/Desktop/firefox$ sh run-mozilla.sh

run-mozilla.sh: Cannot execute .

I get this error when trying to run it, nothing else so I don't know if this is helpful at all.

---

### Post by mostwanted on 2006-08-22
You have to make the file executable:

[IMG]http://monkeyblog.org/ubuntu/videos/Changing_permissions.gif[/IMG]

---

### Post by Rackerz on 2006-08-22
Thanks but it still doesn't work.

---

### Post by yopnono on 2006-08-22
> **Rackerz said:**
> darren@darren-desktop:~$ cd ~/Desktop/firefox
darren@darren-desktop:~/Desktop/firefox$ sh run-mozilla.sh

run-mozilla.sh: Cannot execute .

I get this error when trying to run it, nothing else so I don't know if this is helpful at all.

You are not suppose to run the run-mozilla script, you should use the firefox script.

---

### Post by Rackerz on 2006-08-22
> **yopnono said:**
> You are not suppose to run the run-mozilla script, you should use the firefox script.

How do I run that script then? If I try sh firefox.sh it says it cannot find it. If I try sh firefox it launches the default FF.

---

### Post by yopnono on 2006-08-22
Use the path to the fx script you like to execute.
Or just open the folder and double-click the fx script

---

### Post by mostwanted on 2006-08-23
> **Rackerz said:**
> How do I run that script then? If I try sh firefox.sh it says it cannot find it. If I try sh firefox it launches the default FF.

It's not called firefox.sh, just [COLOR="Red"]firefox[/COLOR].

---

