---
title: "Annoying file called &quot;%1&quot; automatically generated when navigating directories"
date: 2024-01-23
forum: General Help
---

### Post by nunonun2 on 2024-01-23
Hello

I'm using KUbuntu 22.04 LTS and I've noticed that there is an empty file called "%1" which is randomly generated in many folders. I have noticed that it is created whenever I open Dolphin and press F4 to open a terminal, but I think it is also created under other circumstances that I haven't identified yet.

How can I prevent these files from being created?

---

### Post by nunonun2 on 2024-01-23
I found the problem. It was a typo in my **.zshrc**, in the `agent_run_state` variable (a "%" instead of an "&").
In case it helps somebody, the code should be:

```

agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

```

---

