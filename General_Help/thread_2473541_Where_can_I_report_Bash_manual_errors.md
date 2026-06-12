---
title: "Where can I report Bash manual errors?"
date: 2022-04-07
forum: General Help
---

### Post by Paddy Landau on 2022-04-07
I found a couple of (minor) errors in the Bash manual.

Go to [FONT=courier new]man bash[/FONT].

[HR][/HR]
1. Search for [FONT=courier new]OPTIONS[/FONT] (right at the start of the manual).

The option [FONT=courier new]-n[/FONT] is missing. Although it is mentioned in a few places, it should be included in the list of options.

[HR][/HR]
2. Search for [FONT=courier new]INVOCATION[/FONT] (near the top).

In that section is a paragraph containing the explanation, "&#8230; it reads and executes commands from ~/.bashrc and ~/.bashrc."

Obviously, there shouldn't be two files the same. An [online manual]("https://linux.die.net/man/1/bash") indicates that it should be just the one :)

[HR][/HR]
I found this in both Ubuntu 20.04 and 21.10.

Where can I report these so that they can be corrected?

---

### Post by oldos2er on 2022-04-07
The info from ```
man bash
``` says ```
Comments and bug reports concerning this manual page  should  be  directed  to
       chet.ramey@case.edu.
```

---

### Post by Paddy Landau on 2022-04-07
> **oldos2er said:**
> Comments and bug reports concerning this manual page  should  be  directed  to…
I didn't think of looking at the end of the Bash manual! It should have been obvious :redface:

Thank you :)

---

### Post by Paddy Landau on 2022-04-08
Update: I emailed Chet Ramey, and had these two responses.

[LIST]
[*]The start of the OPTIONS section says that all of the options in the [FONT=courier new]set[/FONT] command can also be used. That includes [FONT=courier new]-n[/FONT].
[*]The repeated file was introduced in Debian, which Ubuntu has inherited.
[/LIST]
So, that solves this missing option.

Regarding Debian's introduced bug, do you know where I should report this?

Thank you

---

### Post by ks-alexandr on 2022-04-08
To send a bug report to any package supported by Canonical, you need two things:
1. Launchpad account [https://launchpad.net/](https://launchpad.net/)
2. Execute in the terminal:
```
ubuntu-bug PACKAGE-NAME
```
and follow the instructions.

By doing bug reports, you are helping to make Ubuntu better.

---

### Post by Paddy Landau on 2022-04-08
> **ks-alexandr said:**
> ubuntu-bug PACKAGE-NAME
Thanks. I've created [the bug report]("https://bugs.launchpad.net/ubuntu/+source/bash/+bug/1968313"). Please vote for it if you agree (the green writing at the top left).

---

