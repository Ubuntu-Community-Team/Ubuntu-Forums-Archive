---
title: "xterm title bar"
date: 2005-05-08
forum: General Help
---

### Post by sprucio on 2005-05-08
I am having a slight problem with xterm and it's title bar. Since .bashrc usually has an entry to display the current working directory on the title bar, I have removed that line from my .bashrc file. However, I am still getting the CWD on the title bar.

Upon doing some research, I realized that /etc/profile had an entry for /etc/bash.bashrc. I commented this out and still I was getting the CWD in the title bar.

The last thing I did was actually modify /etc/bash.bashrc where there was an entry for displaying the CWD.

Can anyone explain to me how /etc/bash.bashrc file is being executed? Is this something taht's builtin to the bash shell in Ubuntu?

---

