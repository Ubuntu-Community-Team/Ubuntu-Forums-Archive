---
title: "Error message when trying to install Geany from the terminal"
date: 2017-01-20
forum: General Help
---

### Post by ronjjjg8885 on 2017-01-20
Hello
I'm trying to install Geany so I can start to learn Python.

When I'm typing in the theminal this:
```
sudo apt-get install geany
```

I get this:
```
$: command not found
```

Please let me know if you can help solving this.

---

### Post by howefield on 2017-01-20
The command is correct, are you sure that you typed it correctly ?

---

### Post by ronjjjg8885 on 2017-01-20
YES

Check out the image[ATTACH=CONFIG]273280[/ATTACH]

solved:
the problem was the added "$"

---

### Post by oldfred on 2017-01-20
With geany, I think there were three places where I had to change settings from tabs to spaces.
In preferences, editor, indentation, on saved(preferences, files) and in projects (if a project).

Other python info:
[https://ubuntuforums.org/archive/index.php/t-2206486.html](https://ubuntuforums.org/archive/index.php/t-2206486.html)

---

### Post by coffeecat on 2017-01-20
> **ronjjjg8885 said:**
> Hello
I'm trying to install Geany so I can start to learn Python.

When I'm typing in the theminal this:
```
sudo apt-get install geany
```

I get this:
```
$: command not found
```

Please let me know if you can help solving this.

> **ronjjjg8885 said:**
> YES

Check out the image[ATTACH=CONFIG]273280[/ATTACH]

Have another look at your screenshot. You didn't type this command:

```
sudo apt-get install geany
```

You typed this:

```
$ sudo apt-get install geany
```

The error message is because you prepended the command with a dollar sign, and the system doesn't understand that. You probably found that command in a howto somewhere where the author uses the dollar sign as a shorthand to show the terminal prompt. Just type the command without $.

---

