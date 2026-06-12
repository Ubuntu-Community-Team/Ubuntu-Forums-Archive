---
title: "How do I run a text-mode program without starting a terminal?"
date: 2007-11-17
forum: General Help
---

### Post by Excalibre on 2007-11-17
Pretty much like it sounds - I have a program that uses text mode that I want to run, but nothing happens unless I run it from a terminal, so I'm not sure how to put it into my applications menu and so forth.

---

### Post by Brautigam on 2007-11-17
what type of terminal do you speak of? i am relitively familiar with ubuntu 2.1

---

### Post by mali2297 on 2007-11-17
> **Excalibre said:**
> Pretty much like it sounds - I have a program that uses text mode that I want to run, but nothing happens unless I run it from a terminal, so I'm not sure how to put it into my applications menu and so forth.

I don't use Gnome anymore, but I think there is an option *Run in terminal* when creating a shortcut or menu entry.

Otherwise, set a custom command:
```

xterm -e name_of_program

```

---

### Post by rfruth on 2007-11-17
linux.org has a good terminal tutor [http://linux.org.mt/article/terminal]("http://linux.org.mt/article/terminal")

---

### Post by Excalibre on 2007-11-17
Okay, thanks. Is there a command line option for gnome-terminal to make it have 25 lines? The program complains because it starts by default with only 24 lines.

---

### Post by mali2297 on 2007-11-17
> **Excalibre said:**
> Okay, thanks. Is there a command line option for gnome-terminal to make it have 25 lines? The program complains because it starts by default with only 24 lines.

With xterm, you can use
```

xterm -geometry 100x30

```

I think this would work for gnome-terminal:
```

gnome-terminal --geometry=100x30

```

---

