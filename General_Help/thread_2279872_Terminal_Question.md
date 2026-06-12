---
title: "Terminal Question"
date: 2015-05-26
forum: General Help
---

### Post by CosmicFlux on 2015-05-26
Hi,

I would like to know if there is any existing mechanism for formatting terminal output in the following way:

```
**$ grep desktop /etc/services**
desktop-dna    2763/tcp    #Desktop DNA
desktop-dna    2763/udp   #Desktop DNA

**$ find /etc -iname iptables -exec echo "I found {}" \;**
I found /etc/bash_completion.d/iptables
I found /etc/sysconfig/iptables
I found /etc/rc.d/init.d/iptables
```

As you can see, the command line is always bold, with the output formatted regular. Or, I guess in a similar fashion, the command line being a different colour than the output?

Let me know if you have any ideas.


Kind Regards,

Cosmic

---

### Post by sisco311 on 2015-05-26
If you are using bash, then check out:
[https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)
[https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)
and
[https://wiki.archlinux.org/index.php/Color_Bash_Prompt#Different_colors_for_text_entry_and_console_output](https://wiki.archlinux.org/index.php/Color_Bash_Prompt#Different_colors_for_text_entry_and_console_output)

For example you could add  something like this to your ~/.bashrc file:
```

green=$(tput setaf 2)
bold=$(tput bold)
reset=$(tput sgr0)

# set the prompt to green and input text to bold
PS1='\[$green\]\[$bold\][\u@\h \W]\$\[$reset\] \[$bold\]'

# reset the color when Enter is pressed
trap 'echo -ne "$reset"' DEBUG

```

---

### Post by CosmicFlux on 2015-05-26
Thanks very much, that's exactly what I was looking for! 

Just for reference, here is my desktop.

[IMG]http://www.darrenjamesstott.net/images/DieHard4Scren.png[/IMG]

---

