---
title: "Top and killing"
date: 2014-03-01
forum: General Help
---

### Post by k-tim-b on 2014-03-01
When I run Top and see a process I want killed. What command would I type to kill it?

---

### Post by howefield on 2014-03-01
Type the letter k and follow the screen instructions.

---

### Post by monkeybrain20122 on 2014-03-01
```
kill <PID>
```

Where <PID> is the process id of the process you want to kill

if the process is owned by root start the command with sudo.

P.S. Strange that sometimes I find unresponsive processes(zombies?) that I can't kill from the terminal but can kill easily with system monitor.

---

### Post by tgalati4 on 2014-03-01
Or install *htop*.  You can kill processes with a menu and a selection of kill flags.

```
sudo apt-get install htop
```

---

