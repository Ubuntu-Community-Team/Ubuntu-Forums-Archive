---
title: "Ubuntu for crypto currency (Maxcoin) troubles"
date: 2014-02-09
forum: General Help
---

### Post by candtalan on 2014-02-09
I am trying to use Ubuntu with a cryptocurrency, in this particular case a new one, 'Maxcoin'. In the preparations, I asked about use with Ubuntu, and received a rather glib response, 'It is a distibution of Linux and we will provide a linux file' (or similar). In the event, stuff was provided, via github. Unfortunately, the wallet (client) executables fail from lack of various dependencies. Linux! Pah! I Have a 32bit machine, with Ubuntu 12.04 and Ubuntu 13.10, also a 64 bit machine with Ubuntu 12.04. Concentrating on the binary 'maxcoind'
[https://github.com/Max-Coin](https://github.com/Max-Coin)
specifically
[https://github.com/Max-Coin/clients](https://github.com/Max-Coin/clients)
with  	Maxcoin-linux32
	Maxcoin-linux64
Sadly no deb packages are (yet?) provided.
When I try to run the binary (I know, I know...)
I get apparent dependency errors.
Lot of  detail: [https://bitcointalk.org/index.php?topic=455662.msg5022545#msg5022545](https://bitcointalk.org/index.php?topic=455662.msg5022545#msg5022545)
In general this stuff  is done by experts, which I am not.

The function of the client here, slightly unusually, is both as a 'wallet'  to store any coins value, and secondly as a 'mining' (solo, not group) app.
I have failed to run the binary in the 32 bit machine, (Ubuntu 12.04 and 13.10). 

In the 64 bit machine I (somehow) got maxcoind (the terminal based 'wallet' & mining) running and successfuly configured it for mining, seems to work. I dare not do any more investigation in case I wreck my uninformed success.

Normal life with cryptocoins needs a gui wallet, currently the client maxcoin-qt
Maxcoin-qt does not run in the 32 bit machine nor in the 64 bit Machine.

If anyone is currently getting success specifically with these items I would love to hear. 
Incidentally, the main original bitcoin wallet runs ok (bitcoin-qt, satoshi, [http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu](http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu)) but the maxcoin uses unique encryption and I guess needs its own wallet.

If anyone is currently getting success specifically with these items I would love to hear. 
TIA

---

### Post by ken19 on 2014-02-25
check out 
[http://www.reddit.com/r/maxcoin/comments/1y85sq/very_simple_instructions_ubuntu_gui_wallet/](http://www.reddit.com/r/maxcoin/comments/1y85sq/very_simple_instructions_ubuntu_gui_wallet/)
I got the wallet loaded, now I am trying to get minerd to work right.

---

### Post by candtalan on 2014-02-26
Thanks I will try that, it looks much more hopeful. I do have minerd working (as a non expert), if you think I can help, shout?

---

