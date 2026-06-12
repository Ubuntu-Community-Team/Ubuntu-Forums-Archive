---
title: "[SOLVED] script help"
date: 2007-11-27
forum: General Help
---

### Post by offline on 2007-11-27
```
# Cleanup
# Run as root, of course.
cd /var/log
cat /dev/null > messages
cat /dev/null > wtmp
echo "Logs cleaned up."
```

This is the... first script from the well known ~800 page ABS-Guide from Mendel Cooper(online) and says it cleans the logs. 
and I am already really stuck...
I can't understand how it works?
Why change dir to var/log  if you are going to write to a file called messages(??) from /dev/null. And why you again do this to some wtmp(?). Or, are they commands and not files?
 Can someone explain this to me

---

### Post by PeterJS on 2007-11-27
They are relative paths, specifying the files name messages and wtmp in the current directory. So the cd at the beginning is to put you in to /var/log where the files reside.

You could also do:
```

cat /dev/null > /var/log/messages
cat /dev/null > /var/log/wtmp
echo "Logs cleaned up."

```But I think the point of the cd and the relative path name is to demonstrate how those ideas work in scripts.

---

### Post by offline on 2007-11-27
> **PeterJS said:**
> They are relative paths, specifying the files name messages and wtmp in the current directory. So the cd at the beginning is to put you in to /var/log where the files reside.

You could also do:
```

cat /dev/null > /var/log/messages
cat /dev/null > /var/log/wtmp
echo "Logs cleaned up."

```But I think the point of the cd and the relative path name is to demonstrate how those ideas work in scripts.

1)So this null file is full of "zeros" and copying it to those two files erases their content? 
2)Why clean this mysterious wtmp and the messages file and not *.log

Thanks for the reply.

---

### Post by PeterJS on 2007-11-27
> **offline said:**
> 1)So this null file is full of "zeros" and copying it to those two files erases their content? 

/dev/null is a special device block device that contains nothing, so you can read infinite amounts of nothing out of it, or write infinite amount of extraneous data to, like output from programs you don't care about, with little (no?) overhead. You're familiar with the concept of null, right? It's a file full of null.
And it's not copying, it's reading there contents with cat, and then using the shell to redirect cat's output in to the files. For this example it functions like copying, but conceptually is much different.

> 
2)Why clean this mysterious wtmp and the messages file and not *.log
There are no .log files, everything in /var/log/ is assumed to be a log file so there's really no reason to put an extension on the files.

/var/log/messages is the log file of kernel messages
and
/var/log/wtmp appears to be some sort of cache, but I can't make heads or tails of that much binary data with out some hint has to the way it's supposed to be interpreted.

---

