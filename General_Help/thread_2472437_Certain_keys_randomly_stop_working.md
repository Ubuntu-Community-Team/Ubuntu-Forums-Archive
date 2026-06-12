---
title: "Certain keys randomly stop working"
date: 2022-02-26
forum: General Help
---

### Post by veramocor on 2022-02-26
Hello all, I have an issue that is very frustrating and also quite difficult to describe. I have been running Kubuntu 20.04 on a MSI GS66 Stealth for almost a year now. Here is the output from a uname -a:

Linux dracolich 5.13.0-30-generic #33~20.04.1-Ubuntu SMP Mon Feb 7 14:25:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

About a week ago, I started to have a problem whereby certain specific keys would pause in their operation. I don't know the full set of keys, but I know that the "g", "t", ".", and enter keys are included. The symptoms are that those keys would temporarily not work for about 5-20 seconds, then start working again. Other keys work fine during those moments. I have not been able to ascertain a pattern or cause to this behavior but, as I'm sure you can imagine, it is incredibly frustrating!! The CPU is not under heavy load and I have not found anything suspicious in the syslog file, but then again I have no idea what I should be looking for. Does anyone have any ideas on what might be causing this or how I would even go about diagnosing the issue? All I have done so far is keep an eye on processes via top and looked at the /var/log/syslog file.

Many thanks for any advice. I'm happy to provide any further information as needed.

Stephen

---

### Post by veramocor on 2022-02-26
I guess a question I have for now is: if I note the times when these events happen, what log files (other than /var/log/syslog) should I be checking for a possible clue toward a diagnosis?

---

### Post by Autodave on 2022-02-26
Sounds like a sticking key to me.    Carefully, turn the unit, with the lid open, over.  Tap on the side facing upward (keys should be facing downward).  While still tapping, move the laptop into different positions.  While it is still turned off, put it back to its normal position and start rapidly and repeatedly pressing EVERY key.  Check now by powering unit on and tyoing.

To make sure that it is a keyboard problem, you can hook up an external keyboard and see what happens.

---

### Post by veramocor on 2022-02-26
Thanks for your response. The fact that specific keys are affected does automatically makes one think of a sticking key problem. Unfortunately this is definitely not a hardware issue, and I have tested this with an external keyboard. It is very mysterious to me that a periodic software issue is occurring that only affects certain keys, and I just need to know how to track down what that process is.

---

### Post by dragonfly41 on 2022-02-27
This thread suggests how to* disable* keys.

[https://superuser.com/questions/775785/how-to-disable-a-keyboard-key-in-linux-ubuntu](https://superuser.com/questions/775785/how-to-disable-a-keyboard-key-in-linux-ubuntu)

As to what script is possibly doing this .. I cannot guess.
But you could look to see if xmodmap is run as a process at time of key hobbling.

[Added note]
I am scanning through my desktop apps to build an inventory of useful tools for a widget I am developing.
I noticed Sysprof app which dumps a profile of processes during a recording period.
When you next experience key blocking I suggest running sysprof for a few minutes then analyse at leisure
to look for suspect processes. At least you have a tool to try but I don't know if it will find your cause.

---

### Post by veramocor on 2022-02-27
Thank you. I'm not familiar with Sysprof, but I will give it a try. I feel like there must be some process running in the background that is causing this issue but, aside from the syslog, I'm not sure how to track it down.

---

### Post by dragonfly41 on 2022-02-27
[Some more tips.]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting")

---

### Post by veramocor on 2022-02-27
Thanks. I feel like much of that material is way over my head. I don't even know how to upgrade my BIOS. However, I can report an update on the affected keys. At the time of writing, they are: v g t . enter.

---

### Post by veramocor on 2022-02-27
Okay, another update. I managed to find another external keyboard and I have confirmed during one of the "episodes" that the external keyboard worked just fine. So, contrary to my previous statement, this appears to be hardware related, so I will try some fixes along those lines.

---

### Post by veramocor on 2022-02-27
> **Autodave said:**
> Sounds like a sticking key to me.    Carefully, turn the unit, with the lid open, over.  Tap on the side facing upward (keys should be facing downward).  While still tapping, move the laptop into different positions.  While it is still turned off, put it back to its normal position and start rapidly and repeatedly pressing EVERY key.  Check now by powering unit on and tyoing.

To make sure that it is a keyboard problem, you can hook up an external keyboard and see what happens.

I have tried this but it has not solved the problem. Are there other hardware issues (other than sticky keys) that could cause specific keys to stop working? As I said, the keys in question all became temperamental about a week ago. Is there a motherboard issue that would affect specific keys? In case it's not obvious, I really don't know what I'm talking about here and am grasping at straws.

---

### Post by Autodave on 2022-02-27
Do what I suggested before.  A can of compressed air may also help getting rid of whatever is under the keys.  Generally though, just repeatedly pressing and releasing them....rapidly.....will do the trick.  Knock the dirt out first.

---

### Post by veramocor on 2022-03-01
> **Autodave said:**
> Do what I suggested before.  A can of compressed air may also help getting rid of whatever is under the keys.  Generally though, just repeatedly pressing and releasing them....rapidly.....will do the trick.  Knock the dirt out first.

Thank you. I have removed several keys and cleaned with compressed air, etc. Unfortunately the problem persists. You will notice that the problem keys appear to be clustered (such as t, g, v). At this point, I am assuming there is some connection issues between the keyboard and motherboard, and so plan to have the entire keyboard replaced.

---

### Post by dragonfly41 on 2022-03-01
This post refers to exact same keys

[https://forum-en.msi.com/index.php?threads/laptop-acting-weird-help-gt72-dominator-g-1445.276969/](https://forum-en.msi.com/index.php?threads/laptop-acting-weird-help-gt72-dominator-g-1445.276969/)

I wonder if you have a hidden file ~/.vgt  (or other combination} being accessed ?? Just a guess.

---

### Post by veramocor on 2022-03-22
Just to close this out, I purchased a replacement keyboard for the laptop and had it installed. Problem is now fixed. Thanks for all of the replies.

---

### Post by Autodave on 2022-03-22
I believe that you are in need of a new keyboard.  Before you do that, try some compressed air on the keyboard while you are holding the unit upside down.  Then start pressing every key rapidly and repeatedly.  More compressed air.  Repeat.

---

