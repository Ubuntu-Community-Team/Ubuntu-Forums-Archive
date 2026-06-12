---
title: "bash &quot;apt-get install&quot; suggestion - can I remove?"
date: 2008-01-25
forum: General Help
---

### Post by draeath on 2008-01-25
While nothing but a nit-pick and annoyance...

Just now, I typoed "screen" and bash gave me this:

> draeath@epicenter:~/devel/asc-2.0.1.0$ screem
The program 'screem' is currently not installed.  You can install it by typing:
sudo apt-get install screem
bash: screem: command not found


Can I remove that nonsense about apt-get? I want a plain old "bash: foo: command not found"

---

### Post by LaRoza on 2008-01-25
> **draeath said:**
> While nothing but a nit-pick and annoyance...

Just now, I typoed "screen" and bash gave me this:

Can I remove that nonsense about apt-get? I want a plain old "bash: foo: command not found"

"screem" is an actual program. It doesn't give that option for every command, only if it knows it is a program that can be installed.

---

### Post by draeath on 2008-01-25
I had figured that, but I would like to completely remove the check... it's wasting resources/time doing said check.

If at all possible...

---

### Post by arvevans on 2008-01-25
The purpose of the check is to tell you if you try to execute a command that does exist but is not yet installed, that you can install it.  The resources wasted by the check are pretty inconsequential.  If you type a command that really does not exist, then you will get the more familiar "Command Not Found" type response.

For Example:
[INDENT]arv@arv-desktop:~$ aap
The program 'aap' is currently not installed.  You can install it by typing:
sudo apt-get install aap
bash: aap: command not found
arv@arv-desktop:~$ 
arv@arv-desktop:~$ abc
bash: abc: command not found
arv@arv-desktop:~$[/INDENT]

"aap" is a real command, but just not installed on this computer.
"abc" is not a real command (at least not in the repositories that this computer knows about).

If you really wish to have the old UNIX style command response you can use "sh" instead of bash, as shown below.

[INDENT]arv@arv-desktop:~$ sh 
$ aap
sh: aap: not found
$ abc
sh: abc: not found
$ 
[/INDENT]

You would do this by editing your profile to launch "sh" instead of "bash".

Hope this helps.
Arv
_._

---

### Post by bwtranch on 2008-01-25
jim@jim-desktop:~$ sh
sh-3.2$

---

### Post by bodhi.zazen on 2008-01-25
> **draeath said:**
> I had figured that, but I would like to completely remove the check... it's wasting resources/time doing said check.

If at all possible...

LOL

Try:

```
sudo apt-get remove --purge command-not-found
```

[http://packages.ubuntu.com/feisty/admin/command-not-found](http://packages.ubuntu.com/feisty/admin/command-not-found)

You may need to re-install bash and / or start a new bash shell (terminal) or even log off and back on.

---

