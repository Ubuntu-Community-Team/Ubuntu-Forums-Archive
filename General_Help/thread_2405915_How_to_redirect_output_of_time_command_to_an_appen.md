---
title: "How to redirect output of time command to an appended file?"
date: 2018-11-13
forum: General Help
---

### Post by suaro on 2018-11-13
I would like to take the output produced by time command and place it into a file - but can't seem to find a way to do this. 
Its driving me nuts :)

For example if I want to find out how long it takes to execute the ls command I do this : 

```
# time ls -l
total 0
-rw-r--r-- 1 root root 0 Nov 13 09:44 file1.log
real    0m0.003s
user    0m0.002s
sys     0m0.000s
```


I've tried many variations of sending stderr and output to a file such as 

```
time ls -l >stdout 2>stderr
time ls -l > /tmp/log/allout.log 2<&1
time ls -l > test.log 2>&1
```

(some of the above are plain silly ) , but in most cases where output is produced,  it only shows the output of ls command. 

I'm trying to get the time output logged to a file (in bold above ) .  I realize there is an -o FILE option and even a way to format the output, but it should be possible I would think to get the bold part above into a file ?  

Ideally the time command would be called periodically (like every 15 seconds), so the output would need to be appended to an existing file. 

Having a growing log with something like this (output of time for the given command )  :

```
-rw-r--r-- 1 root root 0 Nov 13 09:44 file1.log
[FONT=lucida console]real    0m0.003s
user    0m0.002s
sys     0m0.000s

-rw-r--r-- 1 root root 0 Nov 13 09:44 file1.logreal    0m0.002s
user    0m0.002s
sys     0m0.000s

-rw-r--r-- 1 root root 0 Nov 13 09:44 file1.log
real    0m0.002s
user    0m0.000s
sys     0m0.002s
```


Heck , I'd even be satisfied if the output of the command being timed (in this case ls -l ) is not in the log. 


Any tips greatly appreciated. 
Thank you so much!

---

### Post by slickymaster on 2018-11-13
See this [https://stackoverflow.com/questions/2408981/how-can-i-redirect-the-output-of-the-time-command](https://stackoverflow.com/questions/2408981/how-can-i-redirect-the-output-of-the-time-command)

---

### Post by HermanAB on 2018-11-13
Hmm...
```
$ date > file; ls >> file; date >> file
```

---

### Post by suaro on 2018-11-13
Thanks slickymaster.  This is exactly what I needed. 

```
(time ls -l) &>> output1.log
```

---

