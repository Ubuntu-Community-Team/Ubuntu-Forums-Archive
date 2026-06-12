---
title: "Change terminal for &quot;Open current folder in terminal&quot;"
date: 2017-04-26
forum: General Help
---

### Post by bistecchino on 2017-04-26
Hello everyone, i'm using Terminator as my "main terminal" and i'm used to press F4 (or click on Tool->Open Current Folder in Terminal) to open the folder that i'm at in the terminal but if I do that it brings up LXTERMINAL and not the Terminator one.

Can I change which terminal is used in this function? 

I tried searching in the forum, on StackOverflow and other places but I didn't find an answer. 

Thanks!

---

### Post by &amp;KyT$0P# on 2017-04-26
In PCManFM: Edit > Preferences > Advanced > Terminal emulator

---

### Post by bistecchino on 2017-04-26
> **halogen2 said:**
> In PCManFM: Edit > Preferences > Advanced > Terminal emulator

That worked like a charm, I don't know how I missed that option, I just had to put terminator %s instead of x-terminal-emulator %s there!

I guess 4 eyes are better than 2 :lolflag:

Thank you :)

---

### Post by &amp;KyT$0P# on 2017-04-26
You're welcome! :KS

You might also want to consider setting [FONT=Courier New]x-terminal-emulator[/FONT] to be terminator.  See if this command offers that option -
```
sudo update-alternatives --config x-terminal-emulator
```

---

