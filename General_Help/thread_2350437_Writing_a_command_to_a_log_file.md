---
title: "Writing a command to a log file"
date: 2017-01-24
forum: General Help
---

### Post by SchnappiJedi on 2017-01-24
Is it possible to write a command to a specific log file? For example say that want to log the command below to a certain file:

```
cp -pruv /source /destiantion
```

What would need to be added in order to log the results to a file?

---

### Post by SchnappiJedi on 2017-01-24
Is it possible to write a command to a specific log file? For example say that want to log the command below to a certain file:

```
cp -pruv /source /destiantion
```

What would need to be added in order to log the results to a file?

---

### Post by ajgreeny on 2017-01-24
```
cp -pruv /source /destination > filename
```will do it for any command that has output; you just add > filename after the command and the terminal output is put into a file.

You can append the next instance of the output by changing the > to >>.

Incidentally I have an alias for cp which means I always run the equivalent of **cp -aiv** whenever I use **cp**.

---

### Post by SeijiSensei on 2017-01-24
In general you can pipe the output of a command to a file with
```
command > /path/to/file
```

If you use ">>" instead, the output is appended to an existing file.

Some program outputs go to the "syserr" device.  To capture those as well use

```
command > /path/to/file 2>&1
```

---

### Post by howefield on 2017-01-24
Does appending 

```
> test.txt
```

do what you want ? That would log a file called test.txt to your /home folder.

A double angle bracket would append the output to an already existing file.

---

### Post by howefield on 2017-01-24
Threads merged.

---

### Post by SchnappiJedi on 2017-01-24
The forum was done when entered post and next looked there are about five different threads. Please delete or merge.

---

### Post by howefield on 2017-01-24
> **SchnappiJedi said:**
> The forum was done when entered post and next looked there are about five different threads. Please delete or merge.

Taken care of and apologies for the misfiring server(s).

---

