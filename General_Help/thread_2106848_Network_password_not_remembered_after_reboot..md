---
title: "Network password not remembered after reboot."
date: 2013-01-20
forum: General Help
---

### Post by gamingfreakk on 2013-01-20
So I'm brand new to lubuntu or linux in general for that matter but I decided to give it a try on a netbook I thought to be 100% useless with xp on it. So far I'm very impressed with how smoothly lubuntu runs on it. The only problem I've run into is what I stated in the title. I've managed to access my shared folder on my windows 7 machine without any problems It's just very annoying to have to type the password every time after a reboot on the netbook. I set it to remember forever but it just doesn't want to do it. Is there a fix for this or do I just need to live with it?

Thanks for the help.

---

### Post by Cheesehead on 2013-01-20
The system should not be prompting you for passwords after your initial login, except if you are performing an admin function.

What do you mean by 'Network password'? Which password is it asking for? Account? Keyring? WEP? Something else?

When is the system promting you for this password? Can you describe the exact wording of the prompt (including the title)? Can you describe the steps you take before the prompt appears?

---

### Post by Morbius1 on 2013-01-20
Unfortunately I don't have an answer for the original question but I might have an answer to this one:
> **Cheesehead said:**
> What do you mean by 'Network password'? Which  password is it asking for? Account? Keyring? WEP? Something  else?
The "network" in question is the samba share located on the Windows box that is asking for credentials. The term "Network password" is one that's actually used in seahorse. A reboot seems to remove the saved password from seahorse.

This came up before and it appears to be happening in 12.10 but for the life of me I can't seem to reproduce the problem.

---

### Post by gamingfreakk on 2013-01-20
> **Cheesehead said:**
> The system should not be prompting you for passwords after your initial login, except if you are performing an admin function.

What do you mean by 'Network password'? Which password is it asking for? Account? Keyring? WEP? Something else?

When is the system promting you for this password? Can you describe the exact wording of the prompt (including the title)? Can you describe the steps you take before the prompt appears?

All I'm doing is navigating to the shared folder through the file manager on lubuntu. As soon as I open it a box pops up "Password required for share media on windows-pc". I put the password in and check the box to remember forever and then I can access the shared folder no problem. The only issue I have with it is it's not remembering forever like I told it to so I'm forced to put it in every time after a reboot. It's not the end of the world or anything it's just a minor annoyance.

---

