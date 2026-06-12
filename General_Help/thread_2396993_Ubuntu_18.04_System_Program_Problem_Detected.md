---
title: "Ubuntu 18.04 System Program Problem Detected"
date: 2018-07-24
forum: General Help
---

### Post by mIk3_08 on 2018-07-24
what was this? 
see image below;
[ATTACH=CONFIG]280491[/ATTACH]

---

### Post by mIk3_08 on 2018-07-24
Any help will be much appreciated.

---

### Post by westie457 on 2018-07-24
If you click on the Report Problem button a report will be generated that you can look through.
The report will tell you which part failed and how it failed. Near the end of the report might be a section saying 'unreportable', if you see that update the system. The problem should go away. If the problem shows again consider reporting the problem.

---

### Post by mIk3_08 on 2018-07-24
Thanks westie457. I already found some solution to solve this situation a minute ago. Thanks for the concern.

---

### Post by Topsiho on 2018-07-24
It would be nice if you tell us what solution solved this situation. So that we can learn from this.

It is not uncommon that a system problem is detected, and that you are asked to report this. As Westie says, clicking the report button will generate a report, which you can read through, and even get a hint of what caused this problem, and which you can use to solve it. Sending the report enables the developers to solve it, and to create an update for it, that some time in the future updates all computers with the same problem. This way many a problem is miraculously solved, and so you help anyone using Ubuntu! It so sometimes seems alive, which is wonderful to watch!

Topsiho

---

### Post by mIk3_08 on 2018-07-26
I just disabled the apport;
```
# set this to 0 to disable apport, or to 1 to enable it# you can temporarily override this with
# sudo service apport start force_start=1
enabled=1
```
under;
```
/etc/default/apport
```
disable the Apport
Turn to 0
```
enabled=0
```

---

### Post by Topsiho on 2018-07-26
???  Why?

You get this OS for free. It's the work of many developers, who developed this and put it at your disposal. You don't have to pay them for it, and you are completely free to put it on any computer you wish, and to give it o anyone you wish to give it to. The developers don't earn a cent from advertisement and digging into your privacy.
You **can **do something back: when a problem arises, you can report it to the developers. It is a two way cutting knife: they can correct this particular problem, and so improve their work, and they can give it back as an update for anyone who uses it.
Why do you disable this?

Well, it is not my decision ... and indeed, you are completely free to do so. No strings attached.

Topsiho

---

### Post by PaulW2U on 2018-07-26
> **mIk3_08 said:**
> I just disabled the apport;
That's not a solution. That's a work around.
> **Topsiho said:**
> You **can **do something back: when a problem arises, you can report it to the developers. It is a two way cutting knife: they can correct this particular problem, and so improve their work, and they can give it back as an update for anyone who uses it.
Agreed. That's one reason why I always run the "development" version of Ubuntu.

During the 18.04 development period I experienced many crashes and reported them when prompted to do so. Most if not all of those issues were resolved before 18.04 was even released. I contributed to Ubuntu development with minimal effort. It takes just a few seconds to follow the process and quite often you are told that the issue is already known so there is nothing for you to do anyway.

@mik3_08, I do know that these errors, if they are submitted, appear on a report that the Ubuntu developers look at daily. Common problems will be fixed. Your input could lead to those problems being resolved a little quicker.

---

### Post by mIk3_08 on 2018-07-26
Thanks PaulW2U and Topsiho. I already submitted the issue from the first time it pops-up on my screen second time and third time I think, but it keeps on popping up with same issue that's why I disabled it and reboot the system and I enabled the apport again after it boots successfully and the system is okay now. Thanks everyone for the concern.

---

### Post by Topsiho on 2018-07-26
Great!
It's a pleasure to help people like you, who listen, and report back.

Topsiho

---

