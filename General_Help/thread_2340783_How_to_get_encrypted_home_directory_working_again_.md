---
title: "How to get encrypted home directory working again after password reset"
date: 2016-10-22
forum: General Help
---

### Post by WedgeHG on 2016-10-22
Hello,

I somehow managed to change my password to something other than what I thought it did and was thus unable to log in anymore. The password was easy enough to reset using recovery mode.

Fortunately I had written down my mount password. I used ''ecryptfs-wrap-passphrase /home/<user>/.encryptfs/wrapped-passphrase'' to recreate the wrapped-passphrase file using my mount passphrase and my new login password.

After rebooting I try to log into the GUI but this fails. It doesn't say that login failed... the screen goes black for a second like normal when logging in but then it goes right back to the login screen. That's odd, but I can switch to a TTY and log in just fine.

Problem is that when I log in via TTY my home directory is not mounted. I do as it suggests and run ''sudo ecryptfs-mount-private'' but this seems to fail. It prints "Insert auth tok with sig [xxxxxxxxxxxxxx] into the user session keyring" followed by "fopen: No such file or directory". Checking the logs, the relevant lines from /var/log/syslog are as follows:

```

sudo: pam_ecryptfs: Passphrase file wrapped
sudo: pam_ecryptfs: Unable to rewrap passphrase file
sudo: Failed to detect wrapped passphrase version: Permission denied
sudo: Error attempting to unwrap passphrase from file [/home/<user>/.encryptfs/wrapped-passphrase]; rc = [-13]
sudo: pam_ecryptfs: Error adding passphrase key token to user session keyring; rc = [-5]

```

Now, I know that the wrapped-passphrase file is ok because I can run ''sudo ecryptfs-recover-private /home/.ecryptfs/<user>/.Private/'' and this works: my encrypted home directory is mounted in /tmp/ecryptfs.xxxxxx and all of my files appear to be intact.

How do I get my system back to normal such that my home directory is mounted automatically when I log in?

Thank you in advance.

Edit: I probably should have included that this is Ubuntu 16.04 desktop edition.

---

### Post by WedgeHG on 2016-10-24
Figured this out. I was doing two things wrong which basically boiled down to a simple permissions error on wrapped-passphrase.

First, I should not have been running ''ecryptfs-mount-private'' using sudo. This should be run as your own user.

Secondly, and this is why I tried using sudo with the previous command (was getting permission denied errors), when I recreated the wrapped-passphrase file I did so from a livecd and had to use sudo to write to my user's home directory. This led to the file being owned by root and not being readable by my user.

So, changing the owner of the wrapped-passphrase file to my own user solved the issue.

---

