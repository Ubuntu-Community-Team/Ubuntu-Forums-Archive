---
title: "How to disable automatic screen title setting?"
date: 2015-01-29
forum: General Help
---

### Post by tavasti2 on 2015-01-29
Hi!

I'm using screen, and mostly having ssh connections to here & there. I launch connections like 'screen -t remhost ssh [EMAIL="username@some.host.over.there.com"]username@some.host.over.there.com[/EMAIL]'.
Idea is to set screen title descriptive, and short. However, screen has feature to set title automatically. My short and descriptive name for window turns to something like 
'ec2-user@taw-test-galera2:/usr/share/doc/cloud-init' which is not what I want. When listing screens with 'C-a w' list of names won't fit in one line. 

Is there some possibility to disable that automatic title setting. Setting prompts such that they won't set title is not an option: machines are mostly from cloud, other people use them also, etc. 

What should I put to my .screenrc?

--Tavasti

---

