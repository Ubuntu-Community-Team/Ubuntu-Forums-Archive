---
title: "Bash error (amateur)"
date: 2012-12-20
forum: General Help
---

### Post by lsutiger on 2012-12-20
I have a small script where I am receiving an "No such file or directory" error. I have attached two screen shots. The first one shows the directory listing with the script highlighted, and shows permissions. Next it shows when I try to run it (I tried with ",/" and without, even though I should not need it). Next it shows the script with a cat.
The next screen shot shows  each line of the script in the CLI, which works.

What am I missing here?

Thanks in advance!

---

### Post by cortman on 2012-12-20
Well, let's cover the basics first: You did set its permissions to executable, correct?

```
chmod +x script_name
```

If it's already located in ~/bin and your $PATH has been updated you shouldn't need the ./ to run it.

---

### Post by lsutiger on 2012-12-20
Ok, I changed interpreter line (which I shouldn't have to) from #!/bin/sh to #!/bin/bash and now I am receiving the following error:
"bash: /home/brian/bin/orderprn.sh: /bin/bash^M: bad interpreter: No such file or directory"

---

### Post by cortman on 2012-12-20
What editor are you using to type the script?

---

### Post by lsutiger on 2012-12-20
nano

---

### Post by fdrake on 2012-12-20
can you please just copy and paste the script betwwen the <code> tags in your post.

also when you exit cat to save the document you have to press <ctrl>+<d> keys.

---

### Post by lsutiger on 2012-12-20
```
#!/bin/bash
shopt -s nullglob
cd /home/brian/orders
for f in *.prn
do
echo "working on $f"
FILENAME=$f
STR=$(echo `expr index "$FILENAME" "."`)
done
exit

```

---

### Post by fdrake on 2012-12-20
copy this command on your terminal:
```

echo "\#!/bin/bash" >> ~/bin/myscript.sh
echo "shopt -s nullglob" >> ~/bin/myscript.sh
echo "cd /home/brian/orders" >> ~/bin/myscript.sh
echo "for f in *.prn" >> ~/bin/myscript.sh
echo "do" >> ~/bin/myscript.sh
echo "echo \"working on \$f\"" >> ~/bin/myscript.sh
echo "FILENAME=\$f" >> ~/bin/myscript.sh
echo "STR=\$(echo \`expr index \"\$FILENAME\" \".\"\`)" >> ~/bin/myscript.sh
echo "done" >> ~/bin/myscript.sh
echo "exit" >> ~/bin/myscript.sh
chmod +x ~/bin/myscript.sh
~/bin/myscript.sh

```


why don't you just use gedit also ....

---

### Post by lsutiger on 2012-12-20
Opened with vi...had a special character in there "^M". Removed and works now!

---

### Post by fdrake on 2012-12-20
> **lsutiger said:**
> Opened with vi...had a special character in there "^M". Removed and works now!

vi and and nano are old editor. try to use vim is much more used nodays. also if you want something more userfriendly i suggest you bluefish and gedit.

---

### Post by cortman on 2012-12-21
> **lsutiger said:**
> Opened with vi...had a special character in there "^M". Removed and works now!

Sorry I'm late in coming, but it seems to be fixed now.
That special character was why I wondered what editor you were using. It's a newline character, I believe vi inserts it.
Glad it's solved!

---

