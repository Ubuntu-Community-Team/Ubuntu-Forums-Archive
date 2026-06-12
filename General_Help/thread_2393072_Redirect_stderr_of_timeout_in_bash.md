---
title: "Redirect stderr of timeout in bash"
date: 2018-05-29
forum: General Help
---

### Post by toolazytowrite on 2018-05-29
I want to run a command with input and output within 1 second like this

timeout 1 $cmd < $inp > $out 

But when $cmd get a runtime error, it prints this which i found irritating

Timeout: the monitored command dumped core
myfile.sh : line 10 : 1234 Segmentation fault timeout 1 $cmd < $inp > $out

I want to redirect this message to a log file, and don't print it on the terminal

I have tried
timeout 1 $cmd < $inp > $out 2> /dev/null 
and
timeout --foreground 1 $cmd < $inp > $out 2> /dev/null 
but all of them failed

I assume that the message comes from the subshell when executing the $cmd, 
so i tried putting set +m before the timeout command, but still failed

---

