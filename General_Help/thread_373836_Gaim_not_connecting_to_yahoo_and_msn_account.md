---
title: "Gaim not connecting to yahoo and msn account"
date: 2007-03-01
forum: General Help
---

### Post by Lionmew on 2007-03-01
I just installed Ubuntu and am trying to get Gaim to work with my Yahoo and MSN account.
All Gaim is telling me is "Disconnected: Unable to Connect"

I don't have a firewall.

Any idea if I need to make conig changes to the advanced options?

Thanks

---

### Post by Rooy on 2007-03-01
For a start, is there a network manager icon on the notificatin area? Does it have a exclamation mark? If so:
Go to System --> Preference -->Sessions, uncheck Network Manager there, logout and login, try gaim again
If that didn't work, open a terminal and:
sudo chmod -x /usr/sbin/NetworkManager
Log out and try again

If both has no effect, you might want to revert the changes back:
sudo chmod +x /usr/sbin/NetworkManager

---

### Post by squee on 2007-03-02
I am also unable to log into my msn account thru Gaim. Running 2.0.0 beta3 I get the message

....@hotmail.com disconnected

unable to authenticate: unable to connect.

Does anyone have an idea how to fix this? My sister has the same problem on the same computer but as a different user. Is this a Gaim problem or a Microsoft one?

Squee

ubuntu 6.06

---

### Post by squee on 2007-03-03
Ok i'v fixed it if anyone else has this problem. All you have to do is accounts>>add/edit  then delete your old account. Make up a new one exactly the same, Its annoying but it worked for me. Of course this could just be the kind of problem thats fixed with restarting or just waiting but anyway.

---

