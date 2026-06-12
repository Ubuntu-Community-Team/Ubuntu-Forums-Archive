---
title: "color coding terminals in ksh"
date: 2015-01-21
forum: General Help
---

### Post by keith14 on 2015-01-21
Hi,
  Switching OS from bash (dflt) to ksh the color scheme used in terminals is lost.
I like ksh and would also like to re-assert the color scheme deployed in bash
terminal windows. After several queries on line it seems like color and ksh don't
mix. I am using 14.04 version.
thanks,
keith

---

### Post by schragge on 2015-01-21
Color scheme has nothing to do with the shell being used. I'm not sure what you *really* mean by this. That the settings in *~/.bashrc* and/or *~/.bash_profile* for color prompt and similar things don't get respected by ksh? Quite understandable because ksh doesn't use these startup files at all. Or that ANSI color escape sequences don't work in ksh quite the same way they work in bash? If you show us an example of what doesn't work, I'm sure somebody here will point out what's wrong with your code.

On an unrelated note, while I think ksh is a great shell for scripting purposes, IMHO bash/zsh/yash, and even tcsh are better suited as interactive/login shells because of programmable completion.

---

### Post by ajgreeny on 2015-01-21
Is there a file similar to ~/.bashrc called ~/.kshrc in your home that has all the configuration for ksh?

I have always used the default, bash, so I am asking this question because I do not know the answer myself.

---

### Post by schragge on 2015-01-21
It depends on what ksh flavor is used. The startup file is *~/.kshrc* for ksh93, but *~/.mkshrc* for mksh. For both shells, it only gets executed if $ENV is not defined, otherwise the file pointed to by $ENV gets executed on startup instead.

---

### Post by keith14 on 2015-01-21
Ok, I've looked at the .kshrc but there are no entries dealing with color, it is very short uncommented file and looks like I may have put it in place.
The .bashrc file also short w/o color assignments; its there but not doing anything.
 The ksh and ksh93 are same if I remember correctly it linked around to only use ksh93. I am currently using a laptop that floats Mint,rebecca (ubuntu 14.04) .
The pc with ubuntu 14.1 is not available at moment. It will be soon.
 Sometime ago I redirected bash OS to ksh there as well and experienced the same terminal color loss. I may not remember correctly.
I will revisit pc with straight ubuntu OS this weekend and update.
thanks,
keith

---

### Post by schragge on 2015-01-22
You may have had alias definitions like
```
alias ls='ls --color=auto'
```
either directly in *~/.bashrc* or in some file like *~/.bash_aliases* that got sourced from *~/.bashrc*.

Does ```
ls --color=auto
``` still work if invoked manually?

---

### Post by keith14 on 2015-01-23
Hi,
 Yes exactly what I lost changing OS to ksh. Nice! I've been using ls for 30+ with a handful of options, don't remember color ever being a selection (recent man on it showed many options I never messed with).
Color is not addressed in .bashrc file in $HOME, where was the alias made? I don't use bash any more but it is info on how things were set-up initially. I have done little to the initial environment other than change OS to ksh.
thanks,
keith

---

### Post by Holger_Gehrke on 2015-01-23
You must have removed those definitions. On my system they are in '~/.bashrc' (and I didn't put them there). They should still be in '/etc/skel/.bashrc', together with a call to 'dircolors', which either takes the definitions from '~/.dircolors' or uses the defaults built into 'dircolors' and puts them into the environment as LS_COLORS. And yes, this implies that you can change the color scheme.

---

