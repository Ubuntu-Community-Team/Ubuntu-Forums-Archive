---
title: "embed cpu usage in bash prompt"
date: 2016-05-24
forum: General Help
---

### Post by alex_charters2 on 2016-05-24
Hi all 
I am trying to embed the CPU usage in my bash prompt. I can get an accurate CPU usage figure using this command ```
echo print `top -n 1 | tr -s " " | cut -d$" " -f10 | tail -n +8 | head -n -1 | paste -sd+ | bc`/ `nproc` | python
```  However I would like to put a percentage sign on the end of the output and embed it into PS1 so the command prompt would look like ```
user@host CPU=35.34% $
```

Thanks in advance for the help
Alex

---

### Post by vasa1 on 2016-05-25
Does your code work when run in a terminal? It doesn't work for me:[CODE]echo print `top -n 1 | tr -s " " | cut -d$" " -f10 | tail -n +8 | head -n -1 | paste -sd+ | bc`/ `nproc` | python
(standard_in) 1: syntax error
  File "<stdin>", line 1
    print / 2
          ^
SyntaxError: invalid syntax

---

### Post by alex_charters2 on 2016-05-25
yes I just tried it and the code does work for me



could you  please let me know how I can embed this into my command prompt as i said in my first post 
[ATTACH=CONFIG]269277[/ATTACH]
thanks
Alex

---

### Post by vasa1 on 2016-05-25
My bad. I had a .toprc which was interfering. It now works for me.

```
export PS1="\u@\h CPU%=$(echo print `top -n 1 | tr -s " " | cut -d$" " -f10 | tail -n +8 | head -n -1 | paste -sd+ | bc`/ `nproc` | python) $ "
```gives what you want, but then doesn't change each time I hit enter.

BTW, check out [http://askubuntu.com/questions/651871/why-is-my-function-not-re-evaluated-in-ps1](http://askubuntu.com/questions/651871/why-is-my-function-not-re-evaluated-in-ps1) to make sure your code is updated rather than remaining static.

---

### Post by alex_charters2 on 2016-05-25
thanks for the help i have now got it fully working so that it updates each time here is the code```
PS1='\u@\h CPU $(echo print `top -n 1 | tr -s " " | cut -d$" " -f10 | tail -n +8 | head -n -1 | paste -sd+ | bc`/ `nproc` | python)% $ '


``` now i can incorporate that into my customized bash prompt project.:):KS

---

### Post by vasa1 on 2016-05-25
You can mark your thread **SOLVED**. Visit [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) to know how and why we all benefit.

FWIW, [https://mohammadg.com/linux/how-to-get-overall-cpu-utilization-from-the-bash-command-line/](https://mohammadg.com/linux/how-to-get-overall-cpu-utilization-from-the-bash-command-line/)

And I learned how to refresh PS1. That was puzzling me quite a bit!

---

### Post by alex_charters2 on 2016-05-25
ha ha that is exactly the same website I got my original code from:lolflag:

---

### Post by vasa1 on 2016-05-26
BTW, do you plan to look at Conky? It can help give you what you ask for in [Display the amount of memory being USED]("http://ubuntuforums.org/showthread.php?t=2325810") as well CPU usage.

---

