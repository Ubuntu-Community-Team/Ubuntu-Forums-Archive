---
title: "Linux command code to echo"
date: 2013-10-17
forum: General Help
---

### Post by rune_pedersen2 on 2013-10-17
Is there to input a string of codes to echo text out in the terminal?
E.g: echo &8|¤37... (etc) echoes out in terminal: "this is the echo from code" ?

I want to have fun with my brother, and ask him to input a piece of code to the linux terminal, and echo out something I want it to say?
Can this be done via script or something, where you can reference to get the code from?

Weird question, I know :P

regards,

---

### Post by Habitual on 2013-10-17
```
read -p "Are you alright? (y/n) " ANSWER
if [ "$ANSWER" = "y" ]; then
  echo "Glad to hear it"
else
  echo "You need more bash programming"
fi
```

Stolen from [http://stackoverflow.com/questions/226703/how-do-i-prompt-for-input-in-a-linux-shell-script](http://stackoverflow.com/questions/226703/how-do-i-prompt-for-input-in-a-linux-shell-script)

Here's a few to bookmark:
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[http://mylinuxbook.com/linux-shell-environment/](http://mylinuxbook.com/linux-shell-environment/)
[http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents](http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents)
[http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf)
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
[http://mylinuxbook.com/bash-shell-scripting-part-i/](http://mylinuxbook.com/bash-shell-scripting-part-i/)
[http://mylinuxbook.com/bash-shell-scripting-2/](http://mylinuxbook.com/bash-shell-scripting-2/)
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)
[http://unixhelp.ed.ac.uk/](http://unixhelp.ed.ac.uk/)

Here's a Google Custom Search Engine I put together for bash resources...
[https://www.google.com/cse/home?cx=016212844476379046035:zj-1bdfg5ga&hl=en](https://www.google.com/cse/home?cx=016212844476379046035:zj-1bdfg5ga&hl=en)

[http://mywiki.wooledge.org](http://mywiki.wooledge.org) is a good place to start

---

