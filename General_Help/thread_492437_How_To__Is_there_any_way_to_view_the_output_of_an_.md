---
title: "How To:  Is there any way to view the output of an existing process. . .?"
date: 2007-07-04
forum: General Help
---

### Post by michwill on 2007-07-04
Hi All,

I'm looking to "interrupt" a process and see it's current output.  Actually interrupt is the wrong word.  I simply would like to observe the result of a command that was previously set in motion (whether it was via SSH, or whatever) as it runs.  For instance, if I issue the following:


```
% command &
```



I'd like to be able to say something like:


```
ps aux | grep -i command | show_me_your_stdout_until_I_control_c_you
```


. . .does anything like this exist in the *NIX world?


Thanks

---

### Post by Bachstelze on 2007-07-04
If you don't want to do über-complicated stuff with job control, *screen* will do what you're looking for.

```
sudo apt-get install screen
screen YOUR_COMMAND_HERE
```

You can then press Ctrl+A-Ctrl+D to "detach" the screen and go back tou your normal shell. To come back to the screen later, do

```
screen -R
```

---

### Post by michwill on 2007-07-04
Very cool. Gotcha, well a couple of questions:



1)  How many different "screen" process can you spawn at once?  What if I want to watch multiple commands?

2)  Let's say I *am* interested in über complicated command stuff, how would I go about it?

---

