---
title: "Unity Mail won't send notifications"
date: 2014-04-17
forum: General Help
---

### Post by rkarulkar94 on 2014-04-17
I was using unity mail until I unpgraded to 14.04. When I tried installing it to 14.04, it installed successfully, but it does not show up in the messaging menu. I doesn;t even show any notifications when new mail is recieved and does not light the envelope blue. What could be wrong and how can I fix it?

---

### Post by batden on 2014-04-19
Did you try sudo dpkg-reconfigure unity-mail?

---

### Post by rkarulkar94 on 2014-04-19
Yes. I tried that as well as purging and reinstalling. The problem persists. When I launch it from the dash, it opens gmail in Firefox. That's it.

---

### Post by Canaryguy on 2014-12-14
Having the same problem.

I reinstalled Ubuntu 14.10 yesterday and today I installed unity-mail but it doesn't show new messages.

When I click on the letter icon which ist near the clock I see only three options: Thunderbird..., New message, Contacts. But unity-mail is not there.

When I execute unity-mail from Terminal I get this:

Unity-Mail: ERROR: Exception occured: b'[AUTHENTICATIONFAILED] Authentication failed.'
Unity-Mail: CRITICAL: Invalid account data provided for connection #0; exiting

---

### Post by Canaryguy on 2014-12-14
In my case I found what the problem was.

I had previously installed the firewall and I activated it. I deactivated the firewall and I set up Thunderbird and unity-mail again and everything is working once more.

---

