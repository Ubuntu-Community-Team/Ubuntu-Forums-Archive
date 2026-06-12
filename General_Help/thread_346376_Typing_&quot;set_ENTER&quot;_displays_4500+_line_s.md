---
title: "Typing &quot;set ENTER&quot; displays 4500+ line script!"
date: 2007-01-25
forum: General Help
---

### Post by Phrawm48 on 2007-01-25
Per the attached, gz'ed text file.

For 2.6.15-27-386, Ubuntu 6.06 / Kubuntu 3.5, typing "set" followed by RETURN produces a 4500+ line output that includes a VERY lengthy script.  I also logged off and used the Console login to produce the same incredibly long output.

This seems to be an incorrect configuration (why a HUGE script in my "set" variables?) but I have no idea where to begin isolating this.

Does anyone have any idea what's going on and how I can best remedy it?

Cheers & thanks,
Ric
SFO

---

### Post by HadroLepton on 2007-01-25
those 4500 lines are from the bash advanced completion scripts (that what happens when you press tab in the shell). typing set will print all environment variables and all environment function from the shell, that includes those functions, and that are many many many functions.

you can verify this by editing your .bashrc and disable following line
```
. /etc/bash_completion
```
then restart the shell and type set. but now some of the tab completion doesn't work anymore.

there is another command to show the environment variables: **printenv** or **env**

the output from printenv and env seem to be identical, but different to that from set. i asume set lists the bash variables while printenv lists the environment variables. note that set is a bash builtin command while printenv is a "stand-alone" command.

---

### Post by Phrawm48 on 2007-01-25
H:

Thanks for the reply -- I tried the different CLI commands and can see the difference.

It remains a bit counterintuitive to me that "set" would produce this huge output.  I guess I expect that bash would internalize the auto-completion values rather than put the all in-line in a 4500+ line script...

Neverthless, if that's the way it's intended to work, so be it.

Cheers, thanks 'gain, & take care,
Ric
SFO

---

### Post by jim h on 2007-02-02
I got this by surprise, too, and I thought bash was broken.  Wasted a bunch of time trying to figure out what was going on.   But the "env" clue was great and solves the problem, so my thanks to HadroLepton for that.

---

