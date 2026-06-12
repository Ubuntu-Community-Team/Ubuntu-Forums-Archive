---
title: "Fortune in the MOTD (console system only)"
date: 2007-10-30
forum: General Help
---

### Post by rearviewmirror on 2007-10-30
I want the MOTD to reflect a new fortune every time someone logs in.  I do not want a cron job updating the MOTD at a set interval but rather the bash profile to pull a new fortune for each user as they log in.  I've seen this done, but I'm just not sure of the procedure.

---

### Post by pjkoczan on 2007-10-30
> **rearviewmirror said:**
> I want the MOTD to reflect a new fortune every time someone logs in.  I do not want a cron job updating the MOTD at a set interval but rather the bash profile to pull a new fortune for each user as they log in.  I've seen this done, but I'm just not sure of the procedure.

You could probably accomplish the same thing just by putting a call to fortune in the .bash_profile or .bashrc. That will give a random fortune every time a new terminal or shell is brought up (even in X).

I'm not sure that updating the MOTD every time someone logs in is the wisest, for a few reasons:

- The MOTD is a system file, owned and only writable by root. You're going to have to give global write access to that file to do what you want. Granted, it's just the MOTD, but people can modify it as they please, including in very inappropriate ways.
- Where I work, someone was once offended by a fortune, so we don't support the program (it's available in an unsupported capacity).
- This gives the user no choice if they want to put something else in their shell (a message, a fortune from a specific subset, nothing at all).
- The MOTD is typically used for important system information, scheduled downtime, etc. Random sayings seem a little out-of-character.

I'm sure what you want is possible, I just don't think it should be done that way.

---

### Post by rearviewmirror on 2007-10-30
All very good points.  This should not overwrite the /etc/motd but rather just present one to each user locally.  The /etc/motd will be static file that is unchanged and still used to present information about the system and the legal disclaimer.  So I guess I should rephrase the request.  The fortune motd should only be sources form the user's bash profile, it is not to update the /etc/motd file in any way.

---

### Post by rearviewmirror on 2007-10-31
I've got it worked out.. I will post a how to shortly.  This does not modify the /etc/motd in any way.

---

### Post by rearviewmirror on 2007-11-05
> **rearviewmirror said:**
> I've got it worked out.. I will post a how to shortly.  This does not modify the /etc/motd in any way.


All that is needed is the following (assuming you have fortune-mod installed).


```
if [ -x /usr/games/fortune ]; then
    /usr/games/fortune -s     # makes our day a bit more fun.... :-)
fi
```

You can put this code in the .bashrc if you just want subsequent shells to display the message or you can add to the .bash_profile for initial login as well.  (.profile if no .bash_profile)

---

