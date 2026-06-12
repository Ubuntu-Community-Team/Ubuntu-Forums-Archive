---
title: "gnu screen startup automation"
date: 2013-05-25
forum: General Help
---

### Post by HiImTye on 2013-05-25
I was wondering if there was a way to specify commands to run on a new window in screen, such as the motd in a regular terminal session. simply adding a command causes screen to run it and then terminate

---

### Post by hardmath on 2013-05-25
Try the example described in [the accepted StackOverflow answer here]("http://stackoverflow.com/q/7585069/487781").  Basically you put the startup command you want in ~/.screenrc, as you seem to have tried.  However a bash command alone will quickly exit, hence the need for something extra.

If you want to start a screen session with a customized command, then:

[FONT=Courier New]screen -c ~/.screenrc-custom[/FONT]

---

### Post by HiImTye on 2013-05-25
it didn't work, just terminated as expected
this also didn't work in .screenrc
```
screen -D -R -S tye
screen -S tye -X exec ~/Launchers/checkUpdates
```
results in```
invalid option -D
invalid option -R
invalid option -S
cannot exec 'tye'
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by HiImTye on 2013-06-08
I switched to tmux, but I solved it by adding ```
# -- tmux section --
# check if we're in it
if [ -n "$TMUX" ]; then
 # yes, run our automation
 alias exit="history -c; exit"
 checkUpdates
else
 alias exit="history -c; if [ -f $HOME/.bash_history ]; then rm $HOME/.bash_history; fi; if [ -f $HOME/.lesshst ]; then rm $HOME/.lesshst; fi; exit"
 w0="$(ps -ef | grep tmux | grep -v grep)"
 # check if tmux is running
 if [ -n "$w0" ]; then
  # yes, attach
  tmux -u attach
 else
  # no, start a new session
  tmux -u
 fi 
fi
``` to```
$HOME/.bashrc
```I suspect that it could work similarly for screen.
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

