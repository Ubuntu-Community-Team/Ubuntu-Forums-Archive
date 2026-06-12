---
title: "Reassign Keyboard Keys"
date: 2012-12-02
forum: General Help
---

### Post by yusuo85 on 2012-12-02
I have a problem, the spacebar on my laptop is busted, I've reassigned the spacebar to the Right Alt key within Windows but I have no idea how to do this within Ubuntu. Its the only thing thats holding me back from using Ubuntu as my main OS.

Can anyone please help me reassign my spacebar key to Right Alt. 

Thanks in advance guys/girls

---

### Post by yusuo85 on 2012-12-02
Anybody, this seems like something that should be simple but I can't find anything

---

### Post by erind on 2012-12-03
> **yusuo85 said:**
> I have a problem, the spacebar on my laptop is busted, I've reassigned the spacebar to the Right Alt key within Windows but I have no idea how to do this within Ubuntu. Its the only thing thats holding me back from using Ubuntu as my main OS.

Can anyone please help me reassign my spacebar key to Right Alt. 

Thanks in advance guys/girls

One option is using **xmodmap** from the command line: 

```
sleep 8 && xmodmap -e 'keycode 108 = space'
```Where 108 is the keycode for Alt_Right in my setup, which can be found using '**xev**' command. Then place the above command in the start-up applications to automatically do the re-mapping during the start-up.

Some more useful reading:

[http://ubuntuforums.org/showthread.php?t=1793269](http://ubuntuforums.org/showthread.php?t=1793269)
[http://www.physics.drexel.edu/liki/index.php/Unicode](http://www.physics.drexel.edu/liki/index.php/Unicode)

---

