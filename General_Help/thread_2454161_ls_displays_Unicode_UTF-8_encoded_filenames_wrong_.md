---
title: "ls displays Unicode UTF-8 encoded filenames wrong in a script"
date: 2020-11-24
forum: General Help
---

### Post by Skaperen on 2020-11-24
this is on _Xubuntu 18.04.5_ last _upgraded yesterday_, although this has been seen for years, although i have made the effort to dig into this recently.  when executed directly, it works correctly every time.  when run via a script, under either *Python2* or *Python3* or b*ash 4.4.20* it does not run correctly.  however, if run under the script and piped through *cat* then it works correctly.  it should output the UTF-8 encoding of ö so the terminal displays it correctly.  what it is doing in the wrong cases is outputting _backslash octal_ conversion of the UTF-8 in the file name.

i have added output of environment variables in the scripts just before executing ls and variables filtered as shown are the same in all cases (in scripts or in shell command line):
```

lt2a/forums /home/forums 32> env|egrep 'LC|TERM'|sort
COLORTERM=truecolor
LC_ALL=en_US.utf8
LC_COLLATE=en_US.utf8
LC_CTYPE=en_US.utf8
LC_MESSAGES=en_US.utf8
LC_NUMERIC=en_US.utf8
SHELLCWD=/home/forums
TERM=xterm-256color
TERMID=pts_14
lt2a/forums /home/forums 33> cat /usr/host/bin/dlenv
#!/bin/bash
env>env
exec ls -dl --full-time "$@"
lt2a/forums /home/forums 34> dlenv  Ulf_Söderberg_Tidvatten.mp3
-rw-r--r-- 1 forums forums 105420813 2018-02-21 23:12:21.000000000 -0500 'Ulf_S'$'\303\266''derberg_Tidvatten.mp3'
lt2a/forums /home/forums 35> egrep 'LC|TERM'<env|sort
COLORTERM=truecolor
LC_ALL=en_US.utf8
LC_COLLATE=en_US.utf8
LC_CTYPE=en_US.utf8
LC_MESSAGES=en_US.utf8
LC_NUMERIC=en_US.utf8
SHELLCWD=/home/forums
TERM=xterm-256color
TERMID=pts_14
lt2a/forums /home/forums 36> ls -dl --full-time Ulf_Söderberg_Tidvatten.mp3
-rw-r--r-- 1 forums forums 105420813 2018-02-21 23:12:21.000000000 -0500 Ulf_Söderberg_Tidvatten.mp3
lt2a/forums /home/forums 37> 

```

---

