---
title: "SSH and bash prompts"
date: 2007-12-20
forum: General Help
---

### Post by dmonkey on 2007-12-20
Hi,

I don't consider myself a noob, but I'm stuck. When I open a terminal, I have configured /etc/bash.bashrc so that I get a nice coloured prompt. This also works when I login as root. Now, when I SSH into another computer, I would like this prompt to stay the same, but this doesn't happen. Instead, SSH seems to read the bash.bashrc file from the remote computer.

My question is, how do I get my prompt to be consistent across SSH sessions?

---

### Post by cyberdork33 on 2007-12-20
logging in through ssh is like opening a terminal on the physical machine, so bash reads its config file, not the config file on your client machine.

---

### Post by dmonkey on 2007-12-20
So are you saying that this isn't possible? I thought there was a way to change this so that SSH always reads my local file.

---

