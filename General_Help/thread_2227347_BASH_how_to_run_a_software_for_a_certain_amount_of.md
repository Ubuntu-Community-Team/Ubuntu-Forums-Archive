---
title: "BASH: how to run a software for a certain amount of time"
date: 2014-06-01
forum: General Help
---

### Post by marbew on 2014-06-01
Hello, 
How is possible to run a script that prints on the screen its stdout that continues to change (like top for instance) for example only for 10 mins.
And after that i would like to save the last output available in a file.
What command I should use for this purpose?

---

### Post by philinux on 2014-06-01
Have a look at the man page for the watch command.

---

### Post by Lars Noodén on 2014-06-01
[timeout](http://manpages.ubuntu.com/manpages/trusty/en/man1/timeout.1.html) will run something for a specified duration and then kill it.

Do you want to capture all of the output or just the last n lines?

---

### Post by philinux on 2014-06-02
Now I'm back at my box I can give an example.

```
watch -n 5 "iwconfig wlan0 | grep -i --color quality"
```

-n 5 is every 5 seconds. Ctrl c to quit it.

---

### Post by marbew on 2014-06-04
**timeout** and watch **great**. How to save the output is fine with **>>** or **>** or **tee** command that's ok

---

