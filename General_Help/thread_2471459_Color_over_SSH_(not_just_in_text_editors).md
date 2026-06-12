---
title: "Color over SSH (not just in text editors)"
date: 2022-01-31
forum: General Help
---

### Post by tobias-richards on 2022-01-31
Emacs is my editor of choice. Sue me. Over SSH, I see all the relevant colors in emacs. What I don't see is bright green for executable, light blue for symlink, dark blue for directory. How can I see those colors over SSH whether from Linux, xBSD, Mac, Windows (putty/kitty) or other? I currently see no colors when running ls over any of these SSH clients. Yes, my SSH clients support color. I told you guys that I see colors in emacs.

No, ls --color or such thing is not what I want. I want to run ls with no extras, and see color from any SSH client that supports color.

---

### Post by The Cog on 2022-01-31
Have a read of ~/.bashrc on your local PC. There is a lot of colour manipulation in there, deciding when to show colour or not. 
Also note this in "man ls":
> Using color to distinguish file types is disabled both by default and with --color=never.  With --color=auto, ls emits color codes only when standard output is connected to a terminal.  The  LS_COL&#8208;
       ORS environment variable can change the settings.  Use the dircolors command to set it.
I suspect that you never actually run ls with no extras.

---

### Post by Impavidus on 2022-01-31
From ls' man page:```

       --color[=WHEN]
              colorize  the output; WHEN can be 'always' (default if omitted),
              'auto', or 'never'; more info below

(...)

       Using  color  to distinguish file types is disabled both by default and
       with --color=never.  With --color=auto, ls emits color codes only  when
       standard  output is connected to a terminal.  The LS_COLORS environment
       variable can change the settings.  Use the dircolors command to set it.

```When you create your user during Ubuntu install, you get a number of aliases automatically:```
$ alias
(...)
alias ls='ls --color=auto'

```So by default, ls runs with --color=auto, which will show colours when your use it directly on a terminal, but not when redirecting the output to a file, a pipe to a different tool or to ssh. You can change this by changing the alias, but then it will also use colours when writing to a file and there are tools that may be broken by such behaviour.

---

### Post by ActionParsnip on 2022-01-31
have you edited your ~/.bashrc file? If not then if you run
```

source ~/.bashrc

```
Does it work OK?

---

