---
title: "[SOLVED] Setting path in Bash"
date: 2008-07-01
forum: General Help
---

### Post by theravenproject on 2008-07-01
Hello, I am working my way around Ubuntu rather well now but recently I have gotten into using the bash shell a lot more intimately...according to the linux Bible 2008 when you enter 
```
thepheonixproject@thepheonixproject:$ echo $path 
```

It should tell you what the pathname is currently set to,,,this does not work and neither does any of the other "Path" directions... I searched for this topic here without success (Although I have been known to err in my searches) so can anyone please point me to where I can find  complete information related to Setting The path in The BASH shell?  Thank you for any and all responses!

---

### Post by sisco311 on 2008-07-01
try:
```
echo $PATH
```

---

### Post by shad0w_walker on 2008-07-01
Linux is case sensitive, so $path is completely seperate from $PATH. Simple little thing that gets most people when they start out.

---

### Post by theravenproject on 2008-07-01
Thanks guys...okay so I have that part down...now any suggestions on what the path variable should be set to as a default or what is normal?  The example given me by the book is

```
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/ucb
```

and mie is currently set to:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Pretty similar except for the /usr/ucb to /usr/games difference?  Please advise

---

### Post by Titan8990 on 2008-07-01
Your path varies by distro. For example Fedora doesnt contain /usr/sbin by default. What you have there is perfectly fine.

---

### Post by VMC on 2008-07-01
Also to see the options for "bash", default Terminal shell, do this from Terminal:

```
cat ~/.bashrc
```

or

```
gedit ~/.bashrc
```

---

