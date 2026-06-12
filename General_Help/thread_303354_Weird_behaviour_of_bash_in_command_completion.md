---
title: "Weird behaviour of bash in command completion"
date: 2006-11-20
forum: General Help
---

### Post by jamadagni on 2006-11-20
First I do this:

```
samjnaa@chandas:~/bf/test$ ls
samjnaa@chandas:~/bf/test$ mkdir abc
samjnaa@chandas:~/bf/test$ touch abc.def
samjnaa@chandas:~/bf/test$ ls -l
total 0
drwxr-xr-x 2 samjnaa samjnaa 48 2006-11-19 19:27 abc
-rw-r--r-- 1 samjnaa samjnaa  0 2006-11-19 19:27 abc.def
```

Now typing "cd a" and pressing tab, I get:

```
samjnaa@chandas:~/bf/test$ cd abc/
```

At this I hit Ctrl+C. Now watch this:

```
samjnaa@chandas:~/bf/test$ sudo -i
root@chandas:~# cd /home/samjnaa/bf/test/
```

Now "cd a" + TAB gives:

```
root@chandas:/home/samjnaa/bf/test# cd abc
```

How come the / is not filled in this time?

Anyway, again I hit Ctrl+C. Now observe further:

```
root@chandas:/home/samjnaa/bf/test# rm abc.def
```

Again "cd a" + TAB gives:

```
root@chandas:/home/samjnaa/bf/test# cd abc/
```

Weird. Whether abc.def exists or not, the only valid input for the cd command is the abc directory. Observe the following weirder example, executed in the same pattern as above after a rm -R * :

```
samjnaa@chandas:~/bf/test$ ls
samjnaa@chandas:~/bf/test$ mkdir abc123
samjnaa@chandas:~/bf/test$ touch abc123.def
samjnaa@chandas:~/bf/test$ touch abc.def
samjnaa@chandas:~/bf/test$ cd abc123/
samjnaa@chandas:~/bf/test$ sudo -i
root@chandas:~# cd /home/samjnaa/bf/test/
root@chandas:/home/samjnaa/bf/test# cd abc
root@chandas:/home/samjnaa/bf/test# rm *.def
root@chandas:/home/samjnaa/bf/test# cd abc123/
```

Could this actually be a bash bug?

Shriramana Sharma.

---

### Post by krismatth3 on 2006-11-20
It's because different auto completetion parameters are set up for root and your user. 

Add a new user and try it with two different users. Or search the man page for auto completetion options, I'm too lazy to look it up. :)

---

