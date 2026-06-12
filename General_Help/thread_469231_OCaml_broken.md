---
title: "OCaml broken"
date: 2007-06-09
forum: General Help
---

### Post by yang on 2007-06-09
I just tried installing ocaml on two completely different Ubuntu systems (one is a Dapper derivative on x64 desktop, other is Feisty on old x86 laptop). It installs fine but when I try to compile anything I get:

```

$ ocamlc hello.ml
>> Fatal error: cannot open pervasives.cmi
Fatal error: exception Misc.Fatal_error
$ locate pervasives.cmi
/usr/lib/ocaml/3.09.2/pervasives.cmi
$ ocamlc -where
/usr/lib/ocaml
$ ocamlc -I /usr/lib/ocaml/3.09.2 hello.ml
$ ls a.out
a.out

```

People in #ocaml say this is an Ubuntu bug. Anybody know how to fix this? Even though passing -I lets me build a simple hello-world app, it doesn't help me building the latest unison, since there's no corresponding environment variable. I have to munge the Makefile, and they call ocamlc directly, so no OCAMLC variable to modify.

(It sucks that you have to learn how to use another language's compiler just to get the latest version of an app.)

---

