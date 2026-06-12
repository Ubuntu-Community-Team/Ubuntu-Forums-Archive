---
title: "ps -aux commad's output"
date: 2017-06-28
forum: General Help
---

### Post by amitha3 on 2017-06-28
Hi,

Recently I found that the output of **ps -aux** command **displayed some tail -f command's flour instances that has been used previously**. **Could I verify are those processes of tail -f command still runs according to the output of ps -aux command, even-though those are terminated using CTRL + C ?** or was that the history, that displayed by ps -aux command?

Thanks

---

### Post by howefield on 2017-06-28
Not a chat thread so moved to the "*General Help*" forum.

---

### Post by spjackson on 2017-06-28
The ps command only shows **active** processes. It does not show any processes that have terminated nor does it show any history.

---

### Post by amitha3 on 2017-06-29
Hi Spjackson,

Thanks for the information. **My point is why ps -aux show the tail command as an active process, after terminating it by pressing CTRL+C keys?**

---

### Post by spjackson on 2017-06-29
I'm sorry, I thought you were asking whether the processes were still running, to which the simple answer is yes. Why they are still running after Ctrl-C is a more complex question. There are many possibilities which depend on the precise context in which they are being run. Are they [zombie processes]("https://en.wikipedia.org/wiki/Zombie_process")? In any event, I am afraid I don't have a simple answer to this question.

---

### Post by amitha3 on 2017-06-30
Thanks a lot for your valuable information. :)

---

