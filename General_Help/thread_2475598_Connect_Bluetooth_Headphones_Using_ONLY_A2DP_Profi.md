---
title: "Connect Bluetooth Headphones Using ONLY A2DP Profile"
date: 2022-06-01
forum: General Help
---

### Post by Spiralagnus on 2022-06-01
I'm  running some experiments to see if I can get my Bluetooth  headphones  to connect to my desktop and my iPhone simultaneously:  desktop via A2DP  and phone via HFP. To make this work, I need to connect  to my desktop  using *only* A2DP, i.e. there  would be no HFP  profile on my desktop at all. (There's no way to  control audio profiles  on the iPhone, so I have to try to do it via  Linux.) I've seen plenty of  tutorials on making sure my computer  doesn't automatically switch to  HFP from A2DP, but I've found nothing  about ensuring my desktop doesn't  even try to make an HFP  profile/connection.

If it helps, I'm using Blueman 2.2.4 on Xubuntu 22.04.

I'd  appreciate any insight the community can provide. In particular, if  you've had luck in the past with simultaneous pairing with Linux and an  iPhone, please let me know how you did it. Thanks!

---

### Post by MAFoElffen on 2022-06-01
Maybe this(?): [https://askubuntu.com/a/1119934/1025239](https://askubuntu.com/a/1119934/1025239)

---

### Post by Spiralagnus on 2022-06-02
> **MAFoElffen said:**
> Maybe this(?): [https://askubuntu.com/a/1119934/1025239](https://askubuntu.com/a/1119934/1025239)

I've seen that post, and it's discussing how to keep Ubuntu from switching to HFP automatically, but it says nothing about how to prevent an HFP connection from even forming.

Interestingly, [Sony claims that I can do]("https://helpguide.sony.net/mdr/whch700n/v1/en/contents/TP0001613464.html")  exactly what I want it to do. Now, when I try to make a connection with  my desktop and then to my phone, the phone says it's connected, but the  Bluetooth device is not recognized if I try to make a call. *However,* if I plug an external Bluetooth transmitter into the desktop, connect to that, and *then*  connect to my phone, I can then listen to music from the desktop and  also make a call from my phone. Everything works as it should.I'm  assuming this is because the transmitter is making an A2DP-only  connection, which leaves the iPhone free to make an HFP connection. The  problem is that I won't always have access to a transmitter. I'd like to  make an A2DP-only connection from the desktop itself.

---

