---
title: "VBoxManage and Compiz"
date: 2008-05-13
forum: General Help
---

### Post by jayde6 on 2008-05-13
Hi all, I have a little problem I hope you guys can help with. I use Virtualbox to play a couple older games and have found that compiz decreases performance. So I made a startup script that says;

```
metacity --replace &
VBoxManage startvm AoE2
compiz --replace
```

This works fine for every other application except virtualbox, compiz kicks back on right after the vbox loads. Most likely VBoxManage (which is used to load a virtualization without going through the main program) quits after loading the virtualization so it goes to the next line of the script. Any ideas to keep compiz off through a startup script till I exit Vbox?

Thanks in advance : )

~Jennifer

---

