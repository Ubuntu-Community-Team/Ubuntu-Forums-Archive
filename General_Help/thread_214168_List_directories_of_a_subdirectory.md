---
title: "List directories of a subdirectory"
date: 2006-07-12
forum: General Help
---

### Post by mlind on 2006-07-12
This one was giving me hard time today. I went though all find and ls parameters, even tried grepping. Finally got it sorted somehow.


For example, list subdirectories (only) of a ~/Examples directory
```

ls -d ~/Examples/*/

```

Looks kinda akward..

---

### Post by glinsvad on 2006-07-12
To do it recursively one would expect that adding -R should work, but somehow it doesn't.

To list (sub-)directories of a path recursively you could do:
```

find ~/Examples -type d

```

---

### Post by jayemef on 2006-07-12
And with zsh globbing you can use
```
$ ls -d ~/Examples/**/*(/)
```

**: recursive search
*: wildcard
(/): return only directories


What's really cool is that if you hit tab before hitting enter, your glob will be replaced by all the given directories. For example, if you had the subdirectories temp1, temp2, and temp3, your prompt might look like
```
$ ls -d ~/Examples/temp1 ~/Examples/temp2 ~/Examples/temp3
```
This doesn't really mean anything with the ls command, but if the purpose of finding these directories was to do something with them with a different command, you could just start with that command, enter your glob, and hit tab to have the command you intended right there in front of you. The tab is unnecessary, as the command would get executed in exactly the same way regardless, but it gives you the opportunity to double-check that you are doing what you intend.

---

### Post by mlind on 2006-07-12
> **jayemef said:**
> And with zsh globbing you can use
```
$ ls -d ~/Examples/**/*(/)
```

**: recursive search
*: wildcard
(/): return only directories


What's really cool is that if you hit tab before hitting enter, your glob will be replaced by all the given directories. For example, if you had the subdirectories temp1, temp2, and temp3, your prompt might look like
```
$ ls -d ~/Examples/temp1 ~/Examples/temp2 ~/Examples/temp3
```
This doesn't really mean anything with the ls command, but if the purpose of finding these directories was to do something with them with a different command, you could just start with that command, enter your glob, and hit tab to have the command you intended right there in front of you. The tab is unnecessary, as the command would get executed in exactly the same way regardless, but it gives you the opportunity to double-check that you are doing what you intend.

That works only on zsh shell ?

---

### Post by jayemef on 2006-07-12
Yes -- globbing is one of zsh's features, basically eliminating the need to use find/grep/sed. I know ksh is supposed to be its closest relative, but I haven't used it, so I'm not sure whether it has this as well. My guess though is that it does not.

---

