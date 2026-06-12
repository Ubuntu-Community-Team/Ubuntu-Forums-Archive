---
title: "kwallet and knetworkmanager"
date: 2007-01-30
forum: General Help
---

### Post by DarkOx on 2007-01-30
I've a question about kwallet that I've been unable to answer. In Gnome, I'm able to use the pam-keyring so that network manager automatically starts up when I log in, without having to put in my wallet password. I'm given to understand that pam takes my login password and applies it to the keyring automatically. 

Is there any way to get kwallet to do something similar?

---

### Post by cri on 2007-02-07
My recommendation is not for the security paranoid, but you can remove the password from your wallet. In the "system settings" dialog select "security & privacy" and then "Launch Wallet Manager." Select your wallet and click "File-->Change Password." Finally, just click "OK" and then "Continue" and you'll be all set. 

The only things in my wallet are my knetworkmanager and kopete settings. People who store lots of passwords there may think twice before doing this.

---

### Post by maikoherajin on 2007-02-17
<laughs>

I can't believe the fix was that easy! It wants a password, so you just give it a blank one. I've been trying to figure out how to autologin to my router for HOURS. (:

Thank you, you have given me one fewer reason to dual boot Windows. Go KDE! (:

---

### Post by Vuen on 2007-03-09
Is there a way to do this without opening up my wallet? I have other passwords stored in there (all my Kontact passwords basically), so opening up the wallet is not really an option. I have my computer set to automatically log in (because I'm not the only one who uses it), so I can't have it asking for the wallet.

It seems really dumb that by default it requires people to type their passwords twice (once to log in, once to open the wallet) just to get internet access.

---

### Post by NQbbe on 2008-06-02
KWallet supports multiple wallets, so you can create one with a blank password for storing your WEP/WPA key in, and just keep the others passwords in a secure wallet.

This article might help you a bit too: [http://fosswire.com/2007/09/18/kwallet-remembering-passwords-the-kde-way/](http://fosswire.com/2007/09/18/kwallet-remembering-passwords-the-kde-way/)

---

