---
title: "i want to run transmission automated"
date: 2008-06-30
forum: General Help
---

### Post by s.jesudasan on 2008-06-30
hi 
im unable to run transmission using crontab
i tried to run a small script which i created and 
it was successful but when i tried to run transmission or rhythmbox 
i didnt get it running
here is my crontab file
# m h  dom mon dow   command
39 * * * * nohup /usr/bin/transmission -m > stal.txt

kindly help me
thanks

---

### Post by sdennie on 2008-06-30
Try something like:

```

39 * * * * DISPLAY=:0.0 su your_username -c "nohup /usr/bin/transmission -m > /home/your_username/stal.txt"

```

Replace the two "your_username" with the name of the user you want to run transmission as.

---

### Post by s.jesudasan on 2008-07-01
bro it didnt work
did this command work on your ubuntu

---

### Post by sdennie on 2008-07-02
Sorry, the su isn't needed:

```

39 * * * * DISPLAY=:0.0 nohup /usr/bin/transmission -m > /home/your_username/stal.txt

```

---

### Post by kpkeerthi on 2008-07-02
You need an 'export' keyword before DISPLAY=:0.
See [http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)

---

### Post by sdennie on 2008-07-02
> **kpkeerthi said:**
> You need an 'export' keyword before DISPLAY=:0.
See [http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)

I don't think it's strictly needed unless you want child shells to inherit the DISPLAY variable.  I did a crontab -e and put the following in and it worked just fine:

```

32 * * * * DISPLAY=:0.0 nohup /usr/bin/gcalctool

```

Still, the export doesn't hurt I suppose.

---

### Post by s.jesudasan on 2008-07-02
for me this comman works just fine

48 * * * * export DISPLAY=:0 && /usr/bin/transmission > /home/stalin/newtran.txt

vor and keerthi thanks a lot for ur help

---

