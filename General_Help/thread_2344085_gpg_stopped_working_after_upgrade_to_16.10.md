---
title: "gpg stopped working after upgrade to 16.10"
date: 2016-11-22
forum: General Help
---

### Post by vedek2 on 2016-11-22
Hello Community,

after upgrading to 16.10 yesterday, I cannot get gpg to work anymore. Before proceeding, I should point out that I couldn't use PGP / Enigmail from thunderbird after upgrading to 16.04 earlier this year. I traced that back to a problem with gpg-agent, all solutions of which I found online were to no avail. I also thought about de- and re-installing gnupg and gnupg2, but shied away from that when I saw what all depends on these packages.

So, let's go to diagnostics about the current problem:
```

$ grep -v ^# .gnupg/gpg.conf | grep -v ^$
default-key 62EB2A51keyserver hkp://subkeys.pgp.net
photo-viewer "display -title 'KeyID 0x%k'"
$ grep -v ^# .gnupg/gpg-agent.conf | grep -v ^$
default-cache-ttl 0
max-cache-ttl 0
$ which gpg 
/usr/bin/gpg
$ which gpg2 
$ dpkg -S $(which gpg)
gnupg: /usr/bin/gpg
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"
```
When I try to run gpg, the following happens, regardless of whether or not I move my .gnupg away or not. I killed the gpg-agent before moving the .gnupg, didn't change anything. I commented the use-agent line from my .gnupg/gpg.conf (as you can see above: it's not there any more), but the agent is still started on any of the following commands:

```

$ LC_ALL=C gpg --gen-key 
gpg (GnuPG) 2.1.15; Copyright (C) 2016 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Note: Use "gpg --full-gen-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: testname
Email address: a@b.c
You selected this USER-ID:
    "testname <a@b.c>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: agent_genkey failed: Operation cancelled
Key generation failed: Operation cancelled
```

```
$ LC_ALL=C gpg 
gpg: Go ahead and type your message ...
test message for ubuntu forum
gpg: no valid OpenPGP data found.
gpg: processing message failed: Unknown system error
```

```
$ LC_ALL=C gpg -d secretfile
gpg: encrypted with 4096-bit RSA key, ID 01234567890abcde, created 2013-12-29
      "Myname (mycomment) <me@host>"
gpg: public key decryption failed: Operation cancelled
gpg: decryption failed: No secret key
```
For this one, I have obviously changed the key details. I can find the key with `$ gpg --list-secret-key 0123456789abcde`, but `$ gpg --list-secret-keys | grep 0123456789abcde` doesn't show anything.

Now, unfortunately, I am once again frustrated after an Ubuntu Upgrade, so I come here for help and solace. What can I try? What more information do you need?

---

### Post by vedek2 on 2016-12-01
In the meantime, I have found out how to purge a deb package without caring about dependencies:
```

dpkg -P --force-depends gnupg
dpkg -P --force-depends gnugp-agent
dpkg -P --force-depends gnupg-l10n

```

After re-installing, I still have the same problems. Nobody got any ideas?

---

### Post by vedek2 on 2017-01-06
Hoping that someone, somewhere will read this thread after all, I continue my investigation. I still cannot use GPG.

I have started the agent in daemon mode with `--debug guru`. While trying to decrypt a file

```
$ LC_ALL=C gpg -d secretfile
gpg: encrypted with 4096-bit RSA key, ID 01234567890abcde, created 2013-12-29
      "Myname (mycomment) <me@host>"
gpg: public key decryption failed: Operation cancelled
gpg: decryption failed: No secret key
```

The agent's output is:

```

gpg-agent[13796]: handler 0x0123456789ab for fd 4 started
gpg-agent[13796]: DBG: chan_4 -> OK Pleased to meet you, process 12199
gpg-agent[13796]: DBG: chan_4 <- RESET
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- OPTION ttyname=/dev/pts/9
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- OPTION ttytype=screen-bce
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- OPTION display=:0
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- OPTION xauthority=/home/myname/.Xauthority
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- OPTION lc-ctype=C
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- OPTION lc-messages=C
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- GETINFO version
gpg-agent[13796]: DBG: chan_4 -> D 2.1.15
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- OPTION allow-pinentry-notify
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- OPTION agent-awareness=2.1.0
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- AGENT_ID
gpg-agent[13796]: DBG: chan_4 -> ERR 67109139 Unknown IPC command <GPG Agent>
gpg-agent[13796]: DBG: chan_4 <- HAVEKEY 0123456789abcdef0123456789abcdef01234567
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- HAVEKEY 89abcdef0123456789abcdef0123456789abcdef 0123456789abcdef0123456789abcdef01234567
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- HAVEKEY 0123456789abcdef0123456789abcdef01234567
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- RESET
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- SETKEY 0123456789abcdef0123456789abcdef01234567
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- SETKEYDESC Please+enter+the+passphrase+to+unlock+the+OpenPGP+secret+key:%0A%22Myname+(mycomment)+<me@host>%22%0A4096-bit+RSA+key,+ID+0123456789abcdef,%0Acreated+2013-12-29+(main+key+ID+0123456789abcdef).%0A
gpg-agent[13796]: DBG: chan_4 -> OK
gpg-agent[13796]: DBG: chan_4 <- PKDECRYPT
gpg-agent[13796]: DBG: chan_4 -> S INQUIRE_MAXLEN 4096
gpg-agent[13796]: DBG: chan_4 -> INQUIRE CIPHERTEXT
gpg-agent[13796]: DBG: chan_4 <- [ 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20 ...(540 byte(s) skipped) ]
gpg-agent[13796]: DBG: chan_4 <- END
gpg-agent[13796]: DBG: keygrip: 21 21 21 21 21 21 21 21 21 21 21 21 21 21 21 21 21 21 21 21
gpg-agent[13796]: DBG: cipher:  7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F 7F
gpg-agent[13796]: DBG: agent_get_cache '0123456789abcdef0123456789abcdef01234567' (mode 2) ...
gpg-agent[13796]: DBG: ... miss
gpg-agent[13796]: starting a new PIN Entry
gpg-agent[13796]: DBG: connection to PIN entry established
gpg-agent[13796]: DBG: chan_4 -> INQUIRE PINENTRY_LAUNCHED 12201
gpg-agent[13796]: DBG: chan_4 <- END
gpg-agent[13796]: DBG: error calling pinentry: Operation cancelled <Pinentry>
gpg-agent[13796]: failed to unprotect the secret key: Operation cancelled
gpg-agent[13796]: failed to read the secret key
gpg-agent[13796]: command 'PKDECRYPT' failed: Operation cancelled <Pinentry>
gpg-agent[13796]: DBG: chan_4 -> ERR 83886179 Operation cancelled <Pinentry>
gpg-agent[13796]: DBG: chan_4 <- [eof]
gpg-agent[13796]: handler 0x7f9176dc2700 for fd 4 terminated

```

As far as I understand it, the agent doesn't understand the AGENT_ID command which gpg sends, and then there's the "DBG: ... miss" line that seems to fail. Is it possible that therein lies the problem?

---

### Post by vedek2 on 2017-02-19
By coincidence, I found (part of) the root cause for the problem and the associated solution:

After installing packages gnupg1 and gnupg2, then purging gnupg1, I managed to get gnupg working on the command line. (Still don't know what was going on there.) Thunderbird was still disfunctional, though.

Then, I noticed that mail sigining and decryption works if and when I unlocked the key on the command line. gpg-agent tried to use pinentry-gnome3, but **that** doesn't work in my setup – I am using the Awesome window manager instead of the default Ubuntu thing.

pinentry-gnome3 then defaults to reading the password from the command line, which is fine when I sign or decrypt on the command line, but thunderbird (and evolution, to which I changed meanwhile) cannot handle that.

The solution: Update /etc/alternatives/pinentry using ```
update-alternative --config pinentry
``` to point to /usr/bin/pinentry-gtk-2 (or any other pinentry that actually gives you a GUI window for inputting the password, instead of prompting on the command line. Also, make sure the .gnupg/gpg-agent.conf doesn't specifically point to pinentry-gnome3.

On a related note, I'd like to deinstall pinentry-gnome3. but gnome-keyring depends on it (yay for a sensible choice of dependencies here).

---

