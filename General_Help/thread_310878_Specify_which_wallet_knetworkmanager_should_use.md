---
title: "Specify which wallet knetworkmanager should use?"
date: 2006-12-01
forum: General Help
---

### Post by msak007 on 2006-12-01
As the title suggests, I'm looking for a way to specify exactly which wallet knetworkmanager should use. This is the problem I'm having:

1. I created a passwordless wallet in kwalletmanager for the sole purpose of knetworkmanager using it, so that it can connect on startup without a password prompt.

2. I created a second, password-protected wallet for all my other apps to store passwords (KMail, Kopete, etc.) so that I can be prompted for my password when launching one of those apps.

I can't figure out how to force knetworkmanager, and only knetworkmanager, to use wallet  #1, and all other apps to use #2. It defaults to wallet #2, and I have to enter a password every time I restart the session so that it will connect to my network. There's an option to specify a default wallet, and a wallet for "local" passwords. But none of the documentation I can find specifies what is determined as a "local" password. And I've also looked for a command line option to tell knetworkmanager which wallet to use (for example in a startup script), but couldn't find anything there. 

If anybody knows how to do this, please let me know!

---

### Post by msak007 on 2006-12-04
Anybody? All I want to know is if it's even possible to specify application-based wallets, and if so how to make it so knetworkmanager uses one specific wallet and all other apps use another one.

---

### Post by msak007 on 2006-12-08
Well I guess I'm to assume that nobody else uses knetworkmanager in conjunction with kwallet.

---

### Post by LordYama on 2006-12-31
Knetworkmanager automatically uses the default wallet in kwallet. I am able to force it to use a different wallet by changing the default, but that means that everything else would try to use it as well. As far as I can tell, there is no way to make knetworkmanager use a wallet of its own.

---

### Post by Vuen on 2007-03-09
I have exactly the same problem. I have my computer set to automatically log in (because I'm not the only one who uses it), so I can't have it asking for the wallet. Why doesn't knetworkmanager not have an option to simply not use the wallet at all?

It seems really dumb that by default it requires people to type their passwords twice (once to log in, once to open the wallet) just to get internet access. Is there a feature request where we can vote on this or something?

---

### Post by swilliams2008 on 2008-07-06
> **Vuen said:**
> I have exactly the same problem. I have my computer set to automatically log in (because I'm not the only one who uses it), so I can't have it asking for the wallet. Why doesn't knetworkmanager not have an option to simply not use the wallet at all?

The KNetworkManager I am running gives me the option to use no wallet but to use a text config file instead. This makes the crentials therein valid for all users of the system but as a downside leaves them stored in plain text.

I have stopped using KNM and gone back to using the traditional /etc/network/interfaces instead.

HTH

---

