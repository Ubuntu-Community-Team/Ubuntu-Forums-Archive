---
title: "How do i bring gdb process up"
date: 2015-02-20
forum: General Help
---

### Post by nagarjuna2 on 2015-02-20
root@drone% ps -aux | grep authd
root     4299  5.0  0.5 159996 88016  ??  RX    7:21AM  11:13.62 /usr/sbin/authd -N
root     4356  0.0  0.4 76904 75116  p1- I     7:24AM   0:01.20 gdb authd
root    18946  0.0  0.0  1960  1192  p3  S+    2:49PM   0:00.00 grep authd


I see gdb authd process is still there i want to bring it up on my screen. How do i do that?
Any suggestions how to bring gdb up on screen?

---

### Post by steeldriver on 2015-02-20
Hello and welcome to the forums

Not sure I can answer your question, however the first step would probably be to try to identify what shell / terminal / session the command is running in - perhaps something like

```

pstree -lsp 4356

```

where 4356 is the PID of the process from your ps command. Btw do you mean 'screen' as in the actual (terminal multiplexing) program 'screen', or generically like "the computer screen"?

---

