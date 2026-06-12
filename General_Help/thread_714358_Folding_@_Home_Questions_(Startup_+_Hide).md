---
title: "Folding @ Home Questions (Startup + Hide)"
date: 2008-03-03
forum: General Help
---

### Post by dethredic on 2008-03-03
Ok, I have some extra CPU power and ram, and I want to fold!

Is there an easy way to make it run at startup. I always have to use 2 commands, and that doesn't work in the startup area. (The CD /home/phil/folding, and the ./FHA504.exe)

Also, can I make the folding window hidden, and not appear anywhere, cause I always accidentally close it.

---

### Post by chewearn on 2008-03-04
You can create a bash script "fah.sh":
```

cat > fah.sh << EOF
#!/bin/bash
cd /home/phil/folding
./FAH504.exe
EOF
```Make the script executable:
```
chmod +x fah.sh
```Add the script to the session start-up list.

---

### Post by dethredic on 2008-03-04
how would I add it? What is the terminal command to run it?

---

### Post by chewearn on 2008-03-04
To add a command to the start-up list, go to:
Top Panel Menu > Preferences > Sessions > Click Add.

Browse to select the file "fah.sh", which you have just created.

---

### Post by dethredic on 2008-03-04
great thanks!

---

### Post by dethredic on 2008-03-05
alright, I think it is working (If the .sh file hides it)
Is there any way to test?

---

### Post by chewearn on 2008-03-05
Check the System Monitor,  the fahcore process should be using almost 100% CPU.  You can also open "FAHlog.txt" in your folding directory; it will show the log of the current fold.

---

### Post by dethredic on 2008-03-05
Great. Thanks for the help man.

---

