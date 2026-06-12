---
title: "Trying to use Pass, running into issues with GPG"
date: 2013-04-16
forum: General Help
---

### Post by Curtis.Everingham on 2013-04-16
Hello, and thanks in advance for any help!

I recently decided to switch the application I use to manage passwords. Unix Pass stood out to me as a great option, and I got to work setting it up.

I have run into several issues along the way, most of which I have been able to find solutions to via google.

[http://www.howtoforge.com/helping-the-random-number-generator-to-gain-enough-entropy-with-rng-tools-debian-lenny](http://www.howtoforge.com/helping-the-random-number-generator-to-gain-enough-entropy-with-rng-tools-debian-lenny)
     Without understanding how or why, this was the only way I was able to get GPG2 to successfully generate keypairs.

[http://unix.stackexchange.com/questions/53912/i-try-to-add-passwords-to-the-pass-password-manager-but-my-attempts-fail-with](http://unix.stackexchange.com/questions/53912/i-try-to-add-passwords-to-the-pass-password-manager-but-my-attempts-fail-with)
     For a while, I was doing the same thing as the OP here, but have now corrected this problem.

Other than these two links, I have not found many useful/relevant information regarding the problems.

Where I am stuck now is retrieving stored passwords. I am able to use gpg2 to generate a keypair, use it to initialize a password store, and store passwords (at least it appears to be working this far). When I go to retrieve the password (with the bash command pass *pass-name*), I get the following:

user@host:~$ pass mail
gpg: gpg-agent is not available in this session
gpg: can't query passphrase in batch mode
gpg: Invalid passphrase; please try again ...
gpg: can't query passphrase in batch mode
gpg: Invalid passphrase; please try again ...
gpg: can't query passphrase in batch mode
gpg: decryption failed: secret key not available
user@host:~$

It is something I do not know alot about, but from the last line of the error message, can guess it has to do with a missing key. Was there something I missed when I generated it or initialized the password store? As far as I know, the secret key is right where it should be. It even shows up when I run gpg2 --list-keys:

user@host:~$ gpg2 --list-keys
/home/user/.gnupg/pubring.gpg
-------------------------------
pub   2048R/853E27DD 2013-04-16
uid                  user <user@mail.com>
sub   2048R/E60ACFF2 2013-04-16

I hope this is a clear enough account of what is happening here. I'm happy to clarify anything if it doesn't make sense

Thanks again to anyone taking the time to read this.



P.S. forgot relevant info like Ubuntu version - I'm running 12.04.2. all programs are up to date using apt-get update / apt-get upgrade

---

### Post by m4gnus on 2013-04-16
Are you using Pass for password storage mostly? I have never heard of Pass but it seems a little weird to me.
Have you looked into either [KeePass]("http://keepass.info/") or [KeePassX]("https://www.keepassx.org/")?

I found either of those are exceedingly easy to use. I personally switched to KeePassX just recently. Much easier to handle the keyfiles, IMO.
Also... What is gpg2?

I don't think they are affiliated with the gnupg.org project.

---

### Post by Curtis.Everingham on 2013-04-16
I don't know much about it, but GPG2 and GPG are mostly the same. GPG2 is the command called by pass, it runs just like GPG if I run it myself though.
     see here: [http://ubuntuforums.org/showthread.php?t=1001120](http://ubuntuforums.org/showthread.php?t=1001120)

---

### Post by akerfeldt on 2013-05-30
I solved this issue by setting GPG="gpg2" instead of the default GPG="gpg" in /usr/bin/pass

---

