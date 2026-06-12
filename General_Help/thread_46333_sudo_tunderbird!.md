---
title: "sudo tunderbird!?"
date: 2005-07-04
forum: General Help
---

### Post by gibbsnich on 2005-07-04
Hi!
I installed Mozilla-Thunderbird with synaptic and copied my email from windows xp. 
After copying my emails I need to "sudo mozilla-thunderbird" if I just start it I cannot see my emails (there's the number of unread emails next to the folder-names, but all folders are empty).
It seems like I copied to files using "sudo cp...". 
So: How can I change the file-permissions or sth. so that thunderbird displays my email when I'm not "sudoing"?

Thanks in advance for any input!

Yours, Michael

---

### Post by tread on 2005-07-04
You need to change the owner of those files
chown -R username.username folder
will change the folder and everything inside it to owned by username.

---

### Post by gibbsnich on 2005-07-04
Thanks! Works great!
I can open thunderbird and see all messages.

But when I want to send/receive mails I get an "Alert"-prompt telling me 

"Could not initialize the browser's security component."
And there may be a problem with my browser's profile directory, r/w 
restrictions, harddisc full...

So I 

chown -R maw.maw /home/maw/.mozilla/firefox/wlw5hq2w.default/

Thinking /home/maw/.mozilla/firefox/wlw5hq2w.default/ is the profile directory... 
But that must be wrong, because I keep getting that message everytime I startup Thunderbird and try to send/receive. After clicking "OK" I can send/receive and I don't get the message again when I send/receive the next times. 
Everything works, it's just annoying.. Does anybody here know what to do?

---

