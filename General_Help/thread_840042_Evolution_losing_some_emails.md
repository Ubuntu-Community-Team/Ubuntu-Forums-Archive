---
title: "Evolution losing some emails?"
date: 2008-06-25
forum: General Help
---

### Post by dumbmatter on 2008-06-25
I have just noticed a very strange problem.  In Evolution, all of my emails are listed correctly in the messages list.  But, for most of my emails from the past month, when I click on them, it just shows 
an unrelated spam message.  It's like Evolution's database linking the message list to the actual email is somehow messed up, so all I see are random messages from my Junk folder when I want to open old emails.

This behavior only occurs for emails from the past ~30 days.  Everything older seems fine.  And it doesn't happen to all emails from the past ~30 days, just the vast majority of them.

So, I'm rather confused now.  I've been using Evolution for years and have never seen this before.  Has anyone else heard of a problem like this?  I'm running Hardy with all the latest updates.

---

### Post by krasty on 2008-07-07
I confirm the same problem with Evolution 2.22.2 and DEBIAN. 
Did not find anything unusual in logs or console output, except for messages like:

spamc[6006]: connect(AF_UNIX) to spamd [INDENT]/home/krasty/.evolution/cache/tmp/spamd-socket-path-GPzKUe failed: No such file or directory[/INDENT]

and spam logs:
[INDENT]May  1 13:44:20 debilek spamd[22797]: spamd: got connection over /home/krasty/.evolution/cache/tmp/spamd-socket-path-2QV5rg 
May  1 13:44:22 debilek spamd[22797]: spamd: result: . 3 - BAYES_99,HTML_MESSAGE,RDNS_NONE scantime=1.4,size=2275,user=krasty,uid=1000,required_score=5.0,rhost=localhost,raddr=127.0.0.1,rport=/home/krasty/.evolution/cache/tmp/spamd-socket-path-2QV5rg,mid=<CDAAD90A.D%assidui2004@SA-TECHINC.COM>,bayes=1.000000,autolearn=no 
May  1 13:44:22 debilek spamd[22797]: spamd: got connection over /home/krasty/.evolution/cache/tmp/spamd-socket-path-2QV5rg 
May  1 13:44:23 debilek spamd[22797]: spamd: result: . -2 - AWL,BAYES_00,HTML_MESSAGE,RDNS_NONE,UNPARSEABLE_RELAY scantime=0.9,size=5315,user=krasty,uid=1000,required_score=5.0,rhost=localhost,raddr=127.0.0.1,rport=/home/krasty/.evolution/cache/tmp/spamd-socket-path-2QV5rg,mid=<1813592018.1209576653562.JavaMail.app@com07.prod>,bayes=0.000000,autolearn=no 
does anyone know what it is caused by?
[/INDENT]

---

