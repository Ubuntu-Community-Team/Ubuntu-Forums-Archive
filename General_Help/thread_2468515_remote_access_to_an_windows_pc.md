---
title: "remote access to an windows pc"
date: 2021-11-01
forum: General Help
---

### Post by T6&amp;sfpER35% on 2021-11-01
Here's the setup , i have a windows 10 pc at work (connected to the work's network) which i can log into , but i don't have admin rights .
Now there's one specific program on the work pc that i want to access from my home pc (xubuntu obviously) . This program (sage 300 people) runs through a browser on the work pc,and through the work's network therefore i quess.
The program ( or more of a web self-service thing) is accessed from the work's intranet but i can also launch it from a browser, but only from my work pc.
Is there a way i can access this program from my home pc ?

---

### Post by dragonfly41 on 2021-11-01
I'm sure that there are multiple ways but whether the company security policy allows is another matter.
My first rough thought is to install ngrok on your Sage client PC. Then you can tunnel to your Sage URL through ngrok session (perhaps a simple rerouting in your ngrok index.html which is open to public). You might add a password in .htaccess.

[https://www.twilio.com/docs/usage/tutorials/how-use-ngrok-windows-and-visual-studio-test-webhooks](https://www.twilio.com/docs/usage/tutorials/how-use-ngrok-windows-and-visual-studio-test-webhooks)

Wait for other easier remote working ideas before trying this.

---

### Post by The Cog on 2021-11-01
That sounds like inviting instant dismissal to me. Get permission before trying that.

---

### Post by dragonfly41 on 2021-11-01
As I wrote (clearly I thought) it depends on security policy in force and an understanding, in this remote working world we are all in today.
Otherwise persuade the company to grant you a remote working licence to access Sage.

---

### Post by T6&amp;sfpER35% on 2021-11-01
yes i thought it might be a problem if i don't have permission to log into their network from home , but all i really want to do is log into the Sage interface, which the work gave me access to , from home.
i thought there might be a simple way...anyway ,guess i'll have to ask the IT guys at work for permission. Probably will be denied .

---

### Post by QIII on 2021-11-01
Their network, their rules.

Since you will have to work this out with them, I'll avoid having others spend their time with suggestions.

Closed.

---

