---
title: "KDEWallet insecurely displaying passwords via GUI to anyone around"
date: 2007-12-25
forum: General Help
---

### Post by Mguel on 2007-12-25
Is there a way to make kdewallet not to display (to anyone) passwords when that particular wallet is open (in use by an app)?

For example, I have kwallet to store my kopete passwords. I usually have kopete running so theat wallet is open too almost all the time I have my laptop turned on. In this situation anyone (ie while I go to the toilet) can view all my passwords stored on kwallet: 

Kmenu -> Setting -> Security & Privacy -> KDE wallet -> Launch Wallet Managet -> Open wallet (as the wallet is open it doesn't ask for a password!) and voilá, you can have access to see, read and copy ALL my passwords! (ie to see kopete passwords: Kopeete -> passwords -> account x -> Show contents)

If you remove kwalletmanager in access control from that wallet you can do the same, the only additional step is that you (anyone) have to Allow acces (once or allways) when prompted, but you can still get to the passwords to be displayed gracefully written... so what is the utility of encryption if the passwords are accessible via GUI?

Shouldn't this be password protected? ie on firefox even after you input the master password for the password manaager, if you go to the preferences and try to "show passwords" you are prompted for the master password to display them (I belive that is to prevent situations like the one I'm describing here with kde wallet).

Cheers, 
Mguel

PS: Using Kubuntu Gutsy 7.10, KDE 3.5.8, KDE Wallet Manager 1.1

PSS: also posted this on KDE-Forums.org

---

### Post by TidusBlade on 2007-12-25
Just tried a few things around, you can create a new wallet and password protect it, if that helps?
EDIT: My wallet has a master password for some reason....

---

### Post by Mguel on 2007-12-25
> **TidusBlade said:**
> Just tried a few things around, you can create a new wallet and password protect it, if that helps?
EDIT: My wallet has a master password for some reason....

Hi, thanks for the answer.

That was my first thought also. But I haven't been able to manage to use more than one wallet. I created a couple of other wallets, but I haven't been able to make different apps use different wallets. I thought to use a wallet "Mguel" for all my passwords and another "Master" to open Wallet Manager (besides "kde wallet" wallet ie for wireless networks without password so it connects automatically). 

But although creating several wallets it stores passwords only on the one I set on "Select wallet to use as default" (on "Automatic Wallet Selection" on "Wallet Preferences"). And I can't leave blank the use as default... maybe that would make kde wallet ask me where I want to store the password for the app that is requesting storing a password. Also I've deleted the kwalletmanager entry at the Access Control of the different wallets hoping that when it would need to access a wallet it would ask me in which one I would like to store a specific password... but it only tried to store it on the one set as default.

I hope I made my self clear... if not, please let me know to explain the issue better.

Thanks,
Mguel

---

### Post by jtheuer on 2008-01-02
you can either configure kwallet to close the wallet after x minutes and/or when the screensaver is on (i.e. you close your laptop-lid or you click "lock screen". That is what I always do and what I prefer!

Jan

---

### Post by Mguel on 2008-01-02
> **jtheuer said:**
> you can either configure kwallet to close the wallet after x minutes and/or when the screensaver is on (i.e. you close your laptop-lid or you click "lock screen". That is what I always do and what I prefer!

Jan

I don't think that is secure enough. I would prefer how things work for TideBlade or how things work on Firefox. If I would have to rely in locking the screen, waiting for the screen saver or wait  the wallet to lock by itself (what would imply entering the wallet passwords many many times during the day) I prefer not to use the wallet at all. For the inherent insecurity of this and because the usability of having to be worried constantly on locking and having to open the wallet every several minutes (besides as I told before I usually have on several programs which use the wallet).

Thanks anyway for the reply, cheers,
Mguel

---

