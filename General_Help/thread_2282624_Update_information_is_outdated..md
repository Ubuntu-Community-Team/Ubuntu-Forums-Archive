---
title: "Update information is outdated."
date: 2015-06-15
forum: General Help
---

### Post by alex317 on 2015-06-15
Hello everybody,
I installed Ubuntu 15.04 a while ago and now,after a while when I turn my laptop on I keep getting an error that says that the update information is outdated.
I think it's from the two repositories i get an error from (see screenshot).
This also appeared after i isntalled some ubuntu restricted extras (might be from that too).

[IMG]http://i57.tinypic.com/9u1yxw.png[/IMG]

Any ideea is appreciated.Thanks for reading my question.

---

### Post by monkeybrain20122 on 2015-06-15
I can't see from the screenshot which of these two 404 are (ppa launchpad is not specific enough) You can just disable them (search for software&update from dash, then go to other software and uncheck the box, or delete them from /etc/apt/sources.list.d) then run sudo apt-get update again.

---

### Post by deadflowr on 2015-06-15
You can access the software and updates in the software updater.
It's the settings button. fwiw
Rinse and repeat the rest of the above advice in post 2.

---

### Post by alex317 on 2015-06-15
They aren't in the software & updates.I don't think that is causing the problem tho,main thing i focus on is getting that red triangle with an exclamation mark to dissapear :) .

---

### Post by Bashing-om on 2015-06-15
alex317; Hello;

> 
tho,main thing i focus on is getting that red triangle with an exclamation mark to dissapear 


Following the aboves -removing the bad sources, and updating the system - will take care of that red mark.

The CLI way:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
in your browser verify which PPA is at fault, and
in your favorite text editor comment out the offending source line.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by alex317 on 2015-06-16
Thanks @[Bashing-om]("http://ubuntuforums.org/member.php?u=1111508")[COLOR=#000000]  ,it works great now! :) . 
Thread can be closed.[/COLOR]

---

### Post by slickymaster on 2015-06-16
> **alex317 said:**
> Thanks @[Bashing-om]("http://ubuntuforums.org/member.php?u=1111508")[COLOR=#000000]  ,it works great now! :) . 
Thread can be closed.[/COLOR]
Please mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution for the problem.

---

