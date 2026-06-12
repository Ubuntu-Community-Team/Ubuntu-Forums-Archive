---
title: "Bash color output"
date: 2014-01-01
forum: General Help
---

### Post by Tristan_Williams on 2014-01-01
I can't take anymore of this grey.
I have set PS1 to the following, which gives me a colorful prompt:
```

PS1="\[\e[01;32m\]\u:\[\e[0m\]\[\e[00;37m\] \[\e[0m\]\[\e[01;36m\]\w\[\e[0m\]\[\e[00;37m\] \[\e[0m\]\[\e[01;31m\]\$\[\e[0m\]"

```

But i want colorized output.

For instance:

Normal output = #FFFFFF
Errors = bright red, bold
Warnings = bright yellow, bold
package/application names = bold
messages = bright blue, bold

How can this be done?

---

### Post by bluefrog on 2014-01-02
[http://mylinuxbook.com/ubuntu-command-line-prompt-colour/](http://mylinuxbook.com/ubuntu-command-line-prompt-colour/)
[https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)

---

### Post by v910JQK on 2014-01-02
Outputs are not managed by Shell but by programs themselves.

---

