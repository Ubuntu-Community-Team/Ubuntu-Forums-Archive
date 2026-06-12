---
title: "Auto suggestion for aliases"
date: 2015-07-18
forum: General Help
---

### Post by peter1897 on 2015-07-18
In openoffice you can predefine words and when you start typing the first letters of a word it start showing suggestions if there is a match from the predefined words and then you can press the space key to accept the suggested word.
Is it possible something like this to be implemented for bash aliases with a script?

---

### Post by sudodus on 2015-07-18
It exists already, and works for executable files (binary programs as well as shell-scripts) and also for aliases.

Type the beginning of the name and press the TAB key. If there is one unique completion, it will be written (to the terminal window). If there are several alternatives, the common complettion will be written, and if you press the TAB key again, a list of the available alternatives will be written. It is called 'bash-completion', and you can find more information about it via the internet or in ```
man bash
```

Notice: it is already there in Ubuntu's terminal windows and text screens, wherever bash is used.

---

### Post by peter1897 on 2015-07-18
My question is about suggestions for aliases created only by the user in .bash_alias file. Now if i type the fist letters and press TAB it shows suggestions for all available commands.

---

### Post by sudodus on 2015-07-18
Yes, all commands, including the aliases. I think that is how it should be.

You can list your aliases with the command ***alias*** (without any parameter), or with for example

```
alias b TAB
```

to get the aliases that begin with b. Maybe that's what you want?

---

### Post by peter1897 on 2015-07-18
I didn't know about** alias b TAB** so that will be useful for me.

I am asking about something like this:

[[IMG]http://i.imgur.com/kd5YRdil.jpg[/IMG]]("http://i.imgur.com/kd5YRdi.gif")

As you can see from the picture you just press a letter and the suggestion appear and if you want to select it you can press the spacebar, that should move the cursor to the end of the command and then you can press Enter to execute it.

---

