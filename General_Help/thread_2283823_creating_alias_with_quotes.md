---
title: "creating alias with quotes"
date: 2015-06-24
forum: General Help
---

### Post by alex408 on 2015-06-24
I am new to the community and the whole bash thing as well, so I'd love to know if there is a simple soluton.

I have a complex command I run all the time that looks like
```
$ command --opt1 --opt2='blah' argument1
```
and aliases follow this syntax
```
$ alias name='long_command_here'
```
but combining the two didn't work for me.
```
$ alias name='command --opt1 --opt2='blah' argument1'
```

I think I have to escape out some of the special characters, like the single backquotes. Any ideas?

---

### Post by Dennis N on 2015-06-24
I use double and single quotes when there are nested pairs of quotes like this. Otherwise, it won't be parsed correctly.

Try this:

```
alias name="command --opt1 --opt2='blah' argument1"
```

---

