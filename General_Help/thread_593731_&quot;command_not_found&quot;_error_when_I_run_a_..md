---
title: "&quot;command not found&quot; error when I run a .bin file in Edgy"
date: 2007-10-27
forum: General Help
---

### Post by Lego Dragon Rider on 2007-10-27
For some reason, only a few unsupported binaries will run on my computer. I'm running Edgy 6.10. A binary will open with Terminal by default. When I try to run one from terminal, I get:

[B]"Bash:* binary_name.bin* : command not found."

[/B]I just type the name into the terminal without any suffix or prefix. 

Am I doing something wrong?
Any idea what's going on?

---

### Post by mali2297 on 2007-10-27
If the file foo.bin is on your Desktop, type:
```

cd ~/Desktop
chmod +x foo.bin
./foo.bin

```

---

