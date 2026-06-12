---
title: "Double prompt in text-based mode"
date: 2007-08-26
forum: General Help
---

### Post by Tangee on 2007-08-26
For some reason when I enter text-based mode (ie tty1-6) I get 2 prompts so it looks like this:

andy@laptop~$andy@laptop~$

but in a terminal window it displays correctly...any ideas?

When the problem occurs, the cursor is actually at the end of the first half (where it should be), and I can write over the second prompt. So it seems as though the duplicate prompt is actually in the background or something...(?)

---

### Post by Tangee on 2007-08-29
solved the problem...

it seems to be directly related to me noobing up the .bashrc file...but I can't understand how it did so i'll post the offending section below and hopefully someone can educate me :P

```
# set $TERM to 'xterm-color' until I can figure out how to do it properly!
TERM='xterm-color'

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[00;33m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac
```

I did the "TERM=xterm-color" line as a dirty hack to remind me to find out how to tell it properly that we "want" color, but never got round to it...

it seems that if I comment out this line, the prompt works fine!

Any ideas?

---

