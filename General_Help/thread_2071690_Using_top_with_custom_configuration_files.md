---
title: "Using top with custom configuration files"
date: 2012-10-16
forum: General Help
---

### Post by cogset on 2012-10-16
I'm starting to use top alongside htop as a system monitor,I see it has many options amongst which the possibility of saving the actual layout to a .toprc file by pressing W : I was wondering if it was somehow possible to save multiple configuration files in order to use top with different layouts without having to rearrange it every time?

---

### Post by jerrrys on 2012-10-16
From the man page

while **top** is referred to throughout this document, you are free to name the program anything you wish.  That new name, possibly an alias,  will then  be reflected on top&#8217;s display and used when reading and writing a configuration file.

[http://manpages.ubuntu.com/manpages/lucid/man1/top.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/top.1.html)

---

### Post by cogset on 2012-10-18
Sorry,I've read that but still don't get it:how do I rename top? I've tried to alias it to top1,but then all I'm getting when I save a new config file is that the old configuration is overwritten.

---

### Post by jerrrys on 2012-10-18
**5b. PERSONAL Configuration File** 
This file is written as '$HOME/.your-name-4-top' + 'rc'. Use the 'W' interactive command to create it or update it. Here is the general layout: global # line 1: the program name/alias  notation " # line 2: id,altscr,irixps,delay,curwin per ea # line a:  winname,fieldscur window # line b: winflags,sortindx,maxtasks " # line c:  summclr,msgsclr,headclr,taskclr 
If the $HOME variable is not present, top will try to write the personal configuration file to the current directory, subject to permissions. 
[http://linux.die.net/man/1/top](http://linux.die.net/man/1/top)


[http://www.linkedin.com/answers/technology/information-technology/computers-software/TCH_ITS_CMP/640403-48617410](http://www.linkedin.com/answers/technology/information-technology/computers-software/TCH_ITS_CMP/640403-48617410)


[https://www.google.com/search?q=configuration+files+for+top&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=en&client=firefox-a&hs=SJU&rls=org.mozilla:en-US:official&q=linux+top+config+file&revid=1393504407&sa=X&ei=D99_UKHrDceJiALs8IHYBg&ved=0CIQBENUCKAI&bav=on.2,or.r_gc.r_pw.r_qf.&fp=df5572c51b7067a4&bpcl=35466521&biw=1024&bih=644](https://www.google.com/search?q=configuration+files+for+top&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=en&client=firefox-a&hs=SJU&rls=org.mozilla:en-US:official&q=linux+top+config+file&revid=1393504407&sa=X&ei=D99_UKHrDceJiALs8IHYBg&ved=0CIQBENUCKAI&bav=on.2,or.r_gc.r_pw.r_qf.&fp=df5572c51b7067a4&bpcl=35466521&biw=1024&bih=644)

---

### Post by kjohri on 2012-10-18
You can link top with some other name. For example,

```
ln -s /usr/bin/top topsy
./topsy
```

Now, top is started with the name topsy, which is shown in top left corner. When you give the W command, the settings are saved in $HOME/.topsyrc. When topsy is run next time, it reads settings from this file.

---

### Post by cogset on 2012-10-18
Perfect,thank you very much.

---

