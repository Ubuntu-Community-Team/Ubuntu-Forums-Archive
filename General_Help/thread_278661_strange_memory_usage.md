---
title: "strange memory usage"
date: 2006-10-16
forum: General Help
---

### Post by bastupungen on 2006-10-16
Hello!
I am running a gameserver with linux-ubuntu. I just checked my memory usage on the server and can't get this straight. I have really few things on this server. What i run daily is: srcds (Counterstrike source server), proftpd and apache (with php and mysql)

But when i check "free" i see that almost all my memory is used up. This can't be good for server performace. Especially not the gameserver, which I am having enough problems with as it is.

This is the output of free:
             total       used       free     shared    buffers     cached
Mem:        906348     846564      59784          0      82128     478928
-/+ buffers/cache:     285508     620840
Swap:      1510068        200    1509868

As you can see more then half of my memory is cached or something. I don't really understand why this is.

And if i check top i get that the only service that is using some real memory space is srcds, with about 20% mem usage. this is the output of top:
top - 00:03:37 up 2 days,  3:24,  1 user,  load average: 0.06, 0.08, 0.14
Tasks:  91 total,   1 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7% us,  0.8% sy,  0.0% ni, 98.5% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    906348k total,   848268k used,    58080k free,    82304k buffers
Swap:  1510068k total,      200k used,  1509868k free,   479840k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5453 bastu     20   5  267m 187m  12m S    3 21.2 141:47.29 srcds_i686
    1 root      16   0  1564  532  460 S    0  0.1   0:01.11 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    5 root      34  19     0    0    0 S    0  0.0   0:00.67 ksoftirqd/1
    6 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/0
    7 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1

....

Am I suffering from some kind of memory **** or is this caching normal?

---

### Post by ebutton on 2006-10-16
I'm running amd64 and I'm a rookie, but I thought this comparison might help in some way:

ebutton@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       1028464     390820     637644          0       7624     203176
-/+ buffers/cache:     180020     848444
Swap:      3036244          0    3036244
ebutton@ubuntu:~$ top

top - 17:24:31 up 32 min,  2 users,  load average: 0.09, 0.08, 0.04
Tasks:  91 total,   1 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.6% us,  0.3% sy,  0.0% ni, 89.1% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1028464k total,   391732k used,   636732k free,     7672k buffers
Swap:  3036244k total,        0k used,  3036244k free,   203264k cached

Regards,
EdB

---

### Post by bastupungen on 2006-10-16
What I can read from your numbers there. You do not have the same problem as i do. you have more then half of your mem-space free. So I guess this is NOT some kind of function in linux mem-usage.

Curse it. How can I see what processes are eating up my memory?

---

### Post by MWAAAHAAA on 2006-10-16
It is quite normal for a linux system to have almost no free memory available. For example, I have 2GB of RAM and only 50MB free. Just imagine you have a bookcase and your desk. There are a number of books you are using quite frequently so you want those lying around on your desk instead of in the bookcase right? That's exactly what linux does, keep those books, and as much of them, out of the bookcase and on your desk, so you can use them quickly when you have to. To quote someone "The reason Linux uses so much memory for disk cache is because the RAM is wasted if it isn't used".

You can search google for terms such as 'linux memory management' if you'd like to know more.

---

### Post by bastupungen on 2006-10-16
Ok. I guess that makes sence for a desktop-enviroment. But for a server enviroment? What happends if my gameserver suddenly (like NOW) needs more ram space? Will it then have to ask the kernel what to remove from ram and then write or what? That doesn't seem efficient, or am i wrong?

If you don't think this will affect my servers performance, then i'll beleve you.

---

### Post by bettlebrox on 2006-10-16
Caching is generally good. This is a good write up on how Linux uses memory:

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html]("http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html")

---

### Post by bastupungen on 2006-10-16
"generally"

Not really a word that made me happy. =) Generally is mostly about Desktop and general use. A gameserver is not general. I guess its good for like apache and FTP. But im not sure if this is "generally" good for an resourse hoggin' game server.

---

### Post by CatKiller on 2006-10-16
If your program suddenly needs to load something into RAM, then it's going to take just as long to load it there if the memory is "empty" as if there's something there, surely? It's not as if the nanoseconds that it takes to refresh the memory is significant next to the **hours** it takes for your hard drive to spin up and start spitting out data.

And hey, next time you need that data, it'll be cached in RAM, rather than needing to be read from disk again. Isn't that sensible?

And the reason you aren't overjoyed by the word "generally" is because you don't know what it means ;)

---

### Post by bastupungen on 2006-10-16
"If your program suddenly needs to load something into RAM, then it's going to take just as long to load it there if the memory is "empty" as if there's something there, surely? It's not as if the nanoseconds that it takes to refresh the memory is significant next to the hours it takes for your hard drive to spin up and start spitting out data.

And hey, next time you need that data, it'll be cached in RAM, rather than needing to be read from disk again. Isn't that sensible?"

I guess that makes sense. I was just worried where all my ram whent, when i didn't know what ate it all. But my question remains. If it isn't my server software (like srcds) that is using the ram (it only used 20%), what is? How can i check which software uses this ram-space.

"And the reason you aren't overjoyed by the word "generally" is because you don't know what it means"
I know what it means but i don't like in the the context it is used. Because if i would have alot of desktop, resource hoggin, programs running then maybe they would get an higher memory priority then srcds (if resouces would get slow for this program it would effect the game for everyone playing, instantly). For all i know all my recently used files in the FTP may have an higher priority. Yes i have given srcds an higher priority but linux is a little unpredictable to me since i don't know the endless amount of variables behind nice.

Do you se my point?

---

### Post by CatKiller on 2006-10-17
I don't know what specifically you've got in memory, and I don't know enough commands myself to help you find out. But you seem to have rather missed the point. Your computer's been up for two days. During that time **everything** that you've had in memory is left there until that memory is explicitly needed again, just in case you need it again. I'd be surprised if you didn't appear to be "using" all your memory. And this isn't a "desktop" thing - Linux has had this function for years, and is allegedly "not ready for the desktop", despite being used for servers for pretty much all that time.

The page that bettlebrox linked to is quite interesting, and suggests that **pmap -d** will give you far more information than you'd want.

You either have enough memory to run the programs all at once that you want to, or you don't. Advantageous use of the memory that you'd otherwise be wasting isn't going to affect that.

My comment about the word "generally" was a not-very-good joke (hey, it was stupid o'clock in the morning here). In mathematics terminology, "generally" means the same as "always".

---

### Post by bonzodog on 2006-10-17
On top of this, linux memory caching is intelligent-  if something needs to be run which is going to use more RAM than is available, it will remove items from cache to make space for the new one.

---

### Post by bastupungen on 2006-10-17
I guess my system is all fine and dandy. The reason I'm a little jumpy is because the gameserver is a piece of shit program that i don't trust one bit, and still I'm totally dependant of it. So I'm searching for memory leaks.

I did some more research with top and found that the top program cannot find enough programs using the memory to constitute for the 98.9 memory usage. I can find only about 60%(counted really high), by using top. So is this cache used by some program not running anymore (which means it will be overwritten instantly someone tries to access that part of the memory) or could it be a memory leak from some program? I am partly trying to make sure my system is fine and also trying to learn more about linux. So please answer me pedagogicly =)

"You either have enough memory to run the programs all at once that you want to, or you don't. Advantageous use of the memory that you'd otherwise be wasting isn't going to affect that."

True in a perfect world but linux is hardly perfect so im covering my bases.

"and is allegedly "not ready for the desktop", despite being used for servers for pretty much all that time."

Even though this is pretty far off topic I have to respond.
*getting the hardware firewall up and making sure it is running*
ARGH I HATE using linux as a desktop. Its really inefficent and frustrating. Windows XP FTW! Ok there I said it, feel free to kill me!  =D

---

### Post by bastupungen on 2006-10-17
> **bonzodog said:**
> On top of this, linux memory caching is intelligent-  if something needs to be run which is going to use more RAM than is available, it will remove items from cache to make space for the new one.

That is good to know. Thats probobly it. Some programs had ram space allocated. I then shut the program down and it is still cached in case the program is started again. Smart! but hard to !KNOW!, made me suspect memory leakage.

If you know some way I can reassure myself that this is not memory leakage then please, do tell.

---

### Post by bettlebrox on 2006-10-17
>I can find only about 60%(counted really high), by using top

The rest is being used by the kernel as cache. If it needs more memory it will flush the cache. U can tweak how much cache it uses, but unless your encountering problems it's best to leave it be.

---

### Post by bastupungen on 2006-10-17
> **bettlebrox said:**
> >I can find only about 60%(counted really high), by using top

The rest is being used by the kernel as cache. If it needs more memory it will flush the cache. U can tweak how much cache it uses, but unless your encountering problems it's best to leave it be.

Ok! it verified from several sources and, no im not currently suffering any serious problems which should derive from memory, so I'll leave it be. Thanks guys!

---

