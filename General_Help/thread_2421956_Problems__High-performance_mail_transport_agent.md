---
title: "Problems?  High-performance mail transport agent?"
date: 2019-06-29
forum: General Help
---

### Post by PDA1 on 2019-06-29
Ubuntu wants to install the latest updates but the High-performance mail transport agent has some sort of problem.  

Below is the error message-

The package system is broken.

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

mailutils: Depends: mailutils-common (= 1:3.4-1) but 1:3.4-1 is installed
           Depends: mail-transport-agent but it is a virtual package

I tried the apt-get intall -f command and it asks a bunch of questions which I have no idea how to answer.  If it helps- I run Thunderbird.

How do I fix this? (Without destroying my system)

Thanks,

Peter (my name....today)

---

### Post by TheFu on 2019-06-30
First, which Ubuntu release are you using?  I'm on 16.04.6, so all the answers below are for that release. Things are a little different in later releases, but shouldn't be THAT different.

Thunderbird has nothing to do with the MTA used.  Thunderbird is a client mail application that doesn't need a local MTA to work.  An MTA is a server application that you would have specifically installed and manually configured.  postfix, exim, sendmail are the most common examples.

Somehow, mailutils was installed.  Ask to remove that and see which other dependencies will also be removed. Then you'll be able to decide which other package forced the mailutils install.  I have postfix installed and configured on most of my systems for "send-only" email. It doesn't use mailutils or mailutils-common, so those aren't tied together.  Very few desktop programs would require any MTA at all; actually, I can't think of any.

Also, the messages above say to disable any PPAs. Have you done that?

---

