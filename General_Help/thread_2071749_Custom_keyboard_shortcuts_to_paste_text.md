---
title: "Custom keyboard shortcuts to paste text"
date: 2012-10-16
forum: General Help
---

### Post by GGleroutier on 2012-10-16
Hi all

For my job, I have to send regular long-ish reports via a web interface. Obviously the reports vary depending on activity, but they always contain certain keywords, groups of words or expressions. Since I have to do this almost everyday, I'd like to speed up the process...
Is there a way to create custom shortcuts that would enable me to paste text directly as I type my report? ie Ctrl+Shift+1 pastes keyword A, Ctrl+Shift+2 pastes expression B, etc.

Firefox shortcuts (since I type directly in a web interface)? Apparently these control only Firefox features and browsing.
Ubuntu shortcuts? Same issue.
Text editor shortcuts?

Any ideas welcome!
Thanks in advance.

---

### Post by Vaphell on 2012-10-16
first install these tools
```
sudo apt-get install xdotool xsel
```

predefined text can be pasted like this:
text typed explicitly
```
echo "text to paste" | xsel -pi; xdotool click 2
```
text from file
```
xsel -pi < text_to_paste.txt; xdotool click 2
```

xsel puts the text in (-i) the primary buffer (-p), which then gets pasted with middle click, emulated by xdotool.

create a key combo enter the code below
```
sh -c 'echo "some text to paste" | xsel -pi; xdotool click 2'
```
or
```
sh -c 'xsel -pi < text_to_paste.txt; xdotool click 2'
```
hotkeys don't like multiple commands so sh -c wraps everything up and acts as 1 cmd.

---

### Post by GGleroutier on 2012-10-16
This looks great, thanks a lot! I knew there must be something like this.

I'll have a closer look at this and get back to you...

Thanks again!

---

### Post by GrouchyGaijin on 2013-01-08
> **Vaphell said:**
> first install these tools
```
sudo apt-get install xdotool xsel
```

predefined text can be pasted like this:
text typed explicitly
```
echo "text to paste" | xsel -pi; xdotool click 2
```
text from file
```
xsel -pi < text_to_paste.txt; xdotool click 2
```

xsel puts the text in (-i) the primary buffer (-p), which then gets pasted with middle click, emulated by xdotool.

create a key combo enter the code below
```
sh -c 'echo "some text to paste" | xsel -pi; xdotool click 2'
```
or
```
sh -c 'xsel -pi < text_to_paste.txt; xdotool click 2'
```
hotkeys don't like multiple commands so sh -c wraps everything up and acts as 1 cmd.
This looks great, but I need some clarification.
Could you please walk me through setting this up step by step?
I installed xdotool xsel, but am lost after that.

---

### Post by Vaphell on 2013-01-08
what do you want to achieve exactly?
either way you have to go to the hotkey config, create new entry and fill it with *sh -c '<something>'*, where <something> is the xsel/xdotool sequence that does what you need.

---

### Post by GrouchyGaijin on 2013-01-08
> **Vaphell said:**
> what do you want to achieve exactly?
either way you have to go to the hotkey config, create new entry and fill it with *sh -c '<something>'*, where <something> is the xsel/xdotool sequence that does what you need.

OK, I just tried again and it seems to be working now.  I guess I didn't read carefully enough.
Thank you.

---

