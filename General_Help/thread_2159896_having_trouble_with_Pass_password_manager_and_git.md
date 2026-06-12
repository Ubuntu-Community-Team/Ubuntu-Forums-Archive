---
title: "having trouble with Pass password manager and git"
date: 2013-07-04
forum: General Help
---

### Post by p4lmtree on 2013-07-04
I've been using pass on my laptop for a while now, and it's been the only computer with which I've used a password manager. I recently built a PC, and I'd like to sync my laptop's password store with my PC's. Here's where I am so far:


[LIST]
[*]Both computers have each other's public keys stored, so they can send/receive encrypted messages between them.
[*]I cannot `pass git push -u --all` from my laptop, but I can `pass git pull` from the PC.
[/LIST]

[LIST]
[*]When I try to push from the laptop, here is the error:
[/LIST]

```
error: failed to push some refs to me@me:path/to/pass/git/repo
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
hint: before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```


[LIST]
[*]When I `pass git pull` from the PC, it actually does pull the contents from the laptop....but I can't open any of the gpg files because they were all encrypted with my *laptop's* public key, not my PC's public key. The exact error that shows is this:
[/LIST]

```
gpg: decryption failed: No secret key
```


So here's what I need to figure out:

1. What exactly is keeping my laptop from being able to push?
2. How can I share my password store with my PC in such a way that the PC can actually use the passwords?

So far the only advice I've gotten in other forums is "oh you should just use [this] password manager instead." I don't want to, so please help me figure out how to use the git function in Pass!

Laptop: Lubuntu 12.10
     PC: Ubuntu 13.04

---

