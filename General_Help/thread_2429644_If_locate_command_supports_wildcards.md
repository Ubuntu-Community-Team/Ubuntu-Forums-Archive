---
title: "If locate command supports wildcards?"
date: 2019-10-21
forum: General Help
---

### Post by petrogromovo on 2019-10-21
Hello,
If locate command (kubuntu 18) can work with wildcards?
Looking at next 3 commands looks like no:
```
$ locate -i .env__lo 
/mnt/_work_sdb8/wwwroot/lar/DockerApps/votes_docker/votes/.env__LoCALHOST
/mnt/_work_sdb8/wwwroot/lar/votes/.env__LoCALHOST
$ locate -i .env_*lo 
$ locate -i .env_?lo 

```

Why last 2 outputs are empty? Is it invalid syntax ?

  Thanks!

---

### Post by sudodus on 2019-10-21
Yes, and **--regex** will let you use extended regular expressions (like for example grep -E).

See
```

$ man locate

...
       locate  reads  one or more databases prepared by updatedb(8) and writes
       file names matching at least one of the PATTERNs  to  standard  output,
       one per line.

       If  --regex is not specified, PATTERNs can contain globbing characters.
       If any PATTERN contains no globbing characters, locate  behaves  as  if
       the pattern were *PATTERN*.

...

       --regex
              Interpret all PATTERNs as extended regexps.

```

[hr][/hr]
Edit: Try

```

locate -i  *.env_*lo*

```
or
```

locate -i  .env__lo

```
or
```

locate -i --regex  .*\.env_*lo.*

```

---

### Post by #&amp;thj^% on 2019-10-21
see if this test will work for you;
```
locate '*lua*so*'
```
I use lua cause I don't work with Dockers.
Also this one:
```
locate --regex 'lua.*so.*' | head -5
```
Ninja'd by my old buddy sudodus

---

### Post by sudodus on 2019-10-21
@1fallen, old buddy,

Your examples are good, because they can be tested by more people and give relevant output :-)

---

### Post by petrogromovo on 2019-10-22
Thanks,
  but looks like with --regex key locate works too long...
  
also can I search substring in content of the found file? Or some other command ?

---

### Post by sudodus on 2019-10-22
You can pipe the output to **grep** and that way search for a pattern in the found file(s).

---

### Post by dragonfly41 on 2019-10-22
Expanding on the grep advice ..

also (for speed of search) look at piping through [ripgrep]("https://github.com/BurntSushi/ripgrep")

---

