---
title: "Illegal option -f in my shell script"
date: 2013-12-01
forum: General Help
---

### Post by willsch89 on 2013-12-01
[COLOR=#000000]Hi

I get this error: "[/COLOR]Illegal option -f" in my shell script
only when I run  with watch command: *watch -n 4 ./collect-results.sh *

When I use only *./collect-results.sh *works fine

[COLOR=#000000]Any ideas?[/COLOR]
[COLOR=#000000]
[/COLOR]```
#/bin/bash
...


export -f get_data
export -f get_jitter
export -f get_average_throughput
export -f get_total_latency
export -f get_maximum_latency
[COLOR=#000000]
[/COLOR]
```[COLOR=#000000]

Thanks[/COLOR]

---

### Post by steeldriver on 2013-12-01
Hello and welcome to the forum

I suspect it's because watch is running the command in a **dash** shell - overriding your #!/bin/bash shebang - from the watch manpage

```

NOTE
       **Note that command is given to "sh -c" **which means that you may need to
       use extra quoting to get the desired effect.  You can disable this with
       the -x or --exec option, which passes the command to exec(2) instead.

```

(in Ubuntu, /bin/sh is a symlink to /bin/dash by default). There doesn't seem to be an explicit option to tell it to use bash - if it's essential to make this work, you could always modify the symlink (I've done that myself, for things that really won't work otherwise - e.g. Makefiles that assume /bin/sh is a bash shell).

---

