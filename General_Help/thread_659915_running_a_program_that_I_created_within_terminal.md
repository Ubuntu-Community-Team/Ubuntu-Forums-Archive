---
title: "running a program that I created within terminal"
date: 2008-01-06
forum: General Help
---

### Post by mitchelljj on 2008-01-06
Hi,

I am having difficulty executing a program within the terminal.

When I run the command sudo '/home/mitchelljj/aac2mp3.sh'.
It prompts me for my password and then it says that the command can't be found.

I have attached the file that I am trying to execute.

Thanks,

John

---

### Post by shad0w_walker on 2008-01-06
Have you made sure the file is executable? If it isn't then that won't help. Use 

```
chmod +x filename
```

To make it executable.

---

### Post by aktiwers on 2008-01-06
Wouldn't it be:
```
sudo sh aac2mp3.sh
```

---

### Post by mali2297 on 2008-01-06
I cannot see why you would need sudo.

Either run it with the command
```

bash /home/mitchelljj/aac2mp3.sh

```

**or** make it executable,
```

chmod +x /home/mitchelljj/aac2mp3.sh

```
and run it with
```

/home/mitchelljj/aac2mp3.sh

```

---

