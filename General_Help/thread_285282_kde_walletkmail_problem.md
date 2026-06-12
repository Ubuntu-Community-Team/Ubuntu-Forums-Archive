---
title: "kde wallet/kmail problem"
date: 2006-10-26
forum: General Help
---

### Post by Remmelas on 2006-10-26
I have asked kmail to remember my passwords, which prompts a kwallet password (if it's not already open).  Fine, expected, etc.  The problem is, every time I open kmail, it asks for my kwallet password (fine, expected, etc) but then asks me AGAIN for all of my mail account passwords.  I've checked in the kde wallet, all of my mail account passwords are successfully stored, but kmail keeps asking for them anyway.  Any ideas how to correct or even troubleshoot?

---

### Post by Amt0571 on 2006-10-28
I'm having the same problem with Kopete...

Anyone knows what can cause this?

---

### Post by ltmon on 2006-10-28
I'm kind of glad that other people are having this problem... I thought I was going crazy.

I tried deleting my entire kwallet configuration and starting again:

```

rm .kde/share/config/kwalletrc
rm -rf .kde/share/apps/kwallet/

```

This has improved things, but I'm still getting some odd behaviour in kmail and on occasional complete freeze of KDE when entering a wallet password (which can be fixed by killing and restarting "kded").

Wish I could help, but hopefully someone will post a solution to this forum.

L.

---

### Post by Remmelas on 2006-10-29
Wrong solution, entirely, but, problem goes away if i use kwallet without a password...

---

### Post by ltmon on 2006-11-01
See my solution on [http://ubuntuforums.org/showthread.php?t=290612](http://ubuntuforums.org/showthread.php?t=290612)

---

### Post by twstokes on 2006-11-25
I'm pretty sure it's a KDE 3.5.5 problem because I upgraded Dapper and had the same issue.

I'm now running Edgy and my Kopete and KMail passwords work, but KWallet wasn't storing a passphrase to an SSH login of mine. Here's what I did to solve the problem for me:

1. Restart KDE so that KWallet "disconnects"
2. Run "kwalletmanager"
3. Opened the wallet I use - it prompted me for my wallet password
4. Noticed that the SSH server passphrase wasn't stored
5. Attempted to connect to SSH Server, and was prompted for passphrase
6. Entered the passphrase and clicked "Save password"

I then noticed a new password was added to my list in KWallet, and it solved my problem.

---

