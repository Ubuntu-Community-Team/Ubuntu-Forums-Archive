---
title: "Problem on running update"
date: 2022-08-16
forum: General Help
---

### Post by satimis on 2022-08-16
Hi all,

Ubuntu 22.04 desktop

On Terminal running;
$ sudo apt update ```

....
....
All packages are up to date.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://download.opensuse.org/repositories/home:/Provessor/xUbuntu_20.04  InRelease: The following signatures were invalid: EXPKEYSIG 876292BF7F9C32BF home:Provessor OBS Project <home:Provessor@build.opensuse.org>
W: Failed to fetch http://download.opensuse.org/repositories/home:/Provessor/xUbuntu_20.04/InRelease  The following signatures were invalid: EXPKEYSIG 876292BF7F9C32BF home:Provessor OBS Project <home:Provessor@build.opensuse.org>
W: Some index files failed to download. They have been ignored, or old ones used instead.

```
Please advise how to solve the problem.  Thanks

Regards

---

### Post by &amp;KyT$0P# on 2022-08-16
Where did you get the signing key for that repo?  Try re-downloading that key from the same source in case they've updated it?

---

### Post by satimis on 2022-08-17
> **halogen2 said:**
> Where did you get the signing key for that repo?  Try re-downloading that key from the same source in case they've updated it?
Hi,

Thanks for your advice.

This is an Ubuntu22.04 vm of Orcle VirtualBox.  It was installed several months ago.

Before I just ran "Software Updater" to update and upgrade the packages.  It went through without problem.  After finish on Terminal I ran;```

$ sudo apt autoremove

```
to remove those unwanted packages.  Also it went through without complaint.  But on running "sudo apt update" it pop up the problem as mentioned on my original posting.

Regards

---

### Post by deadflowr on 2022-08-17
The key expired.
In old releases you could run the commands from this link:
[https://tecadmin.net/expired-key-expkeysig-with-apt/]("https://tecadmin.net/expired-key-expkeysig-with-apt/")

But for 22.04 apt-key has been deprecated, so I don't know how that'll work.

The best solution is to disable the repository in Software and Updates.

---

### Post by satimis on 2022-08-17
> **deadflowr said:**
> The key expired.
In old releases you could run the commands from this link:
[https://tecadmin.net/expired-key-expkeysig-with-apt/]("https://tecadmin.net/expired-key-expkeysig-with-apt/")

But for 22.04 apt-key has been deprecated, so I don't know how that'll work.

The best solution is to disable the repository in Software and Updates.
Hi,

Thanks for your advice.

It is quite funny to me.  I installed the Ubuntun22.04 vm several months before downloading its ISO on Ubuntu website.  Afterwards I cloned 3 VMs, say;
ubuntu2204_00  (original)
ubuntu2204_01
ubuntu2204_02
ubuntu2204_03

They were working without problem.  Yesterday, I ran following steps on all of them
1. Software Updater - to update and upgrade packages
2. Restart VMs
3. On VM Terminal run;
$ sudo apt autoremove
then
$ sudo apt update.

All of them without problem except ubuntu2204_02 VM

I tried several times but the problem still remains

Regards

---

### Post by &amp;KyT$0P# on 2022-08-17
> **deadflowr said:**
> The key expired.
In old releases you could run the commands from this link:
[https://tecadmin.net/expired-key-expkeysig-with-apt/]("https://tecadmin.net/expired-key-expkeysig-with-apt/")

But for 22.04 apt-key has been deprecated, so I don't know how that'll work.

I think that method should still work if you use [FONT=Courier New]gpg[/FONT] directly instead of going through [FONT=Courier New]apt-key adv[/FONT] , just that you need to also use [FONT=Courier New]--keyring[/FONT] option to specify the exact keyring file.  Refer to [FONT=Courier New]man gpg[/FONT] for more info

---

### Post by ActionParsnip on 2022-08-17
[https://askubuntu.com/questions/650032/gpg-errorthe-following-signatures-were-invalid-keyexpired](https://askubuntu.com/questions/650032/gpg-errorthe-following-signatures-were-invalid-keyexpired)

---

