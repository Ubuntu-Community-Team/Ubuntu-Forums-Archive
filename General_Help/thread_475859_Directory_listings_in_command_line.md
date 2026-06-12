---
title: "Directory listings in command line"
date: 2007-06-16
forum: General Help
---

### Post by idn on 2007-06-16
When I use the terminal in a directory with a really long path name, it sometimes makes the terminal window really cluttered as the directory path can take up a whole line, as shown in the screenshot. 

I was wondering is this can be changed, so the left hand side does not display the full directory path, but instead perhaps only the current folder. I know this can be done in fedora because I used it the other day :) any ideas anyone?

---

### Post by thelinuxguy on 2007-06-16
```

export PS1="${debian_chroot:+($debian_chroot)}\u@\h:\W\$"

```

or, if you want ONLY the folder name

```

export PS1="\W\$ "

```

To get back the default prompt:
```

export PS1="${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR="Red"]w[/COLOR]\$"

```

---

### Post by idn on 2007-06-17
thanks for your help!

---

