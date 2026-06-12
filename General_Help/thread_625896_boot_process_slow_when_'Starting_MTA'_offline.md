---
title: "boot process slow when 'Starting MTA' offline"
date: 2007-11-28
forum: General Help
---

### Post by Clouseau__ on 2007-11-28
Hi everyone,

Ever since i did a clean install of gutsy, I've been having problems while booting (and being offline).

**This only happens when not connected to the internet**

The computer starts booting and all of a sudden it exits the graphic screen and shows the log, where it gets stuck for a while on 'Starting MTA'. After some time it finally finishes, but needless to say, the extra time spent 'Starting MTA' is plain annoying.

Now, I'm guessing the MTA is not configured to **only** deliver mail locally (which should be my case) and therefore spends some time looking for a (non available) internet connection.

If that is the case, (I guess) it should be as simple as telling exim not to use the internet.

any help?

thanks in advance!

---

### Post by Clouseau__ on 2007-11-30
bump ...!

---

### Post by dave-5B on 2008-03-16
i have the same problem on my thinkpad, anyone?

---

### Post by Clouseau__ on 2008-03-17
Hi, fixed this a while ago and had forgotten to post how to solve it.

[LIST=1]Go to /etc/rc2.d/ (which is your normal multiuser init state)[/LIST]
[LIST=2]You should have a bunch of symlinks that start with S, then two digits (XX) and then the name of the service it starts[/LIST]
[LIST=3]Search for SXXexim4 (where XX is a two-digit number... in my case it was 20)[/LIST]
[LIST=4]Rename it so that instead of starting with S, it starts with a K (leave the two digits intact): [/LIST]

> sudo mv SXXexim4 KXXexim4

That should do it. You'll be basically executing exim4 (the mail transfer agent) with the **stop** option. More information on the subject [here]("http://docsrv.sco.com:507/en/OSAdminG/sstT.etcrc.html").

Hope this works!

cheers!

---

### Post by aks2008 on 2008-06-03
Thanks Clouseau_ It worked for me.

---

### Post by Clouseau__ on 2008-06-04
Glad I could help ;)

clouseau__

---

