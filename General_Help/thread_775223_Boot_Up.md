---
title: "Boot Up"
date: 2008-04-29
forum: General Help
---

### Post by MosMusy on 2008-04-29
Is it normal that by boot up time for the newest version of Ubuntu (8.04) is longer than the previous version's boot up time.

Thanks

---

### Post by encompass on 2008-04-29
Sure could be.
I could depend on your system too.
For example mine that is older, it's ALOT slower kernel loading then in newer systems.  Simply because it's probably being slowly ignored and phased out.  (I use apm not acpi.)
The more complicated the OS generally it takes longer to load.  It's not always true, but many times yes.  You also need to take into concideration that this is always being built for the modern computer, so it's still fast on newer systems but slower on slower once.
Obvious when you think about it.

---

### Post by jakupl on 2008-05-01
that very much depends... how long does it take?

---

### Post by MosMusy on 2008-05-01
> **jakupl said:**
> that very much depends... how long does it take?

well, it takes a little longer than the previous version of ubuntu. This time the orange bar goes side to side for a while, then it actually starts loading, before it only loaded.

---

### Post by jakupl on 2008-05-01
If the boot-time annoys you, I would install bootchart.
```

sudo apt-get install bootchart
```

when you have done this, you will be able to graphically see the boot in /var/log/bootchart

Edit: You will for instance see your boot time in seconds and what is taking so long.

this is my bootchart. take a look.

---

### Post by jakupl on 2008-05-01
but you are true about longer boot time in hardy.

In gutsy my boot-time was 25 sec. in hardy it is 32 sec i believe. Though I don't really care that much.

Edit: Though I have had it down at 29 in hardy before :)

---

### Post by MosMusy on 2008-05-01
> **jakupl said:**
> If the boot-time annoys you, I would install bootchart.
```

sudo apt-get install bootchart
```

when you have done this, you will be able to graphically see the boot in /var/log/bootchart

Edit: You will for instance see your boot time in seconds and what is taking so long.

this is my bootchart. take a look.

ok, I installed it, now where do I get the bootchart?

---

### Post by jakupl on 2008-05-01
restart your computer and go to /var/log/bootchart directory.
there will one more file everytime you boot, picturing your last boot... so it is maybe a good idea to empty this directory every other week - every month... but nevermind.

---

### Post by MosMusy on 2008-05-14
> **jakupl said:**
> If the boot-time annoys you, I would install bootchart.
```

sudo apt-get install bootchart
```

when you have done this, you will be able to graphically see the boot in /var/log/bootchart

Edit: You will for instance see your boot time in seconds and what is taking so long.

this is my bootchart. take a look.

So, how do I get rid of this thing now? (the bootchart)

---

### Post by encompass on 2008-05-15
same way you got it but backwards...
```
sudo apt-get remove bootchart
```
I would also like to mention that there is very good documentation out there that can help you with these commands.  For example, simply googling bootchart linux would give you some results.  I have learned alot by surfing around documentations pages, learning how to tweak all the little parts of my system.
In this version of linux, it programming progresses with the hardware that exists.  If your hardware is staying the same you computer will ussualloy feel a little slower every time you use a newer version.  Windows is the same kind of system.  It's built to take advantage of newer hardware.

---

