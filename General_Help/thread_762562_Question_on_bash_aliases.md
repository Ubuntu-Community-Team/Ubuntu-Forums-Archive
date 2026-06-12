---
title: "Question on bash aliases"
date: 2008-04-22
forum: General Help
---

### Post by InTokyo on 2008-04-22
the program I am developing is hanging and I am finding my self having to kill it often. I would like to write an alias that will do it. My first thought was to write an alias (for the bash shell) like:
mykill='ps -elf | grep $1 | grep -v grep | awk '{print $4}' | kill -9

However this does not work.

any suggestion on how to proceed?  Again this is to be run on the bash shell.

---

### Post by bingoUV on 2008-04-22
I don't know what criteria you are using to search for the process. But look into pkill and killall to do this for you instead of parsing the output of ps.

---

### Post by duckville on 2008-04-22
To make a alias for bash....
"nano ~/.bashrc" to open the file, there should be some aliases already there.
is simply:
alias *alias_name='killall app_to_kill'*

---

### Post by InTokyo on 2008-04-22
All,

Thanks for the suggestions of using pkill pkillall. 

The problem with these methods is that I invoke the program by "python <program name>". The pkill and pkillall will kill all python invoked programs (not what I want). So, my only option is to parse the ps -elf listing for the program name. 


again any help or direction?

---

### Post by bingoUV on 2008-04-22
That is why pkill exists. Start the process
```

python script.py

```Now kill it by
```

pkill -f 'python script.py'

```The folowing will kill all python scripts starting with scr e.g. **python script1.py**  as well as **python script2.py**
```

pkill -f 'python scr'

```Of course, the following  is the most powerful command
```

man pkill

```

---

