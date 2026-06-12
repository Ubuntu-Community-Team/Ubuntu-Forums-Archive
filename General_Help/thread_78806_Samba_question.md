---
title: "Samba question"
date: 2005-10-18
forum: General Help
---

### Post by schulermx on 2005-10-18
I'm not entirely sure if this is possible to do with Samba but here we go.

I've gone through the steps of selecting what folders I want to share, and I've made them all readable, but not writable. I want to have these folders available to everyone on the Network. Let's say for instance my network name is "schulermx" and I set in my smb.conf "netbios name = schulermx".

If I try to mount "schulermx" in Linux or access it in Windows using \\schulermx it, like it should, comes up with a password prompt. Is there anyway I can have it so the end user just presses 'enter' and poof, all the shared files come up? I don't want them to have to enter a password or a certain username. I know this isn't very secure but I would like to initially have things set up this way.

Thanks in advance

---

### Post by drogoh on 2005-10-19
From smb.conf.default on my FreeBSD machine:

```

[public]
      path = /usr/somewhere/else/public
      public = yes
      only guest = yes
      writable = yes
      printable = no

```

Perhaps it can help.  The comments summarized essentially say "these are the settings for a wide open share".

---

### Post by One Quick Question on 2005-10-19
The security setting is what does it. I believe it's set to "user" by default, which brings the username/password prompt.

Stick *security = share* into smb.conf (or change it to equal share if it's already set to user), restart Samba, and you should be good.

EDIT:
Oh yeah... do you also need to set those guest settings too?  I forget...       If you still get the prompt, try these out:
[i]guest ok = yes
guest only = yes[/i]
I don't remember if they're necessary for easy breezy access.

---

