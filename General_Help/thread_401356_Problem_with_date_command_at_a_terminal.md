---
title: "Problem with date command at a terminal"
date: 2007-04-04
forum: General Help
---

### Post by jamadagni on 2007-04-04
I am using Kubuntu Edgy and I have the following problem:

```

$ ./datefmt "foo\nymd hm"
+"foo%n%F %R"
$ date +"foo%n%F %R"
foo
2007-03-29 20:03
$ date $(./datefmt "foo\nymd hm")
date: extra operand `%R"'
Try `date --help' for more information.

```

Why is it not working? I will attach the script if needed. Thanks.

---

