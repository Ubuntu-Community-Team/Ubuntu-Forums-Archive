---
title: "Grep and Sed help!"
date: 2013-07-10
forum: General Help
---

### Post by Fenlig on 2013-07-10
Hey guys,

So I have a log file like this:

2013-07-10 21:40:54 [INFO] Janus_Mesca joined the game
2013-07-10 21:40:54 [INFO] Fenlig joined the game
2013-07-10 21:41:21 [INFO] BigRedHoodie joined the game


And I'm trying just to return what ever appears in between the "[INFO]" and the "joined".

With my attempts I've only been able to remove the two words themselves.

tail -500 $rfile | grep "INFO.*joined the game" | sed -e 's/\[INFO\]\(.*\)joined/\1/'

Any help?

---

### Post by sciguy125 on 2013-07-10
```
sed -e 's/\(^.*\[INFO\] \)\(.*\)\( joined the game$\)/\2/'
```

I broke the line into three parts:
1. ...[INFO]
2. the names
3. " joined the game"
 
Then, I told it to replace the entire line with the second part (the "\2").  I think awk would be more appropriate and "easier", but you asked about sed and I'm more of sed person myself.

---

### Post by papibe on 2013-07-10
Hi Fenlig.

This is an alternative using awk. 
```
awk '/INFO.*joined/ {print $4}' file.txt
```
Or, if the file has that exact format all from top to down, you can use this:
```
awk '{print $4}' file.txt
```
Let us know how how it goes.
Regards.

---

### Post by VMC on 2013-07-10
Another way to skin the cat:

```
cut -d" " -f4 <file>
```

---

