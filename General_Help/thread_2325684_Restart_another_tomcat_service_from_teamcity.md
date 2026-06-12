---
title: "Restart another tomcat service from teamcity"
date: 2016-05-24
forum: General Help
---

### Post by 1clue on 2016-05-24
Hi,

I have a 12.04.5 Ubuntu Server build box. It has:

[LIST=1]
[*]TeamCity 8.1 -- [https://www.jetbrains.com/teamcity/](https://www.jetbrains.com/teamcity/) which builds automatically from github checkins.
[*]Test tomcat -- tomcat7 instance.
[*]Other things not really relevant to the discussion.
[/LIST]

TeamCity runs under a non-root user and has been working for a long time.  8.1 is not the latest greatest.

Test tomcat runs non-root, I don't particularly care which one but for now let's say testtomcat user.

When I get a successful build/testing from teamcity, I want this to happen:
[LIST=1]
[*]Shutdown test tomcat
[*]zap temp directories and logs for test tomcat
[*]delete .war and exploded war from testtomcat/webapps
[*]Put the new .war into webapps
[*]Startup test tomcat.
[/LIST]

I also want testtomcat to be running on system start.

The problems are:
[LIST=1]
[*]If I use /etc/init.d script to start testtomcat, teamcity can't run the script because it is not root.
[*]I can't change permissions on the /etc/init.d script because there are checks for that, and Ubuntu seems to be wired to not like wrong permissions in this directory.
[*]If I use $CATALINA_HOME/bin/ startup.sh and shutdown.sh, teamcity can restart the service (if testtomcat user is teamcity user) but the service does not start at boot, and the /etc/init.d script is broken.
[*]Using sudo from teamcity raises my hackles, and doesn't work anyway.
[/LIST]

Does anyone have a working solution for this?

I would like to avoid teamcity plugins for this setup if possible.

Thanks.

---

