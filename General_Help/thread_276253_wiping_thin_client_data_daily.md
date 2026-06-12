---
title: "wiping thin client data daily"
date: 2006-10-12
forum: General Help
---

### Post by san983yfah10fnj0ujsa0 on 2006-10-12
I've just set up a thin client lab using edubuntu. It's working great: fast and without problems. I'm now looking for a way to easily maintain the lab.

What I'd like to do is wipe all the student work from the previous day clean and start fresh for the following day. I imagine I'll be setting up a cron job to do this, but actually figuring out what to tell the cron job to do has me baffled.

I thought I'd just tar the i386 folder and replace the working i386 folder each day with it, but I'm running into permission problems. I've run chown and chmod (from root), but there are still files that will not change ownership. When I try to tar (or even copy) the i386 folder, it either gives me a permissions message or, in the case of copying it, only gives me a portion of the folder hierarchy.

I'm I way off track? Certainly this is possible and much easier than I'm making it.

thanks!

btw, I've tried for two days to come up with a username, and everything I came up with was rejected because 'a user with that name already exists' (ie dsafjhgafuifbeiw), which must be incorrect. This one finally worked for whatever reason.

---

### Post by san983yfah10fnj0ujsa0 on 2006-10-13
So does no reply mean no one knows or no one understands what I'm trying to do?

---

### Post by Tomosaur on 2006-10-13
Well 1) Why would you want to do this, and 2) Why don't you just delete the subdirectories of /home/user?

---

### Post by san983yfah10fnj0ujsa0 on 2006-10-13
1) The thin clients are public terminals, and so I want to make sure the systems are secure and haven't been loaded with malware or some malicious script.  Also, beause the terminals are public, I don't want it to get filled with files and so forth--who knows what a student would put on it!  This terminal is mostly just for web surfing anyway.  So each morning, the computer would boot up and have no files retained from the previous day.

2) I am new to edubuntu and linux.  Is this the best way to accomplish what I want?  If the directories are removed each night, are they automatically regenerated on next boot up?  Please forgive if this is a stupid question.

Are there any other security/administration issues I should consider?

---

