---
title: "How do i remove &quot;acestream.list&quot;"
date: 2015-10-27
forum: General Help
---

### Post by Robin.sorensen91 on 2015-10-27
I want to remove the file acestream.list inside etc>apt>sources.list.d but i just cant.

I added the file there when i tried to install acestream, which i was unable to do to, and now that file is stopping the computer from running an apt-get update. I need it gone. 

But i cont understand how i should remove it. Tried terminal but cant get it to work. Help?

---

### Post by howefield on 2015-10-27
What did you try from the command, it probably should be something like..

```
sudo rm /etc/apt/sources.list.d/acestream.list
```

Or to do it from the GUI, try..

```
sudo -H nautilus
```

but be careful with that, a window with root access means you can delete more than you intend if you are not careful.

---

### Post by Robin.sorensen91 on 2015-10-27
> **howefield said:**
> What did you try from the command, it probably should be something like..

```
sudo rm /etc/apt/sources.list.d/acestream.list
```

Or to do it from the GUI, try..

```
sudo -H nautilus
```

but be careful with that, a window with root access means you can delete more than you intend if you are not careful.

First one worked, which is wierd sincei already tried that. Ughh.... 

Thanks ;)

---

### Post by howefield on 2015-10-27
Pressing the up arrow in the terminal will cycle through the command history, so you could go back and check what you typed, possibly a typo in you command.

Anyway, glad you are sorted.

---

