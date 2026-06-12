---
title: "rsync command not working"
date: 2024-02-06
forum: General Help
---

### Post by umangwah67 on 2024-02-06
hey all
[FONT=Söhne Mono, Monaco, Andale Mono, Ubuntu Mono, monospace][COLOR=#111827]**rsync, this mention command is not working properly, alternative for synchronizing files between directories and systems.?**[/COLOR][/FONT]

---

### Post by The Cog on 2024-02-06
I don't think there are any known bugs in rsync. I think we need a lot more detail about what you are having problems with before we can even thing about helping with a solution. The exact command you are using, the type of source and destination, and what is going wrong.

---

### Post by MAFoElffen on 2024-02-06
+1 ---
Like exactly what command, with all options you used, from which directory, with a listing of the target directory to see if there was something there already... and the output of any errors...

Just saying "it didn't work" doesn't tell us how it failed.

Now if, rather, it did work, but you do not 'like' the results, and want to use something else, that is another matter we can address. Unfortunately, most backup options are rsync based. LOL. But there are options.

---

### Post by dragonfly41 on 2024-02-06
If
(a) you install grsync (the GUI wrapper of rsync)
(b) go to GUI File > Preferences and tick 
“Show error list when finished”
"Enable Logging"
(c) in Advanced Options tick "Show itemised changes list"
there might be more clues to diagnose issues.

---

### Post by SeijiSensei on 2024-02-06
rsync is fussy about file specifications. Did you read the manual page?

[https://linux.die.net/man/1/rsync](https://linux.die.net/man/1/rsync)

Did you run the command with the -v switch, e.g.,
```
rsync -av source target
```

Did you run the command with sudo so you can copy all directories?

---

### Post by TheFu on 2024-02-07
> **umangwah67 said:**
> hey all
rsync, this mention command is not working properly, alternative for synchronizing files between directories and systems.?

Post the exact command.  You can also post the command to an online explainer -  [https://explainshell.com/](https://explainshell.com/) to have it explain each option using the public manpages.  There is a slight risk that your version of rsync is different, but rsync is fairly stable.

BTW, your post is specifying a font and color, which is odd.  I've removed that formatting in my quote. The default fonts and color are best, unless there is a specific thing you want to highlight.

When posting terminal commands, best to use the Advanced Editor and the '#' code-tag format.

Almost always, issues with rsync are due to a misunderstanding.

---

