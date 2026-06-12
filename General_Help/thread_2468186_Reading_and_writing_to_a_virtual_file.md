---
title: "Reading and writing to a virtual file?"
date: 2021-10-20
forum: General Help
---

### Post by wrybread on 2021-10-20
I have two scripts running on an Ubuntu machine that need to communicate, and I was thinking a good (easy) way to do that could be by reading and writing a virtual file. 

However this communication happens twice per second all day every day, and it's running on an SD harddrive, so I'd like to confirm that I'm not taxing the harddrive or straining resources.

Am I correct in thinking that the only way to write to a virtual file is with a ramdisk? Or does Ubuntu already have a way to do this without creating a ramdisk?

If I need to create a RAMdisk, this is the best way?

```

sudo mkdir /mnt/ramdisk
sudo mount -t tmpfs -o rw,size=50M tmpfs /mnt/ramdisk

```

And eventually put that mount command in fstab to make it permanent (repeated each reboot).

Thanks for any help.

---

### Post by SeijiSensei on 2021-10-20
Ubuntu creates a scratch area for you in memory.  You can see it under /run/user/[userid], e.g., /run/user/1000 if you're the first or only user on your machine.  If you run "ls -lt /run/user" you'll see that you own /run/user/[userid] and can write there.

---

### Post by wrybread on 2021-10-20
> Ubuntu creates a scratch area for you in memory. You can see it under /run/user/[userid], e.g., /run/user/1000 if you're the first or only user on your machine. If you run "ls -lt /run/user" you'll see that you own /run/user/[userid] and can write there.

Aha, thanks for that. I see it now in the results of "df -h" For anyone else who comes this way, run "df -h" and look for filesystems of the "tempfs" type. Here's the ones I see:

```

tmpfs           1.6G  3.0M  1.6G   1% /run
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           1.6G   16K  1.6G   1% /run/user/1000

```

Do you happen to know if it's bad practice to read and write to a file in tempfs multiple times per second?

Can anyone see a downside?

---

### Post by Doug S on 2021-10-20
> **wrybread said:**
> Do you happen to know if it's bad practice to read and write to a file in tempfs multiple times per second?

Can anyone see a downside?I do not think it is bad practice to use it.
For some tests I have been doing with shallow idle states, I have been passing tokens around some fifo files in /dev/shm at an average rate of 250,000 read/write cycles per second. About 10 hours per test, and I have done it maybe 50 times over a few months.
I do not see a downside.

Potentially interesting side note: The rate of token passing, for the 2 or more cross-core pair case, slows down by ~~50% over the 10 hours test. I have yet to figure out why.

EDIT (after the next two posts): My token passing work is done via named pipes, although I do also have a similar test that uses un-named pipes.

```
doug@s19:/run/user/1000$ doug@s19:/run/user/1000$ ls -l po*
[COLOR="#FF0000"]p[/COLOR]rw-rw-r-- 1 doug doug 0 Oct 20 17:25 pong1
[COLOR="#FF0000"]p[/COLOR]rw-rw-r-- 1 doug doug 0 Oct 20 17:25 pong10
doug@s19:/run/user/1000$ ls -F po*
pong1[COLOR="#FF0000"]|[/COLOR]  pong10[COLOR="#FF0000"]|[/COLOR]
```

see also[ here]("https://www.gnu.org/software/coreutils/manual/html_node/What-information-is-listed.html").

---

### Post by TheFu on 2021-10-20
Uh ... use a named pipe.  There are "writer" processes and 1 "reader".  This has been part of Unix since the 1970s.  Very easy to use.
In a CLI terminal, using **ls -F** will show these special files as 
```
file=
```

Look in /tmp/ and you'll likely see a number named pipes for different tools.  My password manager and batch queue programs have pipe files in there.

[https://www.networkworld.com/article/3251853/why-use-named-pipes-on-linux.html](https://www.networkworld.com/article/3251853/why-use-named-pipes-on-linux.html)  Pretty easy.  We can actually use these to provide controls to programs that accept input from stdin as well, but that's a bit of a hack.  Some GUI programs provide control in this way. I can probably dig up an example to do that too - any scripting language can be used. I did it in bash, but the reading and writing are usually easier with better languages like perl, python, ruby, .... 

OTOH, using a direct socket on any of the 127.0.0.x/8 interfaces is just as easy if you ever may want the writer and reader to be on different systems, I'd do that instead.  127.x.x.x/8 is only for the loopback interface, so only the same host can access it.

---

### Post by Impavidus on 2021-10-21
+1 to named pipes or sockets. My first thought as well. They're designed for this. I used them on a few occasions. Note that there are both network sockets, which can also be used locally, and Unix domain sockets, which get a name in the filesystem.

---

