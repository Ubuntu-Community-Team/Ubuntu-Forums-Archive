---
title: "running programs without './'"
date: 2008-06-21
forum: General Help
---

### Post by Sadistic Tribble on 2008-06-21
Is there any way in Ubuntu, or other distros for that matter, to create a program that can be run without using the ./ command in the Terminal?

---

### Post by babylon2233 on 2008-06-21
You have to put it inside /usr/bin/ directory or just export your path.

---

### Post by sdennie on 2008-06-21
The best way to do this is to put your custom scripts/programs in in ~/bin and add /home/your_username/bin to the PATH.  To do the latter, edit ~/.bashrc and, at the bottom add:

```

export PATH=/home/your_username/bin:${PATH}

```

Then in a terminal type:

```

mkdir ~/bin

```

The next time you start a terminal, any programs in ~/bin will run without having to specify a path.

You can also add "." to the PATH so that you never have to type ./some_program but, I don't actually recommend that because it's not a good habit to get into.

---

### Post by VMC on 2008-06-21
> **vor said:**
> The best way to do this is to put your custom scripts/programs in in ~/bin and add /home/your_username/bin to the PATH.  To do the latter, edit ~/.bashrc and, at the bottom add:

```

export PATH=/home/your_username/bin:${PATH}

```

Then in a terminal type:

```

mkdir ~/bin

```

The next time you start a terminal, any programs in ~/bin will run without having to specify a path.

You can also add "." to the PATH so that you never have to type ./some_program but, I don't actually recommend that because it's not a good habit to get into.

Also to make sure you didn't make any mistakes after you make the above changes.
Type this into Terminal to show your path:

```
echo $PATH
```

It's beginner stuff.

---

### Post by bodhi.zazen on 2008-06-21
Nice one vor :)

I use this :

```
    # Set PATH to include a user's private bin
    if [ -d "${HOME}/bin" ] ; then
      export PATH=${HOME}/bin:${PATH}
    fi
```

Put that in ~/.bashrc

It will be active next time you open a shell

To use immediately you can either 

```
. ~/.bashrc #Watch the initial . <space>
```

or 

```
export PATH=${HOME}/bin:${PATH}
```

---

### Post by Habbit on 2008-06-21
> **bodhi.zazen said:**
> ```
. ~/.bashrc #Watch the initial . <space>
```

:lolflag:You could have just written> source ~/.bashrc
and you wouldn't have had to put any "watch for the invisible but required dot" signs. Sometimes more is less and viceversa :KS

---

### Post by bodhi.zazen on 2008-06-21
:lolflag:

yea, would save on typing on the forums for sure, but I use . @ the terminal to save on typing and figured I could teach someone something, so the extra typing was worth the extra effort.

---

