---
title: "who output question"
date: 2008-04-09
forum: General Help
---

### Post by Rizla on 2008-04-09
hi, when i do a who command.

I see the following

<myusername> :0
<myusername> pts/0

when i do a who am i, it returns
pts/0


so what is the :0 showing up?

one more thing, when i do a netstat -a  I see a TON of output like this

unix  2  [ACC ]  STREAM  LISTENING  17719 /tmp/orbit-(username)/linc-1780-0-1e21a669d5dbc

is this normal?

---

### Post by Rizla on 2008-04-09
I'm looking at my auth.log and i see a lot of this:

Apr  8 23:17:01 RIZDSK CRON[9442]: (pam_unix) session opened for user root by (uid=0)
Apr  8 23:17:01 RIZDSK CRON[9442]: (pam_unix) session closed for user root
Apr  9 00:17:01 RIZDSK CRON[15016]: (pam_unix) session opened for user root by (uid=0)
Apr  9 00:17:01 RIZDSK CRON[15016]: (pam_unix) session closed for user root
Apr  9 01:17:01 RIZDSK CRON[20581]: (pam_unix) session opened for user root by (uid=0)
Apr  9 01:17:01 RIZDSK CRON[20581]: (pam_unix) session closed for user root
Apr  9 02:17:01 RIZDSK CRON[26146]: (pam_unix) session opened for user root by (uid=0)
Apr  9 02:17:01 RIZDSK CRON[26146]: (pam_unix) session closed for user root
Apr  9 03:17:01 RIZDSK CRON[31704]: (pam_unix) session opened for user root by (uid=0)
Apr  9 03:17:01 RIZDSK CRON[31704]: (pam_unix) session closed for user root
Apr  9 04:17:01 RIZDSK CRON[4831]: (pam_unix) session opened for user root by (uid=0)
Apr  9 04:17:01 RIZDSK CRON[4831]: (pam_unix) session closed for user root
Apr  9 05:17:01 RIZDSK CRON[10551]: (pam_unix) session opened for user root by (uid=0)
Apr  9 05:17:01 RIZDSK CRON[10551]: (pam_unix) session closed for user root
Apr  9 06:17:01 RIZDSK CRON[16126]: (pam_unix) session opened for user root by (uid=0)
Apr  9 06:17:01 RIZDSK CRON[16126]: (pam_unix) session closed for user root
Apr  9 06:25:01 RIZDSK CRON[16868]: (pam_unix) session opened for user root by (uid=0)
Apr  9 06:25:01 RIZDSK CRON[16868]: (pam_unix) session closed for user root
Apr  9 07:17:01 RIZDSK CRON[21730]: (pam_unix) session opened for user root by (uid=0)
Apr  9 07:17:01 RIZDSK CRON[21730]: (pam_unix) session closed for user root
Apr  9 07:30:01 RIZDSK CRON[22936]: (pam_unix) session opened for user root by (uid=0)
Apr  9 07:30:01 RIZDSK CRON[22936]: (pam_unix) session closed for user root
Apr  9 08:17:01 RIZDSK CRON[27784]: (pam_unix) session opened for user root by (uid=0)
Apr  9 08:17:01 RIZDSK CRON[27784]: (pam_unix) session closed for user root

I  was asleep so what are all the open and close session.

---

### Post by Het Irv on 2008-04-09
The netstat is normal, at least I have it as well on the 2 Ubuntu computer I run. (I'm not sure what it is)

---

### Post by jocko on 2008-04-09
> **Rizla said:**
> I'm looking at my auth.log and i see a lot of this:

Apr  8 23:17:01 RIZDSK [COLOR=Red]CRON[/COLOR][9442]: (pam_unix) session opened for user root by (uid=0)
...

I  was asleep so what are all the open and close session.

That's cron doing what it's supposed to do.
From the debian package information in the cron package:
> cron is a background process (`daemon') that runs programs at regular
intervals (for example, every minute, day, week or month); which
processes are run and at what times are specified in the `crontab'.

So nothing to worry about, just normal automated system maintenance that happens every now and then...

---

### Post by Rizla on 2008-04-10
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				ok, i guess the cron stuff is good, what about that first user in the who output

:0

is this normal?

I found this link and it started to scare me thinking that I may have someone on my comp.
[http://www.securiteam.com/exploits/5FP0T20GAK.html]("http://www.securiteam.com/exploits/5FP0T20GAK.html")

---

### Post by PeterJS on 2008-04-10
:0 is the designation of the first X session. X sessions are identified in the format :Session-Screen, if you've only got one screen, or an application that really only cares about the session it will truncate that down to just :Session.

---

### Post by Rizla on 2008-04-10
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **PeterJS said:**
> :0 is the designation of the first X session. X sessions are identified in the format :Session-Screen, if you've only got one screen, or an application that really only cares about the session it will truncate that down to just :Session.

Alrighty, no worries then.  Thanks, i was getting paranoid.

---

