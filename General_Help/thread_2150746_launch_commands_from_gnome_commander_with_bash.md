---
title: "launch commands from gnome commander with bash"
date: 2013-06-02
forum: General Help
---

### Post by pogorodnikov on 2013-06-02
Hi,

I wish to launch commands from a file manager since it conveniently sets working directory. I try gnome commander. Hence I have two questions.
First, if I happen to hit Enter key after I issue a command which prompts for some text input, like sudo, it starts without a terminal and I  never get to it. What happens to that process and what should I do about  it?
Second, if I launch a command with Shift+Enter, then it starts in a new  terminal. I can see program output and interact with it, but I never  know when it finishes because it does not return to shell. I would like to have bash started  in same terminal when a program finishes. For this, I try the following  command for a terminal in gnome commander's settings:  ```
gnome-terminal --execute bash -c '%s ; bash'
``` But this does not  work for commands with arguments. How do I make this work?

---

