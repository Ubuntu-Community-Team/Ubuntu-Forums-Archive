---
title: "Scheduled Script Weirdness"
date: 2008-06-11
forum: General Help
---

### Post by hoggy on 2008-06-11
I've got two scripts that I'm calling via root's crontab that aren't quite acting right on my Ubuntu boxen.

The first one checks a directory and uses esmtp to mail me the contents (I'm interested in the date...)  When it fires, I get a blank email.  When I call the script manually (ala /etc/backupscripts/checker), it works perfectly.

Once, after a patch/reboot, it worked on its own.  Never since, though...

On one of my other boxes, I have a script that scans the network.  Again, run from bash, it works well.  When scheduled, it loses access to the '$HOSTNAME' variable.  I use that for a portion the filename, and the cron-generated files leave that portion blank.

Any ideas here?  Any resources I could use to understand what's different on these boxes than what I'm used to?

The second script came right off an old CentOS box that has had no trouble with it for over two years...

---

### Post by bingoUV on 2008-06-11
1. Check your scripts using sh rather than bash before trying them through cron.

2. Ubuntu resets the environment for the cron scripts. Run a script using cron, which will have the following command. Compare it with the output of the same command without cron. You'll know the difference
```

set > /tmp/cronEnv

```

3. Instead of using $HOSTNAME, maybe `hostname` will be fine for you.

---

