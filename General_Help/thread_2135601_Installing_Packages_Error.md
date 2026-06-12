---
title: "Installing Packages Error"
date: 2013-04-14
forum: General Help
---

### Post by sirflik on 2013-04-14
I could really use some help. I've been dealing with this issue for awhile now and have serched for weeks but can't find anyway to fix it. I basically can't install any programs or packages from anywhere. Everytime i do it gives me this:

The installation or removal of a software package failed

installArchives() failed:  Extracting templates from packages: 27%% Extracting templates from packages: 54%% Extracting templates from packages: 81%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 27%% Extracting templates from packages: 54%% Extracting templates from packages: 81%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 27%% Extracting templates from packages: 54%% Extracting templates from packages: 81%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 27%% Extracting templates from packages: 54%% Extracting templates from packages: 81%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 field name `../../../java-7-openjdk-common/jre/lib/compilefontconfig.jar' must be followed by colon 
Error in function: 

I'm not very good with this type of thing. I'm running Ubuntu 12.10. Thanks for any help.

---

### Post by ibjsb4 on 2013-04-15
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter one line at a time:

[http://ubuntuforums.org/showthread.php?t=1153932&p=7245217&viewfull=1#post7245217](http://ubuntuforums.org/showthread.php?t=1153932&p=7245217&viewfull=1#post7245217)

And welcome to the forums :)

---

### Post by schragge on 2013-04-15
IMHO, the advice in next after the linked post is easier to follow. :)

---

### Post by ibjsb4 on 2013-04-15
> **schragge said:**
> IMHO, the advice in the next post after the linked one is easier to follow. :)

An update will not repopulate /available :)

---

### Post by schragge on 2013-04-15
So what? Are you still using *dselect* that you care about completeness of */var/lib/dpkg/available*? Besides, there was [thread=2116258]a thread[/thread] where */var/lib/dpkg/available* somehow got mysteriously repopulated by *apt-get update* :) so I guess nothing is impossible on Ubuntu.

---

### Post by ibjsb4 on 2013-04-15
Yep, must just be my box since an update didn't do it.  But enough of apples and oranges and back to the OP :)

---

### Post by sirflik on 2013-04-15
That link and those commands fixed it all! Thanks you guys! Consider this solved.

---

### Post by ibjsb4 on 2013-04-15
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

