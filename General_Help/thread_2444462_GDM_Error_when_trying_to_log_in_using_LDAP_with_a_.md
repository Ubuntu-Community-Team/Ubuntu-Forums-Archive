---
title: "GDM Error when trying to log in using LDAP with a username starting with a number"
date: 2020-05-30
forum: General Help
---

### Post by tylerecouture on 2020-05-30
Hey folks, I run a high school computer lab with Ubuntu 16.04 and I'm trying to upgrade it to 20.04.  Unfortunately my organization uses usernames that are 7 digit numbers, which is causing me problems.

We are using OpenLDAP for authentication, and on the client computers I am installed LDAP/NSS/PAM with the [instructions provided by debian]("https://wiki.debian.org/LDAP/NSS#NSS_Setup_with_libnss-ldapd").  I have tried both `libnss-ldap`, and `libnss-ldapd` 

They both work...as long as a user's username does not start with a number (or in libnss-ldap case, usernames also can't have a period in them either).  Unfortunately, all of the usernames in my organization are seven digit numbers!

Here is the error when trying to log in with username `9999999`:

    > ...gdm-password][5010]: pam_unix(gdm-password:session): session opened for user 9999999 by (uid=0)
    ...gdm-password][5010]: pam_systemd(gdm-password:session): Failed to get user record: Invalid argument

Where as here are the same logs when trying to log in with the username `test`

    > ...gdm-password][5242]: pam_unix(gdm-password:session): session opened for user test by (uid=0)

I am guessing that the problem is associated with [this systemd bug report]("https://github.com/systemd/systemd/issues/15141") and it looks like the issue may have been fix there?

Can anyone advise me how to upgrade my systemd to use the version that includes the fix, if that is the problem?

Note that this only prevents me from logging in the the desktop environment, users can still log in from a TTY or via SSH no problem. So I'm not sure how this relates to GDM, but it wasn't a problem that occurs with LightDM on 16.04

**Update:** If I switch to LightDM, it all works, all my users can log in to  the desktop environment.  So the problem appears to be with GDM.

---

### Post by DuckHook on 2020-05-30
This has caused problems for many before you. The problem is one of ambiguity. Beneath the user&#8209;friendly surface layer, Linux actually uses numeric UIDs and so must map alphabetic usernames to those numeric UIDs. When you use numbers for usernames, some parts of the system will get confused as to whether you are referring to a username or a UID. In your case, it is likely that OpenLDAP sees a number and assumes that it must look for an integer UID 9999999. It then chokes when it cannot find such a UID in the user database.

An example of the problems that can arise from such numerical ambiguity is the following: by default, Ubuntu assigns a numerical UID of 1000 to the system's first user. Anyone can see their UID with the simple shell command:```
id
```&#8230;If another user is then created with a username of "1000", but is assigned the UID of 1001, then what is the system supposed to do when you issue, for example, a *chown 1000* command? Which user are you acting upon?

systemd is a key and deeply integral part of the OS. I'm not sure how the rest of your OS will react to a systemd that is newer than the parts it was designed to pair nicely with. It has never occurred to me to perform such a heart transplant.

Although I don't know how to make the systemd substitution, I do have two suggestions:

[LIST=1]
[*]Since these are production machines, don't change anything on them until you've experimented on something else. This is one of those occasions that call for testing things out in a VM. Only when you are sure that it works in a VM should you consider rolling out the systemd substitution on your critical bare metal machines.
[*]An easy option is to change all usernames to alphanumeric ones. If 9999999 could be prefaced with k9999999, this would disambiguate the designation and make it obviously a username.
[/LIST]
I'm going to try doing more research on this topic, but may not find anything helpful.

---

### Post by DuckHook on 2020-05-30
*Thread moved back to **General Help** as the appropriate forum.*

---

### Post by tylerecouture on 2020-06-01
Thanks!  I'm not sure it's an LDAP issue since I can still authenticate?  TTY and SSH log-in works no problem.  And desktop log in also works on Ubuntu 16.04. It's only logging in to the desktop environment on 20.04 that causes the error.   I was hoping there was some PAM setting I could use to relax the username strictness, like `compat` but I don't really know what I'm talking about.

---

### Post by DuckHook on 2020-06-01
> **tylerecouture said:**
> …but I don't really know what I'm talking about.
Neither do I! :lolflag:

This is rich. You come here looking for detailed help and get nothing from me but a blast of over&#8209;generalized bombast that may not even apply to your specific issue. > …I'm not sure it's an LDAP issue since I can still authenticate?  TTY and SSH log-in works no problem.  And desktop log in also works on Ubuntu 16.04. It's only logging in to the desktop environment on 20.04 that causes the error.   I was hoping there was some PAM setting I could use to relax the username strictness, like `compat`
Perhaps there is. Hopefully, a more knowledgeable user will dive in here and can help you with that.

As out of my depth as I am with PAM and LDAP, the two suggestions I previously posted are still sound.

[LIST=1]
[*]If you want to try replacing systemd, experiment to your heart's content in a VM.
[*]Is there a reason the usernames can't be changed by simply prefacing each with a letter?
[/LIST]
In general (there I go with generalizations again), even if the system handles ambiguity gracefully, it's best not to rely on such smarts and make things as unambiguous as possible.

A further thought: does this happen in 18.04? If not, another strategy would be to upgrade only to Bionic and wait for the first point release of Focal before going for it. You could test Focal out in a VM to make sure it works in your circumstances. It is a good idea to wait for the first point release in any case, especially with production machines. A lot of bugs get squashed and regressions get fixed in those first few months.

---

### Post by tylerecouture on 2020-06-02
Update: If I switch to LightDM, it all works, all my users can log in to the desktop environment.  So the problem appears to be with GDM.

I had the same problem with 18.04 a couple years ago, so I skipped it hoping whatever the problem was would resolve by 20.04...hahahaha.  But my 16.04 lab is running out of time to upgrade!

---

