---
title: "Two bash jobs started at the same time, one to monitor a log file."
date: 2013-08-13
forum: General Help
---

### Post by Trifonov on 2013-08-13
Hallo!

it is dificult to explane but lets try!
I am using python to execute an external program by simply using the python "os" libary:

os.system("./script1") # script1 generates several log files and the most important fo me is "info.log" !
os.system("./script2") # script2 uses the output from script1

the  problem is that those scripts are in 50000 element "for loop" and  "script1" needs at least 2 min to finish it's job (it has fixed time  duration)
In the first 1-2 sec I can find out whether I need the  output data or not bu looking in to the log file. However, as script1 is  already compiled program and i can modify it i have to wait till it  finish.
I was thinking about a method in Bash that i can run two processes at the same time:
one  is to start "./script1" and the other is to monitor any change in the  "info.log" file.... if "info.log" has been updated or it change its  size, 
then the second script to terminate both processes

something like:

os.system("  ./script1 1 > energy.log 2 > dev/null/ & if [ $(stat -c %s  info.log) -ge 1371]; then kill %1; else echo "OK"; fi") - which does not  work...

Please if someone know a method let me know!

All the best,
Tito

---

### Post by ian-weisser on 2013-08-14
The part I don't understand is why you want to do it in one line of shell script instead of python.
os and subprocess have the tools you need to start scripts, get PIDs, and kill a process.

---

