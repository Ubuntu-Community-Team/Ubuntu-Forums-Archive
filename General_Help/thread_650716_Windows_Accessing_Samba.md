---
title: "Windows Accessing Samba"
date: 2007-12-26
forum: General Help
---

### Post by futureal on 2007-12-26
Hi,

I've configured Samba a number of times in the past and never had any real issues, but I am having one now. I just installed Ubuntu on a new PC, and set things up as always. Security is set to user, the workgroup matches the one I am on, and I have a single share set up. I've added a user account for my Samba user via:

smbpasswd -a account

So all appears well. From Windows, I try to open:

\\192.168.1.xxx (address of my linux machine)

It prompts me for a login box, where I enter the user/pass that I set up above. All seems well. I get a list of the shared stuff, in this case my single shared directory.

However, when I click on that shared folder, I get *another* login box, prompting me for:

Login: WINDOWSHOSTNAME\sambauser (pre-filled)
Password:

No matter what I enter here, it fails. Also, each time I try something I see neither an event in the Windows log nor an event in the Samba logs (log.smbd or the machine-specific log.xxx files), which makes me think this is a Windows-side issue.

Has anybody encountered this or have any ideas on what I could do to solve? In the past when I've set this up I haven't had this issue, and I don't think I'm doing things any differently. :(

Note that this happens if I access the machine via \\192.168.1.xxx or \\hostname, same result.

---

### Post by futureal on 2007-12-26
One addition: if I set security = share, and I attempt to access from Windows, it now gives me a login with a grayed out "WINDOWSHOST\Guest" as the name and prompts for a password.

Still totally stumped. :(

---

### Post by bollix47 on 2007-12-26
I had a very similar problem.

Used this [Samba Howto]("http://ubuntuforums.org/showpost.php?p=1174825&postcount=1") and the problem went away.

Hope it can help you too.

---

