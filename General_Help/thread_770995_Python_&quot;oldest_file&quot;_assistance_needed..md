---
title: "Python &quot;oldest file&quot; assistance needed."
date: 2008-04-27
forum: General Help
---

### Post by chrismyers on 2008-04-27
Hi guys,

I'm new to programming Python. Despite some effort, I am having trouble working out how I pick out the oldest modified file in a directory.

This is what I have so far:

```
#!/usr/bin/python
import os, time
 
watch_path = "/home/chris/pytest"
wait_time = 5
 
while not sum((len(f) for _, _, f in os.walk(watch_path))):
    print 'No Files present in "' + (watch_path) + '". Checking again in %s' % (wait_time) + ' seconds...'
    time.sleep(wait_time)
else: 
    print 'Files present' 
```The above code checks for the existence of file in the directory. I then need to move the oldest modified file into another folder, before working on it.

I am aware that I can check an individual file modification age with:
```
statinfo = os.stat('somefile.txt')
print statinfo.st_mtime
```How do I use this command to select & move the oldest file in this directory?

Many thanks in advance.

---

### Post by ryanhaigh on 2008-04-28
Maybe something like 

```

import os
oldest = ''
oldestAge = 0

for file in os.listdir('.'):
	age = os.stat(file).st_mtime
	if age > oldestAge:
		oldestAge = age
		oldest = file
print oldest

```

I don't know what the st_mtime is but I assume its an integer that is larger for older files.

---

### Post by chrismyers on 2008-04-29
Many Thanks ryanhaigh.

I had to make some small modification, but this is the result:

```
#!/usr/bin/python
import os, time
 
watch_path = "/home/chris/"
wait_time = 60
 
while not sum((len(f) for _, _, f in os.walk(watch_path))):
    print 'No Files present in "' + (watch_path) + '". Checking again in %s' % (wait_time) + ' seconds...'
    time.sleep(wait_time)
else: 
    print 'Files present' 

oldest = ''
oldestAge = 0

for file in os.listdir(watch_path):
    age = os.stat(watch_path + file).st_mtime
    if age > oldestAge:
        oldestAge = age
         oldest = file
print oldest
```Now, instead of printing the file, I can do anything I like with it.

Again, many thanks. :)

---

