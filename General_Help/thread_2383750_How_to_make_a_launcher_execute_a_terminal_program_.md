---
title: "How to make a launcher execute a terminal program and then persist"
date: 2018-01-29
forum: General Help
---

### Post by galacticstone on 2018-01-29
Hi Folks,

I want to make a launcher button to open a terminal and run the Neofetch program. However, when I tried doing this, the launcher would work, but the terminal window only stayed open for a second and then it disappeared. How can I make a launcher button that will display the information until I close it? (instead of immediately closing on it's own).

Thanks in advance!

MikeG

---

### Post by vasa1 on 2018-01-29
> **galacticstone said:**
> Hi Folks,

I want to make a launcher button to open a terminal and run the Neofetch program. However, when I tried doing this, the launcher would work, but the terminal window only stayed open for a second and then it disappeared. How can I make a launcher button that will display the information until I close it? (instead of immediately closing on it's own).

Thanks in advance!

MikeG
You could share the code for the launcher you made in case there's something someone may notice.

---

### Post by kostkon on 2018-01-29
Have you set the Terminal entry in your .desktop file to True? i.e.:
```
Terminal = True
```

---

### Post by sisco311 on 2018-01-29
I would try something like:
```

xfce4-terminal -x bash -c "neofetch && read -sp Press\ Return\ to\ close\ the\ window"

```
or
```
xfce4-terminal -x bash -c "neofetch && read -n1 -sp Press\ any\ key\ to\ close\ the\ window"
```

Of course replace xfce4-terminal with the terminal emulator of your choice.

---

