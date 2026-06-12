---
title: "Cannot open my kwallet! and more"
date: 2007-05-08
forum: General Help
---

### Post by Homie Bongo on 2007-05-08
Please help! after restarting my Kubuntu Feisty system, I get several very bad errors.
All suspicious I did the last session was moving few big files out of my home partition, because there was 0 bytes space left on it.

First, I cannot open my wallet. When knetworkManager tried to conncet to network it asked me for the wifi key. Opening kwalletManager I see there are no wallets listed, so i located:wallet
I found two files in ~/.kde/share/apps/kwallet/
kdewallet.kwl        (some 14 KB)
kdewallet.kwlLtfVba.new       (148 B)
so the first file should be it, but opening it in the program only says:
> Sorry - KDE Wallet Manager
Error opening wallet home/me/.kde/share/apps/kwallet/kdewallet.kwl.
:'(

So I opened Konversation to try my luck on IRC only to get another error:
it cannot connect and only repeats:
> 
[23:37] [Info] Looking for server irc.ubuntu.com:8001...
[23:37] [Info] Server found, connecting...
[23:41] [Error] Connection to Server irc.ubuntu.com lost: operation is not supported. Trying to reconnect.
I cannot connect to irc.kde.org either

and as if it wasn't enough, not only that I cannot login to any forum without the passwords, but I cannot even check my Gmail in Konqueror - it says:
> Your browser's cookie functionality is turned off. Please turn it on.
I open the settings window > cookies tab and it only says:
> 
Unable to start the cookie handler service.
You will not be able to manage the cookies that are stored on your computer.

:confused: 

(fortunately I also use Firefox which remembers some of my passwords)

Please help, how can I get my passwords from the wallet? Any advicde with the Konqueror cookie or IRC problem will be appreciated too, thanks

---

### Post by Homie Bongo on 2007-05-08
oh, both IRC servers work again for me, it must have been some connection problem or what

---

### Post by Homie Bongo on 2007-05-09
one day after and my kwallet and cookies work again, what a relieve!

morning is wiser than evening they say in Czech, but what the heck could have caused the manager to refuse my wallet is beyond me

---

