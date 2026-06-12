---
title: "Odd issue with grep command from CLI"
date: 2019-02-28
forum: General Help
---

### Post by darkhobbo on 2019-02-28
Hello!

I'm running Ubuntu 18.04 Desktop on another machine, and I am SSHing into this machine from my main computer.

I've noticed the following issue and it is really annoying and I'm not sure how it came about. This issue is only prevalent on the a user called greg on the target machine.

Here is what is happening:
```

greg@phoebe:~$ printf "Hello\nWorld\n" | grep "World"


Command 'greg' not found, did you mean:


  command 'gfreg' from deb gfarm-client
  command 'preg' from deb emboss
  command 'grig' from deb grig
  command 'dreg' from deb emboss
  command 'grep' from deb grep
  command 'grog' from deb groff-base
  command 'geg' from deb geg


Try: sudo apt install <deb name>

```

I can do this same command on another user, and I have no problems.

```

operations@phoebe:~$ printf "Hello\nWorld\n" | grep "World"
World

```

Has anyone seen this before? I'm wondering if the user's name is causing some issues?

Cheers,
Greg

---

### Post by darkhobbo on 2019-02-28
Shoot, I discovered the issue after digging. Somehow I had aliased the command in my `.bashrc`. 

This issue is now resolved.

---

