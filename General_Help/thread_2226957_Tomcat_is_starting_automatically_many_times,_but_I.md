---
title: "Tomcat is starting automatically many times, but I've never  configured it"
date: 2014-05-29
forum: General Help
---

### Post by y-george-b on 2014-05-29
Running Xubuntu 13.10
I installed tomcat 8 ( not using apt-get ) by downloading the tar file and untarring it in /usr/local/ making a symbolic link like :
tomcat -> apache-tomcat-8.0.8
When I want to start it I run /usr/local/tomcat/bin/startup.sh and shutdown with /usr/local/tomcat/bin/shutdown.sh
I have never configured any init.d startup scripts but I was surprised to discover that tomcat started automatically after a computer reboot.
There is nothing tomcat related in /etc/init.d
Just now I found that there were multiple tomcat instances and java process running. When I killed -9 them they started up again
The only way I could stop then starting was to  rename /usr/local/tomcat to /usr/local/tom
I am completely confused by this !!
George

---

### Post by Toz on 2014-05-30
Hello and welcome to the forums.

That really is an odd problem. I can't replicate it even if I try. Do you save sessions at all? I wonder if its in a saved session somewhere. Try running the following command to see if it is:
```
fgrep -ri tomcat ~/.cache/sessions/*
```

---

