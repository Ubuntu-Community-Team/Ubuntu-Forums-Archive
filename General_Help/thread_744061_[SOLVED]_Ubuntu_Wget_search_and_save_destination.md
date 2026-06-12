---
title: "[SOLVED] Ubuntu Wget search and save destination"
date: 2008-04-03
forum: General Help
---

### Post by Rytron on 2008-04-03
Hi,
How could I download a file using wget in Ubuntu and specify where to save the file. Is the file saved to a certain location by default?

for example I want to download something so I would need to:

```
wget [URL LINK]
```

Is the above correct?

Now I want to download that file to my desktop.

How would I do this?

Thanks.

---

### Post by sekinto on 2008-04-03
Actually you would do it like this:
```

cd /home/USER/Desktop
wget YOURFILE

```
Or if you like one liners:
```
cd /home/USER/Desktop && wget YOURFILE
```

---

### Post by ghostdog74 on 2008-04-03
use wget to get a web page

---

### Post by justleen on 2008-04-03
you can use the -O option on wget to specify the output. No need to use cd fist
```

wget http://whatever.com/index.html -O /home/Desktop/clickme.html

```

---

### Post by cdenley on 2008-04-03
Or if you wanted to download and grep file
```

wget http://ubuntuforums.org/showthread.php?p=4643780 -q -O -|grep Rytron

```

---

