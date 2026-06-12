---
title: "Extended Regular Expression Question"
date: 2017-05-01
forum: General Help
---

### Post by John_Patrick_Mason on 2017-05-01
Hi all,

I don't understand the following sequence:

```

echo "This works." | grep -E '[[:upper:]][[:upper:][:lower:] ]*\.'

```

which is supposed to detect any kind of written sentence in the English language.

How come the word **works** is being highlighted? Would the word **works** have to start with an uppercase letter in order for it to be highlighted hence the character class [[:upper:]]? I don't get it.

---

### Post by steeldriver on 2017-05-01
The expression is matching the whole sentence as one (rather than separate words), I think

```

[[:upper:]]

```

a single upper-case character, followed by

```

[[:upper:][:lower:] ]*

```

zero or more upper-case characters, lower-case characters and spaces, followed by

```

\.

```

a literal period.

---

### Post by John_Patrick_Mason on 2017-05-01
Thanks for the quick response. I get it now.

---

