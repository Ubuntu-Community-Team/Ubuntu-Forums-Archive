---
title: "Run function in tmux"
date: 2014-03-23
forum: General Help
---

### Post by demontager on 2014-03-23
My bash script has some functions and i need one tmux pane to execute function within bash script. For example below code won't work and will be reported that command "internal" not found.
```

common() {
internal() {
echo "Function executed"
}   

SESSIONNAME="ses"

tmux new-session -s $SESSIONNAME -n session -d
tmux split-window -t $SESSIONNAME:0 -h

tmux send-keys 'internal' 'C-m'
tmux select-window -t $SESSIONNAME:0
tmux attach -t $SESSIONNAME
}

```
So how may i tell tmux to execute function from script where tmux pane was invoked ?

---

### Post by Lars Noodén on 2014-03-23
Maybe you could add the function to .bashrc.  But that could be a bit heavy-handed.

---

### Post by demontager on 2014-03-23
Yes, i know it will work from .bashrc and yes will  be more actions, like adding function to .bashrc. Hope  it is still somehow possible within one script.

---

### Post by demontager on 2014-03-23
I made one workaround. When tmux executed also one pane in it executes temporary script /tmp.  And i also need a way to kill and exit tmux in that pane. Tried to put this in script
```
kill $(ps aux|grep '[t]mux'|awk '{print $2}')
```
 But after kiiling all panes again restored

---

