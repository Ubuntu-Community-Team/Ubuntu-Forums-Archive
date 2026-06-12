---
title: "shell script that requires super user rights"
date: 2007-02-28
forum: General Help
---

### Post by JermainWijnhard on 2007-02-28
Hi, I have a question. I'm currently doing a tutorial on how to use the terminal and im now in a chapter about scripting. But i've bumped into the following situation: 

I need to make a script that can output an HTML file with info about my system. One of the things needed is a check for root.

```

if [ $(id -u) = "0" ]; then
    echo "superuser"
fi
```

Now this tutorial was (i think) not thinking about ubuntu users. Because the test would always get a false because the sudo command is not given. Does anyone know what to do in this case?

For more info this is the [link ]("http://www.linuxcommand.org/wss0090.php")i've used for the tutorial. All and any help is welcome.

---

### Post by nereid on 2007-02-28
You could check the output of the groups command wether the user is in the admin group or not.

---

### Post by JermainWijnhard on 2007-02-28
> **nereid said:**
> You could check the output of the groups command wether the user is in the admin group or not.

But the result should always show that im not the superuser right? I mean whenever i do something that requires a superuser, I fill in my sudo pass and after the command is done, I'm immediately a normal user again. The thing im getting at is that there is no super user, there is sudo :/

---

### Post by Ramses de Norre on 2007-02-28
If the script is ran with sudo, id -u will return 0 as if it was run by root itself. There is no difference between running something from a root prompt or from a user prompt with sudo.

```
ramses@icarus:/usr/lib/frostwire$ id -u
1000
ramses@icarus:/usr/lib/frostwire$ sudo id -u
0

```

You'd see _a lot_ of apps/scripts fail if this didn't work.

---

### Post by JermainWijnhard on 2007-03-01
Oh i see, thank you :)

---

### Post by nereid on 2007-03-01
With the groups option I meant, that you could check the output and if the user was in the admin group, than he would have the right to become root.

---

### Post by Ramses de Norre on 2007-03-02
> **nereid said:**
> With the groups option I meant, that you could check the output and if the user was in the admin group, than he would have the right to become root.

But he shouldn't be granted root privileges until he actually gives his password.

---

### Post by nereid on 2007-03-02
No, but he can check this way if a user is allowed to become root in Ubuntu.

---

### Post by Ramses de Norre on 2007-03-02
It wont always work... On my machine I took out the admin line and made a new line granting superuser privileges only to me. So on my machine, for example, your solution wont work.

---

### Post by nereid on 2007-03-02
No, but who does things like that? That is for what the admin group exists.

---

### Post by JermainWijnhard on 2007-03-05
Hmm,.. but the piece of code is part of a bigger script. The big idea behind whe whole script it is this:

Make an HTML file, show info about the computer in that file. For those bits of information that root is needed, do a check. If the person has root, show info, if the peron has no root, write "you have no root."

Now all the seperate parts (codes and functions) work in the CLI, but in the HTML output it does the check for root, but it doesn't ask for sudo, so it will always say "you have no root".

---

