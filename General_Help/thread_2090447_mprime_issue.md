---
title: "mprime issue?"
date: 2012-12-02
forum: General Help
---

### Post by -RYknow on 2012-12-02
So, I've used Mprime on numerous occasions in the past, and I've never had an issue. It has been awhile, so maybe I'm doing something wrong? I just can't seem to get it to run. I must be typing a command wrong?

- I used the link in this thread to get the tarball. [Here]("http://ubuntuforums.org/showthread.php?t=1337958")

- Then I extracted the contents to a folder called "mprime" on my desktop. 

And here is what I'm getting; 

```
ryknow@ryknow-Server:~$ cd ~/Desktop/mprime
ryknow@ryknow-Server:~/Desktop/mprime$ ./mprime
bash: ./mprime: No such file or directory
ryknow@ryknow-Server:~/Desktop/mprime$ 
```

I feel like I'm just doing something stupid. Hopefully someone here can make me feel like an idiot, and help me! :rolleyes:

Thanks, 
-RYknow

---

### Post by Cheesemill on 2012-12-02
What's the output of:
```
ls -lha ~/Desktop/mprime
```Edit - 

I've just had a look at the thread you've linked to and it's pointing to an old version of mprime.
For the latest release check out [http://www.mersenne.org/freesoft/](http://www.mersenne.org/freesoft/)

At a guess your problem is caused by trying to run a 32-bit version of mprime on a 64-bit system, try the download on the page I linked to and see if it makes a difference.

---

### Post by -RYknow on 2012-12-02
I realized it was an older version. I downloaded the newer version and it ran fine. 

Thanks, 
-RYknow

---

