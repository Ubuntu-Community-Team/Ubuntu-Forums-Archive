---
title: "Stuck downgrading libssl"
date: 2017-12-23
forum: General Help
---

### Post by MarcusL on 2017-12-23
I have updated my `Ubtuntu 16.04` server earlier today, and one of my apps which uses `wkhtmltopdf` stopped working.

Based on the [thread here]("https://github.com/wkhtmltopdf/wkhtmltopdf/issues/3001"), the solution is to downgrade and lock `libssl` to the previous version.

```
[COLOR=#24292E][FONT=-apple-system]apt install libssl-dev=1.0.2g-1ubuntu4.8[/FONT][/COLOR]
```[COLOR=#24292E][FONT=-apple-system]
[/FONT][/COLOR]
When I try and downgrade:

```
vagrant@homestead:~/src$ sudo apt install libssl-dev=1.0.2g-1ubuntu4.8
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Version '1.0.2g-1ubuntu4.8' for 'libssl-dev' was not found

```

Why can it not find this specific version? Is there a workaround? Thanks

---

