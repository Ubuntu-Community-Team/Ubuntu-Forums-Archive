---
title: "help with file paths"
date: 2014-02-13
forum: General Help
---

### Post by mike146 on 2014-02-13
Hi
I am new to ubuntu server but really enjoying it. I am running it on a VirtualBox VM from a Vista machine if that matters. My question is basically, I have a python script in "var/www/python" that is supposed to create a xml file in the same python directory. It works fine on my Mac OS machine (with a directory specific to that machine) but not on this one. I'm guessing its my path used within the file? If so, what would the correct path be? here is the terminal output containing the path I used (see "fo"):

[FONT=Menlo]apps@ubuntu:/$ python /var/www/python/staggered2.py[/FONT]
[FONT=Menlo]Traceback (most recent call last):[/FONT]
[FONT=Menlo]  File "/var/www/python/staggered2.py", line 26, in <module>[/FONT]
[FONT=Menlo]    fo = open("var/www/python/DiaChannelDataFull.xml", "w")[/FONT]
[FONT=Menlo]IOError: [Errno 13] Permission denied: 'var/www/python/DiaChannelDataFull.xml'
[/FONT]
Any guidance would be appreciated. Thanks
Mike

---

### Post by howefield on 2014-02-13
Try preceding the command with sudo eg,

```
sudo python /var/www/python/staggered2.py
```

---

### Post by mike146 on 2014-02-13
That did it. I should have tried that prior to posting. never thought of it. Ugh. Anyway, thank you thank you. You saved me an hour of frustration trying different paths.

---

