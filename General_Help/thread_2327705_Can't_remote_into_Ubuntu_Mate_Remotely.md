---
title: "Can't remote into Ubuntu Mate Remotely"
date: 2016-06-13
forum: General Help
---

### Post by ktz84 on 2016-06-13
I have used the following guide to setup xRDP on Ubuntu 15.10. I am able to log in from my local network however when I log in through my tethered mobile phone data connection it doesn't connect. Any idea what could be up. The IP is definitely right. I'm connecting from remmina.

---

### Post by X-RED_Tech on 2016-06-13
> **ktz84 said:**
> I have used the following guide to setup xRDP on Ubuntu 15.10.

What guide?


> I am able to log in from my local network however when I log in through my tethered mobile phone data connection it doesn't connect. Any idea what could be up. The IP is definitely right. I'm connecting from remmina.
Whenever you're connection from outside the local network:
1. You need to use the public IP and
2. You need to setup port forwarding rules at the router.

This is all it can be said without further data.

---

### Post by ktz84 on 2016-06-13
Apologies. Copied the link but never pasted it.

[http://c-nergy.be/blog/?p=8498](http://c-nergy.be/blog/?p=8498)

I have the external IP set up and the port is forwarded to the internal ubuntu ip on port 3389 but wondering if that is the right port. How do I check?

Update. Ok definitely 3389 as I can append :3389 to the end of the internal ip address and it still connects.

---

### Post by X-RED_Tech on 2016-06-13
If the port forwarding is correctly set it should work by replacing one IP with the other, everything else being the same.
Have you rebooted the router after setting up the rule? Many need a reboot to make effective.

---

### Post by ktz84 on 2016-06-13
Hi it works. I'm an idiot. I forwarded 3398 and not 3389. I should have realised what I had done earlier because in my last post I put the wrong port in and changed them all :(

Thanks for your help.

---

### Post by X-RED_Tech on 2016-06-13
It happens and fortunately you spotted and corrected the mistake.

Now think about forgetting a coma in a remote command and bringing a server down; now picture that server being used by a notorious IT/Hardware multinational company in Europe... Yeah, I did that ...

---

### Post by ktz84 on 2016-06-14
> **X-RED_Tech said:**
> It happens and fortunately you spotted and corrected the mistake.

Now think about forgetting a coma in a remote command and bringing a server down; now picture that server being used by a notorious IT/Hardware multinational company in Europe... Yeah, I did that ...

That sounds like a nightmare scenario. Just goes to prove that no matter how good the person when humans are involved errors can and do happen. Sure we are all who we are we because of genetic mutations so I guess you could say we are hard wired for error :D

---

