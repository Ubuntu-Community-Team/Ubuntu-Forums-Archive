---
title: "Bash completion broken when completing with equal sign"
date: 2014-03-23
forum: General Help
---

### Post by rparree on 2014-03-23
Hi,

Since a while my tab completion no longer works. At first i thought i was my own custom completion i created, but also when removing my own script it does no longer work as before.

The problem is simple:

```

$ export A=/<tab>
$ export /

```

SO when i type the tab key after the equal sign, the equal sign gets removed and i only see the value (in this case what i have typed so far: the /"

Any clues.

tx.,

---

### Post by ajgreeny on 2014-03-23
You need to escape the = with a \ as if it were, for example, a space.
```
$ export A\=/<tab>
```

---

### Post by rparree on 2014-05-09
Hi,

Thanks for your response. I have never had to do that. I gave it a try anyway, but the problem is still there.

```
$ export ABC=/[TAB]
``` --becomes--> ```
$ export /
```

Same with "escaping" the =

---

### Post by Habitual on 2014-05-09
not going to work.

---

### Post by rparree on 2014-05-30
HI

What do you mean it is not going to work. It has worked for years, just suddenly it stopped. Note that under *bash --norc *it works.

tx.,

---

### Post by steeldriver on 2014-05-30
Your 'export ABC=/' example works for me as well (12.04, bash version 4.2.25(1)-release) - specifically it offers the contents of / as completions

Maybe you can narrow down the source of the issue by temporarily replacing your ~/.bashrc with the default one from /etc/skel, then doing the same for ~/.profile and so on up the rc file 'hierarchy'

---

### Post by brian_woods on 2014-05-30
I agree with rparree . It would work.

---

### Post by rparree on 2014-07-29
I found the problem. It was a completion script from Node's npm: [http://stackoverflow.com/questions/20365372/bash-completion-for-path-in-argument-with-equals-sign-present/25010080#25010080](http://stackoverflow.com/questions/20365372/bash-completion-for-path-in-argument-with-equals-sign-present/25010080#25010080)

---

