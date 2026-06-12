---
title: "Java uses way too much RAM"
date: 2013-11-29
forum: General Help
---

### Post by geelsd on 2013-11-29
[COLOR=#000000]Dear community,[/COLOR]


[COLOR=#000000]Ubuntu 12.10 Server. (x64)[/COLOR]


[COLOR=#000000]I've been having alot of trouble with Java and Minecraft at the moment. I allocate the 1024MB ram with the -xms and -xmx flag, and on 80% of the Minecraft servers it works. But sometimes some Minecraft server crashes or something and "top" shows 7GB of ram is being used by it.[/COLOR]

[COLOR=#000000]I use openjdk-7-jre for this. I'd love some help.[/COLOR]

---

### Post by mikewhatever on 2013-11-29
Looks like there are memory leaks. Consider submitting bug reports.

---

### Post by geelsd on 2013-12-05
That is the only option?

---

### Post by slickymaster on 2013-12-05
> **mikewhatever said:**
> Looks like there are memory leaks. Consider submitting bug reports.

+1

There's a tool you can use to confirm it. It's called [memprof]("http://manpages.ubuntu.com/manpages/dapper/man1/memprof.1.html") and it's used for profiling memory usage and finding memory leaks.

---

### Post by r-senior on 2013-12-05
There's also VisualVM for monitoring what's happening in the Java VM. You can do JVM heap dumps, monitor garbage collection and so on. It has a great plugin called VisualGC that shows whats happening with the heap and garbage collector.

```
$ apt-cache search visualvm
visualvm - All-in-One Java Troubleshooting Tool
```

You might need to switch to Oracle's JDK to get all the features working though.

---

