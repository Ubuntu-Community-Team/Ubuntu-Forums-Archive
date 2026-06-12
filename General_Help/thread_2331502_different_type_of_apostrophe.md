---
title: "different type of apostrophe"
date: 2016-07-22
forum: General Help
---

### Post by lksjfnvljnfdv on 2016-07-22
Hi,


I'm trying to write a bash script as part of a course i am learning, it's just something basic but if i use a `'` in the code it doesn't work.


It comes up with an error 
bash: syntax error near unexpected token `do'


if i use a ` in the code it does works.


How do i get a  ` instead of a `'` Can't see a way to get a different apostrophe.


(I'm copy and pasting it here, FYI)

---

### Post by steeldriver on 2016-07-22
It will depend on your keyboard layout - on a standard US keyboard it is on the same key as ~

You could also replace the 'backtick' construction by a (more modern) form of command substitution i.e. instead of

```

`command`

```
use
```

$(command)

```

See [http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution)

---

### Post by lksjfnvljnfdv on 2016-07-22
ok i will try that

---

### Post by lksjfnvljnfdv on 2016-07-22
thanks, so from now on where it says use that type of apostrophe i can use the $(something here);

---

### Post by Habitual on 2016-07-22
> **cn-roberts said:**
> thanks, so from now on where it says use that type of apostrophe i can use the $(something here);

Yes. exactly.
And actually, they are called backticks - [COLOR=#ff0000]**`**[/COLOR]
Not to be confused with a single quote. - '
however, your errant script may have one or more issues with either.
eg:
```
for i in[COLOR=#ff0000] **`**[/COLOR]seq 1 100**[COLOR=#ff0000]`[/COLOR] **; do echo $i ; done
``` is still valid, (backticks are to be deprecated says info, but no one knows when)
but it should also be written using
```
for i in $(seq 1 100); do echo $i ; done
```

Want some Links? ;)
Have Fun!

---

