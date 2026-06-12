---
title: "Copy line in editors"
date: 2018-03-02
forum: General Help
---

### Post by ordak on 2018-03-02
Hi,

Is there a way to copy a whole line in various editors ?
I ask because I have several commands stored in files . I want to run them via terminal easily.

---

### Post by amanchesterman on 2018-03-02
In Geany, triple-click selects all the text from the start of a line to the next line break. (double-click selects to the next space.) You can then copy and paste as usual.

---

### Post by SeijiSensei on 2018-03-02
Most terminal applications let you highlight text on-screen and use copy/paste.  Just display the file you want to use with a command like more, highlight and copy the line you want, and paste it at the terminal prompt.

---

### Post by HermanAB on 2018-03-02
Triple click and middle click.

---

### Post by ordak on 2018-03-03
> **amanchesterman said:**
> In Geany, triple-click selects all the text from the start of a line to the next line break. (double-click selects to the next space.) You can then copy and paste as usual.

What about adding a right click choice "Copy this line" in editors. The job seems to be done with less effort this way.

---

### Post by The Cog on 2018-03-03
Triple-click seems easier to me, and seems to work pretty-much everywhere already. I guess it's built into the GUI components so it doesn't have to be written into each app individually.

---

### Post by dragonfly41 on 2018-03-03
> [COLOR=#000000]I ask because I have several commands stored in files . I want to run them via terminal easily.[/COLOR]

How many commands?
There are automation tools you can try if you have a large catalogue of commands to manage.

---

### Post by ordak on 2018-03-03
> **The Cog said:**
> Triple-click seems easier to me, and seems to work pretty-much everywhere already. I guess it's built into the GUI components so it doesn't have to be written into each app individually.

I am already used to single click and double click. If I get used to triple click, I may do it in the wrong place, like computer games.

---

### Post by ordak on 2018-03-03
> **dragonfly41 said:**
> How many commands?
There are automation tools you can try if you have a large catalogue of commands to manage.

The number of commands is not that much. But the mostly used commands are:

```

sudo apt update
sudo apt list --upgradable
sudo apt upgrade

```

---

### Post by HermanAB on 2018-03-03
Triple click, middle click uses a different copy buffer from ctrl-c, ctrl-v.  So you can copy and paste two things, such as a username and a password, at the same time.

---

### Post by Impavidus on 2018-03-03
> **ordak said:**
> The number of commands is not that much. But the mostly used commands are:

```

sudo apt update
sudo apt list --upgradable
sudo apt upgrade

```

I suggest you use aliases. You can put them in your ~/.bashrc or (if you have many) in your ~/.bash_aliases. The default .bashrc already has a few aliases defined and reads more from .bash_aliases if it exists.

---

