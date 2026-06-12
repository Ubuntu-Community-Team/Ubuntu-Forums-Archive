---
title: "Retrieving a &quot;lost&quot; process"
date: 2007-06-10
forum: General Help
---

### Post by dboyd13 on 2007-06-10
Hi,

I started a wget process from an SSH session, then I disconnected from the SSH session.

This process is still running in the background, and confirmed that the download is still continuing:

Here is an example output from ps ax
```
6697 ?        S      0:01 wget http://www.blabla.net/download/myfile.gz
```

Is there any way that I can retrieve this process and display it's output (i.e. download status) back into a terminal/TTY?

Thanks.

---

### Post by DagMan on 2007-06-10
I really don't know the answer but couldn't resist the temptation to point out the screen program.  Perhaps you already use it.  If not, once installed on the computer acting as the server it will let you reatach to the terminal that something was running in when you lose your connection.
sudo apt-get install screen ,if you don't already have it.

---

### Post by reclusivemonkey on 2007-06-10
```
fg wget
```

Should do it.

---

### Post by dboyd13 on 2007-06-10
Thanks for the advise so far...

1. @DagMan: I will give screen a try, but was really hoping that there was a "native" solution.
2. @reclusivemonkey: 

But if I terminate send CTRL-Z to wget within the SSH session, I am able to recover the output with the "fg wget" command you suggested, only when i'm within that SSH session

if I issue that command from another session, after terminating the SSH session, I get the following error:

```
fg wget
bash: fg: wget: no such job

```

Any ideas?

---

### Post by reclusivemonkey on 2007-06-10
> **dboyd13 said:**
> 
2. @reclusivemonkey: 

But if I terminate send CTRL-Z to wget within the SSH session, I am able to recover the output with the "fg wget" command you suggested, only when i'm within that SSH session

if I issue that command from another session, after terminating the SSH session, I get the following error:

```
fg wget
bash: fg: wget: no such job

```

Any ideas?

Yes; you need to use screen, as the other poster suggested.  Screen is the "native" solution.  If you log out from your SSH session, you will lose wget.

---

### Post by dboyd13 on 2007-06-11
Thanks for the advise. I will do some research on "screen". Hopefully it will do the trick. Cheers.

---

