---
title: "Ubuntu cannot locate bitcoin-qt executable"
date: 2016-10-04
forum: General Help
---

### Post by thanuntu on 2016-10-04
It's been a long time since I last used bitcoin, so I don't know since when I am affected but here goes...

I am on a Ubuntu 12.04 install running gnome-session-fallback.

I have installed bitcoin-qt through the repository ppa:bitcoin/bitcoin.
```
sudo apt-add-repository -y ppa:bitcoin/bitcoin
sudo apt-get install bitcoin-qt
```

The version is 0.13
```
apt-cache policy bitcoin-qt
```
gives
```

bitcoin-qt:
  Installed: 0.13.0-precise3
  Candidate: 0.13.0-precise3
  Version table:
 *** 0.13.0-precise3 0
        500 http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```

The bitcoin icon appears normally at the applications toolbar.

However, when I try to launch from the application icon I get error:
> Could not launch 'Bitcoin'
Failed to execute child process "bitcoin-qt" (No such file or directory)

Trying to do so from cli, is also useless:
```
:~$ bitcoin-qt
bitcoin-qt: command not found
```

I tried to remove-reinstall and then purge-reinstall, but to no avail.

Any thoughts?

---

### Post by #&amp;thj^% on 2016-10-04
That repository doesn't contain bitcoin-qt.
[https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin](https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin)

So my advice here is to remove what you have installed
```
sudo apt-get remove bitcoin-qt

```
The default client for Linux is the QT client so you just need:
```
sudo apt-get install bitcoin

```
Additionally, the 32bit version of this is currently failing to build
Hope this helps

---

### Post by thanuntu on 2016-10-04
Thanks for this.

I tried to remove this repository, but ```
sudo apt-get install bitcoin
``` produced > E: Unable to locate package bitcoin.

Then, as per the repo's description I saw that it does contain bitcoin-qt. I reselected the repo and tried again
```
sudo apt-get install bitcoin
```
only to get the same error.

Actually this is the repo bitcoin suggests for Ubuntu in its download page ([https://bitcoin.org/en/download](https://bitcoin.org/en/download)).

Is there something wrong with my installation?

---

### Post by thanuntu on 2016-10-04
I entirely removed the repo, resolved a problem with apt-get being unable to find a PGP signature
```

sudo apt-get update
W: There is no public key available for the following key IDs:
1397BC53640DB551

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551
```

ad then installed the default bitcoind.

When I tried to execute I got:
> bitcoind 
bitcoin is very out of date and has been removed.
Please see upstream sources at [https://github.com/bitcoin/bitcoin/](https://github.com/bitcoin/bitcoin/)
or the PPA at [https://launchpad.net/~bitcoin/+archive/bitcoin](https://launchpad.net/~bitcoin/+archive/bitcoin)

So, I did:
```
sudo apt-add-repository -y ppa:bitcoin/bitcoin && sudo apt-get update && sudo apt-get install bitcoin-qt
```

but then I got the same issue, bitcoin-qt could not be located.

---

### Post by #&amp;thj^% on 2016-10-04
I just showed you that it works... but you want to keep trying your way...I can only lead you to the water...the rest is up to you.
This PPA: Dose not show bitcoin-qt: [https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin]("https://launchpad.net/%7Ebitcoin/+archive/ubuntu/bitcoin") ...See Screenshot
```
bitcoin-qt 0.13.0-1

```
Good Luck

---

### Post by thanuntu on 2016-10-04
Look, I am not trying to abuse your time and I already thanked you for trying to help.

I CAN read you know...

If you take the screenshot from a little higher, you'll see that it does mention bitcoin-qt.
[ATTACH=CONFIG]271497[/ATTACH]

And bitcoin.org does mention that exact repo.
[ATTACH=CONFIG]271496[/ATTACH]

I assure you, I do know how to follow instructions.

Thanks again...

---

### Post by #&amp;thj^% on 2016-10-04
I never felt abused ;)...I volunteer my time with no conditions attached.
I am just a matter of fact type person.
So now that is out of the way...have you tried yet with:
```
sudo apt-get install bitcoin
```
Remember the 32bit version fails to build.

---

### Post by thanuntu on 2016-10-05
Hi again and thanks for hanging in with me.

Yes I did try it, both with the stock Ubuntu repo and the repo suggested by bitcoin.org. The stock repo only offers bitcoind (with the previously mention of it being outdated and pointing to the suggested repo) and the suggested repo gives the errors described above.

Just to clarify that I am on a 64bit installation.

---

### Post by #&amp;thj^% on 2016-10-05
Hi thanuntu This should help with the "bitcoind" Deb. (Note the "d" at the end)
Try to overwrite the existing version:

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/bitcoind_0.8.5-precise1_amd64.deb
```

And if I remember correctly you also need "libqtgui4"
```
sudo apt-get install libqtgui4 
```

If we have to we can build it from source if you so choose. (This route is a bit tougher though)
It also would not hurt to install the necessary parts needed.
```
 sudo apt-get install qt4-qmake libqt4-dev build-essential libboost-dev libboost-system-dev libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev libssl-dev libdb4.8++-dev
```
If you would be kind enough to show any errors you receive back here.
And Fingers Crossed...try and install bitcoind again.

---

