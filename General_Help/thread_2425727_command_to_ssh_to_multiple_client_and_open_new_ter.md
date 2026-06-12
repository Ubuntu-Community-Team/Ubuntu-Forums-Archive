---
title: "command to ssh to multiple client and open new terminal"
date: 2019-08-29
forum: General Help
---

### Post by Sbeucxo on 2019-08-29
Dear all,

I am the lucky user of a university HPC cluster for my research. I am a enthusiast Linux user since years but complete new to HPC.
Jobs I launch are spread over multiple nodes and for monitoring reason, I would like to open multiple terminal to the different nodes using ssh
Would there be a command that would ssh to a list of nodes and opens a new terminal for each of them?

Thanks in advance
Sebastien

---

### Post by btindie on 2019-08-29
I'm not aware of anything that does this directly.

You could though script something using *tmux,* the terminal multiplexer. You can get it to create new windows/panes and send commands to them. Realistically though, you'd want to run the job disconnected from the terminal to avoid any potential problems and just tail the log file.

Alternatively, if you just want to run the same commands on multiple hosts, you can use *pssh* 

Also, take a look at [https://www.tecmint.com/run-commands-on-multiple-linux-servers/](https://www.tecmint.com/run-commands-on-multiple-linux-servers/) which has a few suggestions. One of which, clusterssh, may interest you.

---

### Post by TheFu on 2019-08-29
clusterssh is one option. It enters the exact same command into every other system in the cluster.

Might want to script it. Depends on the number of nodes whether that is a good idea. Just add more lines for different systems.  Might want to use a different terminal, IDK.
```
XTERM_OPTS="-u8 -fs 16 -fa Monospace -sb -fg green -bg black"
uxterm -sb -geometry 80x25+0+0 $XTERM_OPTS -e ssh -X hadar &
uxterm -sb -geometry 80x25+760+355 $XTERM_OPTS -e ssh -X romulus &
```

Of course, for managing many machines, there are devops tools like ansible, puppet, chef, cfengine, rexify, salt-stack.  Many of those are worse than just scripting it yourself over ssh, IMHO.  Ansible isn't too bad, but they deprecate things every few years, so it is a constant maintenance nightmare.  OTOH, I have perl5 scripts written in 1994 to manage systems which still work nearly unchanged.

---

### Post by HermanAB on 2019-08-30
There are two types of Parallel SSH in the repos.

---

### Post by Sbeucxo on 2019-08-30
Many thanks to all of you!

---

