---
title: "Ubuntu can't turn off"
date: 2024-06-26
forum: General Help
---

### Post by alimamzi on 2024-06-26
I run ubuntu 22.04 on my pc but I encounter to problem .when I click on tabs power off my monitor change to black color but my pc didn't power off.i have to press key power manually .how can I solve it

---

### Post by Rubi1200 on 2024-06-26
Let's test something to try and find out what the problem might be.

Open a terminal with Ctrl+Alt+T:

```
sudo systemctl poweroff
```

Does the system shutdown normally?

---

### Post by ActionParsnip on 2024-06-26
Does the system have a make and model?

---

### Post by alimamzi on 2024-06-26
Excuse I'll try it because I'm far away my place that do it..I anwser as soon as possible

---

### Post by #&amp;thj^% on 2024-06-26
This may help us to help you as well, checking the logs:
```
 journalctl -rb -1

```

this will show the system logs just before your Linux system was shutdown the last time. This is what you need to analyze the long shutdown problem.

When you shut down your Linux system, it sends the sigterm and politely asks the running processes to stop. Some processes misbehave and they ignore the sigterm and keep on running.

This could cause a delay to the shutdown process as your system will wait for the running processes to stop for a predefined time period.
I've seen where it waits for a service to stop say 3-5 mins then waits another 3-5 mins.

Try to avoid a hard power off as much as possible.

---

