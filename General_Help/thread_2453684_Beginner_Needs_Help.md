---
title: "Beginner Needs Help"
date: 2020-11-15
forum: General Help
---

### Post by jack0987 on 2020-11-15
Not new to linux but not very good at it at all.

I have an eth wallet that I lost my password to by accident. I doubt I will be able to recover it
but thought I'd make a stab at it.

I install ubuntu 20.04 (I think) on one of my computers and then installed the eth software. This program on github ([https://github.com/lexansoft/ethcracker](https://github.com/lexansoft/ethcracker)) worked spot on for me
about two years ago but having lots of problems now. I finally think I got the install for it done right.

Can you help? When I run it I get this message:

w12admin@W12:~/ethcracker$ go run src/ethcracker.go -pk donotuse.json -t test1.txt -threads 1
# _/home/w12admin/ethcracker/src/accounts/keystore
src/accounts/keystore/keystore.go:114:17: error: incompatible types in assignment (incompatible type for method ‘SelfDerive’ (different parameter types))
  114 |   ks.wallets[i] = &keystoreWallet{account: accs[i], keystore: ks}
      |                 ^
src/accounts/keystore/keystore.go:153:57: error: incompatible type for field 1 in struct construction (incompatible type for method ‘SelfDerive’ (different parameter types))
  153 |    events = append(events, accounts.WalletEvent{Wallet: wallet, Kind: accounts.WalletArrived})
      |                                                         ^
src/accounts/keystore/keystore.go:154:30: error: argument 2 has incompatible type (incompatible type for method ‘SelfDerive’ (different parameter types))
  154 |    wallets = append(wallets, wallet)
      |                              ^

---

### Post by TheFu on 2020-11-15
You really need to put _ethcracker_ into the thread title for any hope of getting help.

---

### Post by jack0987 on 2020-11-15
How does one change the thread title?

---

### Post by ajgreeny on 2020-11-15
Closed pending staff discussion.

---

### Post by DuckHook on 2020-11-15
This thread will remain closed. As per the Forum [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules"), though all participants on this thread may have honourable intent, discussion of password cracking is off limits: > From the Forum [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules")

…17. Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

---

