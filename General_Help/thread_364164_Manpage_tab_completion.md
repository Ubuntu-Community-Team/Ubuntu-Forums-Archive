---
title: "Manpage tab completion"
date: 2007-02-17
forum: General Help
---

### Post by SadaraX on 2007-02-17
Does anyone know how to get manpage tab completion working in Ubuntu? I used to have this working all the time under various version of Debian (most recently Mepis). But I cannot get it to work at all in Ubuntu. 

I know that Ubuntu has some strange tabbing behavior for the 'cd' command, but I figured out to how to change that.

But I cannot for the life of me figure out why the 'man' command will not tab complete. I have compared settings between my Ubuntu machines which do not tab complete with the settings of my Debian machines which will tab complete. I am baffled. 

Any help would be greatly appreciated.

---

### Post by scooper on 2007-02-18
/etc/bash.bashrc has some commented-out lines that enable the extra bash-completion capabilities.  If you just remove the "#"'s at the beginning of the 3 lines under the comment that starts with "# enable bash completion..." it should enable the behavior you want.  You'll have to start a fresh shell to see the results.  I think the same commented-out block is in your own ~/.bashrc file and you could fix it there instead.

---

### Post by SadaraX on 2007-02-18
> **scooper said:**
> /etc/bash.bashrc has some commented-out lines that enable the extra bash-completion capabilities.  If you just remove the "#"'s at the beginning of the 3 lines under the comment that starts with "# enable bash completion..." it should enable the behavior you want.  You'll have to start a fresh shell to see the results.  I think the same commented-out block is in your own ~/.bashrc file and you could fix it there instead.

Thank you very much. As it turns out, the only thing that I needed to add to my own .bashrc file was this bit of code:

```

# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

Everything else was fine. I wonder why normal bash tab completion is disabled for Ubuntu by default? I **_*REALLY*_** think they should turn it on by default, as it is in most distributions of Linux.

---

### Post by scooper on 2007-02-18
Glad it worked.  It is a bit mind-boggling why it isn't enabled.  I've never had a problem caused by bash-completion, and I feel lost without it.

---

