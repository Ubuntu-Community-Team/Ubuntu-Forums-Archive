---
title: "What is the idea behind group passwords and group admins?"
date: 2014-10-26
forum: General Help
---

### Post by terminator14 on 2014-10-26
Earlier today, I found out that all groups on a linux system can have a Group Admin, and a password.
Now I'm trying to figure out why.

It's pretty easy to figure out the arguments the gpasswd command takes using the man page - so that's not what I'm after. What's less obvious is the idea behind group passwords and groups admins. Regular user's can't become part of any group they feel like, whether that group has a password or not, so having groups have passwords doesn't really make sense right away.

This is how I imagine Group Admins and group passwords work:

A new group is created by the System Admin (root) for a new project
A group administrator (aka Project Manager) is assigned to the group with gpasswd by the System Admin
Members are added to the group in one of two ways:
[LIST=1]
[*]The Group admin (Project Manager) uses gpasswd to add members to the group
[*]
[LIST]
[*]A password is set for the group either by the Group Admin, or the System Admin
[*]People who are to be group members are all given this password, so that they may use 'newgrp' to join the group for the current session

Note: If a group password is NOT set, this does NOT mean that any user can just join the group. This means that either the group admin or the system admin have to add members to the group manually (using usermod or gpasswd)
[/LIST]
[/LIST]
Can anyone confirm that this is indeed the idea, or correct me if I'm wrong?

---

### Post by 1clue on 2014-10-26
I never liked group passwords because more than one person has the password.

---

### Post by 1clue on 2014-10-26
Everything that can be done with gpasswd can be done without gpasswd.

You should look up how groups work and how permissions work.  And how sudo works.

I work a lot with servers for commercial use, and can't think of a single case where group passwords were used.  It's a security risk any time passwords are shared.

I would advise that you not change permissions or groups on any system-installed directories, unless you feel comfortable scraping your system off and starting over.  I've made more than one system unusable experimenting with this sort of thing, and if you're as curious and bold as I was then you probably will also, just try to do it on something disposable.  :)

---

### Post by 1clue on 2014-10-26
Generally speaking I will allow people to become members of a system-installed group (apache for example) and whatever else is necessary to administer the thing in question.

System permissions on any distro are very carefully thought out.  As much as you think you know about groups, you probably don't know as much about them as the people who set them up in the first place.  I'm going to assume you'll brick your box and have to reinstall a few times, it's a pretty common pattern when experimenting with groups and permissions.  No biggie, as long as your critical data is kept elsewhere and easily transferrable to the newly installed box.

Usually we have a Linux install for one basic purpose.  I leave the system permissions alone.  I create a couple groups, one would be a core group of people who can do anything and another would be people who have limited extra permissions, and yet another who might have read-only access to some things.

The core group is easy:  They're sudoers.  One of my favorite features of Ubuntu is the removal of the root user.  It still exists but nobody can log in that way.  There is no reason for a root password on a UN*X system.  Any sudoer can become the root user.

The limited extra permissions group is trickier.  I use 'consultants' often enough, it satisfies the use case for most of my systems.  These people have access to change some things, and sometimes run an extra command.  If there's something special you need them to do that doesn't seem to fit the existing permissions, you can give them access with sudo, to run a single command with extra privileges.

---

### Post by terminator14 on 2014-10-26
I appreciate the replies, but

1. I already know how groups work, how permissions work, and how sudo works
2. The fact that sharing passwords is unsafe is literally in the gpasswd man page. I'm aware of this
3. > **1clue said:**
> [I] can't think of a single case where group passwords were used. - while this is interesting, it doesn't really explain the purpose of gpasswd

I'm not trying to set group ownership on anything, change permissions of any kind, or figure out the best way to deal with permissions on some system. 
I'm trying to understand what gpasswd is theoretically used for, and why it exists. As far as I can figure, it just lets the admin either:
[LIST=1]
[*]Designate a person who adds/removes users from a particular group
[*]Set a group password and let the project members share it with whoever needs to be part of the group
[/LIST]

---

### Post by terminator14 on 2014-10-26
> **1clue said:**
> I'm going to assume you'll brick your box and have to reinstall a few times, it's a pretty common pattern when experimenting with groups and permissions.

Hard to brick your box when you're not doing anything with it...

---

### Post by whitesmith on 2014-10-26
> **1clue said:**
> ... 'consultants' often enough, it satisfies the use case for most of my systems.  These people have access to change some things, and sometimes run an extra command.  If there's something special you need them to do that doesn't seem to fit the existing permissions, you can give them access with sudo, to run a single command with extra privileges.

Yes, and you can run sudo in a way that can play back all the changes made to a system, by either a single user or group. Nifty. Nothing like it in Windows as far as I know. Look into this. It really comes in handy when you have assigned elevated privileges to more than one user, and then after something goes wrong, all shout in unison, "It wasn't me!" I'd never go back to the "good old days" when God's own password had to be whispered to users of widely varying technical understanding for something as simple as installing a program (that, or do everything yourself). Cheers.

---

### Post by terminator14 on 2014-10-26
> **whitesmith said:**
> Yes, and you can run sudo in a way that can play back all the changes made to a system, by either a single user or group.

Not related to my original post, but interesting. I've never heard of this superpower. Are you referring to Sudoreplay (which I just found after reading your post)?

On another unrelated note, awesome sig: "**In working with *nix...There be dragons.**"

Back to my Original Post: anyone know why linux lets you set passwords, and an admin for groups?

---

### Post by whitesmith on 2014-10-27
> **terminator14 said:**
> Not related to my original post, but interesting. I've never heard of this superpower. Are you referring to Sudoreplay (which I just found after reading your post)?

Yes, that's the one. Really stops the "Not me" noise.

---

### Post by tgalati4 on 2014-10-27
If you read up on the history of groups in Unix, it was useful in a single-computer environment with many, many users logged in.  So you could have a finance department group, and a human resources group, and a sales group.  Group passwords were needed to start and stop services for each of these groups, without disrupting the overall system.  It's a poor-man's hypervisor, before hypervisors were conceived.  Think early 1980's.

I can't think of a Use Case today that would need group passwords.  Normally, virtual machines would be spun up to support difference groups of users, and the administrator of that vm would be the "group" administrator.  There are security risks with having multiple group passwords in a single OS, because that allows multiple vectors for compromise.

So to answer to OP's question:  *Because We Can.*

---

### Post by terminator14 on 2014-10-27
> **tgalati4 said:**
> If you read up on the history of groups in Unix, it was useful in a single-computer environment with many, many users logged in.  So you could have a finance department group, and a human resources group, and a sales group.  Group passwords were needed to start and stop services for each of these groups, without disrupting the overall system.

It sounds to me like this is something that can still be done, but without gpasswd. If you make the binary of a service owned by a group, and allow members of that group execute permissions for that binary, then as long as the service doesn't make any calls to C functions that require root privileges, members of the group can run it.
gpasswd and group passwords appears to be geared towards controlling how users become members of a group, more than what the group can do. Am I wrong about this, or is that what you meant?

---

