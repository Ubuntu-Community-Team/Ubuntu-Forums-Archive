---
title: "Typing multiple lines: how?"
date: 2007-11-19
forum: General Help
---

### Post by Akira Mishima on 2007-11-19
Sorry for this silly question, but how can I change line when typing multiple lines such as this one:

sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new

In other words, how to go from one line to the next one without triggering an event? (As a newbie I would press Enter, but...)

Thanks

---

### Post by tehet on 2007-11-19
Perhaps you mean this?
```
command1 && command2 && command3
```

---

### Post by ajgreeny on 2007-11-19
That's the way!  The double && means the first command is acted on and if no problems it moves to the second etc etc.  If any errors occur the whole sequence stops until you sort out the problem,  A single & will allow the commands to follow one after another even if errors occur, so is not quite so useful.

---

### Post by dj Kalma on 2007-11-19
If the OP is trying to do multiple commands such as those in the example, it would be OK to just hit enter after every command. I don't see the need to use &&'s with those.

---

### Post by daengbo on 2007-11-19
He asked ...

---

