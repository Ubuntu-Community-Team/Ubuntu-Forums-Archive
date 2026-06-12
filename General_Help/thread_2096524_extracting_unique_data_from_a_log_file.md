---
title: "extracting unique data from a log file"
date: 2012-12-20
forum: General Help
---

### Post by cbillson on 2012-12-20
Hi, have a need to identify and extract some data from a log file. the file logs multiple threads but each has an ID. I'd like to get a list of the unique thread ID's.

I presume i need to create some form of 'for' loop, and can construct the command fairly easily to look for each line that contains thread(12345) and act upon that as a variable, but not sure how to drop it if i've already 'seen' it.

Any help or thoughts gratefully received.

Cheers
Chris

---

### Post by The Cog on 2012-12-20
If all you want is the thread id numbers, I would probably use 
cut | sort | uniq 
with appropriate arguments to cut so that it picks out the thread ids. Without a sample line I can't be sure how to do that, but something like this perhaps:
```
cut -f 1 *.log | sort | uniq
```

---

### Post by cbillson on 2012-12-20
Awsome!! thanks

the data is in the format

10/08-13:02:32.830  WARN   Thread[Thread-12345,1,main] some data

---

### Post by btindie on 2012-12-20
Something like this should do what you need
```
cat log | sed -e 's/^.*\[//;s/\].*$//' | sort -u
```

If you also want to know how many of each thread there were use
```
cat log | sed -e 's/^.*\[//;s/\].*$//' | sort | uniq -c
```

It just removes everything before and after the [ ] brackets.

---

### Post by cbillson on 2012-12-20
> **btindie said:**
> Something like this should do what you need
```
cat log | sed -e 's/^.*\[//;s/\].*$//' | sort -u
```If you also want to know how many of each thread there were use
```
cat log | sed -e 's/^.*\[//;s/\].*$//' | sort | uniq -c
```It just removes everything before and after the [ ] brackets.

Thanks very much, though it appears to cut too much, this appears to return the portion 'some data'

at this stage i'd like to be able to extract and list just the unique thread numbers - ie:

12345
12346
12348
etc

---

### Post by cbillson on 2012-12-20
> **cbillson said:**
> Thanks very much, though it appears to cut too much, this appears to return the portion 'some data'

at this stage i'd like to be able to extract and list just the unique thread numbers - ie:

12345
12346
12348
etc

cant delete this reply :(

---

### Post by steeldriver on 2012-12-20
something like this maybe?

```
sed -rn 's/.*Thread-([0-9]+).*/\1/p'
``````
$ echo "10/08-13:02:32.830 WARN Thread[Thread-12345,1,main] some data" | sed -rn 's/.*Thread-([0-9]+).*/\1/p'
12345

```

then sort -u obviously

---

### Post by cbillson on 2012-12-20
> **steeldriver said:**
> something like this maybe?

```
sed -rn 's/.*Thread-([0-9]+).*/\1/p'
``````
$ echo "10/08-13:02:32.830 WARN Thread[Thread-12345,1,main] some data" | sed -rn 's/.*Thread-([0-9]+).*/\1/p'
12345

```then sort -u obviously


Fantastic!! thank-you all very much. each reply has given me guidance for the next steps with this data, really grateful.

---

