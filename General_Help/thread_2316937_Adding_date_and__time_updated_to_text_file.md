---
title: "Adding date and  time updated to text file"
date: 2016-03-12
forum: General Help
---

### Post by GrouchyGaijin on 2016-03-12
Hi Guys,

I have a script running as a cron job that sorts the data in one text file and then sends the sorted data to another text file.

```
cat /home/john/Dropbox/todo/todo.txt | sort --field-separator=: -k 2 > ~/Dropbox/todo/"Todo by Due Date".txt
```

My question is how can I append the date and time updated to the end of the  Todo by Due Date file without overwriting all of the contents of that file or having multiple update times listed?

If I use:
```
UPDATE=$(date +"%F at %T")echo $UPDATE > ~/Dropbox/todo/"Todo by Due Date".txt



```

The contents of the file are overwritten.  If I ue >> I will end up with multiple update dates and times.

---

### Post by GrouchyGaijin on 2016-03-12
I found it - should have Googled first.

```

UPDATE=$(date +"%F at %T")
echo Last updated on $UPDATE > ~/Dropbox/todo/update_time.txt
cat /home/john/Dropbox/todo/todo.txt | sort --field-separator=: -k 2 > /home/john/Dropbox/todo/"Todo by Due Date".txt
cat /home/john/Dropbox/todo/update_time.txt /home/john/Dropbox/todo/"Todo by Due Date".txt > /home/john/Dropbox/todo/"Updated List.txt"


```

---

