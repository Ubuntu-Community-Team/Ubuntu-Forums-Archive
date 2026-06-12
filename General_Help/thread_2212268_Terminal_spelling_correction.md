---
title: "Terminal spelling correction"
date: 2014-03-20
forum: General Help
---

### Post by RedPandaFox on 2014-03-20
G'day,

Quick question for something that has been bugging me for a while. When I am trying into the terminal and attempt to type "apt-get", I constantly hit "apt0get".

Is there a way to have the terminal auto-correct this error as it would save me a small headache.
inb4: "search before posting". Had a quick browse but don't believe I could find anything probably as the searches I used were very vague.

Thanks

---

### Post by btindie on 2014-03-20
You could add to your ~/.bash_aliases file
```
alias apt0get='apt-get'
```
it won't correct your typing mistake but it will run the correct program.

---

### Post by Dave_L on 2014-03-20
A partial solution is to use the TAB key, which does auto-completion.
Type the first few characters, press TAB once or twice, and it will attempt to fill in the rest of the command.

Or you can use Ctrl+r to recall previously typed commands from the history file.

---

