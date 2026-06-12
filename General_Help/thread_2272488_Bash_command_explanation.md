---
title: "Bash command explanation?"
date: 2015-04-07
forum: General Help
---

### Post by CantankRus on 2015-04-07
This also greps the "--color=auto"  
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] ps x | grep nautilus
 2891 ?        Sl     0:12 nautilus -n
 9507 pts/20   S+     0:00 grep --color=auto nautilus
```

But when the first letter is wrapped in [COLOR="#FF0000"][][/COLOR] the "--color=auto" doesn't show...
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] ps x | grep [COLOR="#FF0000"][[/COLOR]n[COLOR="#FF0000"]][/COLOR]autilus
 2891 ?        Sl     0:12 nautilus -n
```
Can someone explain to me what the [] brackets do in this instance.?

---

### Post by Mark_Hagan on 2015-04-07
Good one!

Does the presence of a regular expression perhaps change when bash forks the process for the grep and so it doesn't actually appear in the ps output? I.e. the grep expression is correct but its own process is not in the output it us grep'ing.

Apologies for hazarding a guess but I couldn't resist it...

---

### Post by Lars Noodén on 2015-04-07
It's like Mark suggests, the pattern [n]autilus matches anything with an 'n' followed immediately by 'autilus'   So it won't match '[n]autilus' because that has ']' followed by 'autilus' but it would match 'xyznautilusabc' if it were there.  

You might look at [pgrep](http://manpages.ubuntu.com/manpages/trusty/en/man1/pgrep.1.html), especially with the -x option.

---

### Post by CantankRus on 2015-04-07
I still don't see how it eliminates the "--color=auto **nautilus**" line.
Is it because the " --color=auto **nautilus**" now literally becomes "--color=auto **[n]autilus**" so is not matched?

Aha, got it. #-o I didn't realize the "--color=auto" was created from the grep statement.
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] ps x | grep **sillyphrase**
26264 pts/0    S+     0:00 grep --color=auto **sillyphrase**
```

Thanks Mark and Lars.

---

### Post by Holger_Gehrke on 2015-04-07
The '--color=auto' option is added by an alias in ~/.bashrc. The literal string '[n]autilus' -- found in the command line field of the output of ps -- does not match the regular expression '[n]autilus', which looks for a character from the set containing only the letter 'n' followed by 'autilus' and finds the 'n' followed by a literal ']'. Another way to do the same thing which might be more obvious, because it doesn't clash with the mor familiar shell syntax would be 'n{1}autilus' -- search for one 'n' followed by 'autilus'.

One more thing: get in the habit of enclosing regex in single quotes, the bash might do some globbing with it otherwise.

---

