---
title: "RAM conservation and process reduction"
date: 2013-10-02
forum: General Help
---

### Post by hiig on 2013-10-02
I have a machine dedicated to only one function, but the machine lacks RAM, and I've ruled down a small performance issue to a lack of RAM. I run ubuntu-server, and the only things I had to apt-get was ia32libs and mono for another program that uses the internet. Other than that, I don't use anything else on it. What processes can I safely disable, and/or completely uninstall, without negatively affecting the running of my system?

If I need to post a list of my processes, how can I do it via terminal?

---

### Post by ajgreeny on 2013-10-02
The command **ps** will show processes and you can make a text file of a list if needed with** ps -e > processes.txt**

See **man ps** for details.

---

### Post by hiig on 2013-10-02
Once I've made the file, how can I upload it from the terminal?

---

### Post by philinux on 2013-10-02
> **hiig said:**
> Once I've made the file, how can I upload it from the terminal?

type in.

```
pastebinit processes.txt
```

then copy the link created in your next post.

---

### Post by hiig on 2013-10-02
Here you go: [http://paste.ubuntu.com/6183903/](http://paste.ubuntu.com/6183903/)

---

### Post by Gyokuro on 2013-10-02
Hi

Sorry for the rest that I step in - it's interesting which processes you are running but in case of memory related questions you should post the output of top or better vmstat.

---

### Post by hiig on 2013-10-02
Had to do a bit of googling to figure out how, but I got it quick enough: [http://paste.ubuntu.com/6184788/](http://paste.ubuntu.com/6184788/)

---

### Post by philinux on 2013-10-03
Looks like mono is hogging the cpu for sure. Post back what vmstat displays in the terminal.

---

### Post by hiig on 2013-10-03
High CPU and RAM usage is expected on mono. That's fine. I just need to know if there are any other processes that are useless.

---

### Post by philinux on 2013-10-03
> **hiig said:**
> High CPU and RAM usage is expected on mono. That's fine. I just need to know if there are any other processes that are useless.

Have you got a swap partition. That might help.

What does vmstat report.

If you look at your pastebin from post 7 the top 4 are mono and if you look down the list there is nothing else of consequence. Unless my eyes deceive me.

---

### Post by hiig on 2013-10-03
Vmstat: [http://paste.ubuntu.com/6188361](http://paste.ubuntu.com/6188361)

As for having a swap partition, I'm not sure. When I got the ISO for ubuntu-server, everything was installed automatically.

If I don't have one, I'm not sure I would want one. The crawling these mono processes facilitate involve heavy HDD usage. It's rare that the hard drive is not clicking about with activity (and its silence is usually a good indicator of when something has gone wrong). So I'm not sure if having a swap/larger swap would be beneficial or not.

---

### Post by philinux on 2013-10-03
In a terminal what does this show.

```
free -m
```

Take a look at how swap can help. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by hiig on 2013-10-03
Swap shows 1533. I assume that's MB. Wouldn't make sense for it to be anything else.

---

### Post by philinux on 2013-10-03
> **hiig said:**
> Swap shows 1533. I assume that's MB. Wouldn't make sense for it to be anything else.

Ok but lets see what 

```
free -m
```

Shows in total. Just copy and paste what it shows

---

### Post by hiig on 2013-10-03
For total, used, free, shared, buffers, and cached respectively:

Mem: 1554, 1476, 77, 0, 2, 115
Swap: 1533, 114, 1419

---

