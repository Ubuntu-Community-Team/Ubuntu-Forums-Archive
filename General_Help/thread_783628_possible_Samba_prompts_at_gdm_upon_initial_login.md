---
title: "possible Samba prompts at gdm upon initial login"
date: 2008-05-05
forum: General Help
---

### Post by kevinfishburne on 2008-05-05
I'm using Ubuntu 8.04 Desktop AMD64 with all updates other than the proposed repo. After creating a new user, logging out, then logging in with the new user, I receive one of two prompts. Subsequent logins are normal. The first prompt says something like "Successfully added user joeblow" then continues normally after clicking OK. If I later delete that user, including the home directory, then recreate the user, the prompt says "Failed to add entry for user joeblow."

I can't find anything in any log files, but think it might be a problem with Samba or pam-smbpass. When creating a new user, a corresponding Samba account is automatically created somehow. When deleting the user, the Samba account is left in place and not removed. I think that after recreating the user and logging in again, the failure message appears because the Samba user already exists. The initial message is reporting that the Samba account was successfully created.

I did a search on the contents of certain files and found that error message inside pam_smbpass.so and libsmbclient.so.0.1. Is there a way to prevent these pop-up messages from appearing in gdm informing me of success or failure? Even pointing me to the config file that would tie pam_smbpass and gdm together would be a good start. Thanks all.

---

### Post by dpb on 2008-12-16
> The first prompt says something like "Successfully added user joeblow" then continues normally after clicking OK. If I later delete that user, including the home directory, then recreate the user, the prompt says "Failed to add entry for user joeblow."

I can't find anything in any log files, but think it might be a problem with Samba or pam-smbpass. When creating a new user, a corresponding Samba account is automatically created somehow. When deleting the user, the Samba account is left in place and not removed. I think that after recreating the user and logging in again, the failure message appears because the Samba user already exists. The initial message is reporting that the Samba account was successfully created.

I had a similar problem in symptom, and wanted to post a reply here in case anyone else ran into this.  Searching Google for 

```
ubuntu "failed to add entry for user"
```

produced only a small handful of results, so this seemed like as good a place as any.

I had an error where I changed my user name on a system, but upon logging in, got this warning (?) and had to click OK each time to proceed.  I tracked it down to a samba issue, and performed the following commands to clear things up.

First, I deleted both users from samba.  When I deleted each, I got partial error messages about certain components being deleted not existing, but other messages printed made it seem like it was continuing anyway.

```

sudo smb -L -x <old_username>
sudo smb -L -x <new_username>

```

Next, I created just my new user, supplying the same password as I use on the Linux side of things:

```

sudo smb -L -a <new_username>

```

After logging in again, I no longer got the prompt.

I suppose that the original poster's problem could be different, but manually running these commands could give a clue as to what is happening with the samba registration behind the scenes in GDM.

Good Luck!

---

