---
title: "Cool bash prompt with Time?"
date: 2013-01-13
forum: General Help
---

### Post by honeybear on 2013-01-13
Hi,

More in depth, just with time on that: 

Would you know / have a cool bash prompt with the time? colorful for instance .

Regards

---

### Post by dino99 on 2013-01-13
here is the newest howto  :)

[https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)

---

### Post by Habitual on 2013-01-13
```
while sleep 1;do tput sc;tput cup 0 $(($(tput cols)-29));date;tput rc;done &
```

you want a clock mechanism as your prompt proper?

---

### Post by Lars Noodén on 2013-01-13
There are a number of shortcuts available to set $PS1.  See the manual page for [bash](http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html) and scroll down to "PROMPTING"

Otherwise you can include the output from $(date +"%H:%M")

```

PS1='$(date +"%H:%M:%S ")'

```

---

### Post by Habitual on 2013-01-13
> **Habitual said:**
> ```
while sleep 1;do tput sc;tput cup 0 $(($(tput cols)-29));date;tput rc;done &
```you want a clock mechanism as your prompt proper?

just add ' \@ ' somewhere in your PS1

---

### Post by Cheesemill on 2013-01-13
Some good PS1 links...

[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/c141.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/c141.html)
[https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)
[https://bbs.archlinux.org/viewtopic.php?id=50885](https://bbs.archlinux.org/viewtopic.php?id=50885)

---

