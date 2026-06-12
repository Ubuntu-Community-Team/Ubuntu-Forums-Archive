---
title: "Getting a repository error on 'apt update'."
date: 2024-04-23
forum: General Help
---

### Post by stevermann on 2024-04-23
(Ubuntu 12.3.0-1ubuntu1~22.04)

```
sudo apt update 
```presents this error:


W: GPG error: [https://repo.linuxbabe.com]("https://repo.linuxbabe.com/") jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 752E173A3F8B04F5
E: The repository 'https://repo.linuxbabe.com jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


I really can't recall why linuxbabe was added to the repository. Could I simply delete '/etc/apt/sources.list.d/linuxbabe.lst'?

---

### Post by VMC on 2024-04-24
maybe it will work:
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 752E173A3F8B04F5
```

---

### Post by stevermann on 2024-04-24
Thanks, but nope, didn't change anything.

---

### Post by Rubi1200 on 2024-04-24
Go to Software & Updates >> Other Software >> remove the PPA from there (requires authentication).

Then run ```
sudo apt update
``` in a terminal.

Issue resolved?

---

### Post by stevermann on 2024-04-24
Same error.

---

### Post by wyattwhiteeagle on 2024-04-24
> **stevermann said:**
> (Ubuntu 12.3.0-1ubuntu1~22.04)

```
sudo apt update 
```presents this error:


W: GPG error: [https://repo.linuxbabe.com]("https://repo.linuxbabe.com/") jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 752E173A3F8B04F5
E: The repository 'https://repo.linuxbabe.com jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


I really can't recall why linuxbabe was added to the repository. Could I simply delete '/etc/apt/sources.list.d/linuxbabe.lst'?
I had this same issue with spotify.
Turns out that the public key I was using had expired.
I went to spotify's website and obtained the new public key.
The error went away after running the new command line's.

Try obtaining the new public key by visiting their website for the cli command line's for your *buntu distro.

---

### Post by stevermann on 2024-04-24
[COLOR=#000000]"Try obtaining the new public key by visiting their website for the cli command line's for your *buntu distro."

I tried that but there has been no activity on the LinuxBabes forum for two years.  And no answer to my query there.
I didn't get my UIbuntu from Linuxbabes.

Since I only have one folder that must be saved on this server, I am tempted to just start over.[/COLOR]

---

### Post by wyattwhiteeagle on 2024-04-25
> **stevermann said:**
> [COLOR=#000000]"Try obtaining the new public key by visiting their website for the cli command line's for your *buntu distro."

I tried that but there has been no activity on the LinuxBabes forum for two years.  And no answer to my query there.
I didn't get my UIbuntu from Linuxbabes.

Since I only have one folder that must be saved on this server, I am tempted to just start over.[/COLOR]

Answering 2 questions will help to locate which command lines you need.

What *buntu are you using? (Ubuntu, Lubuntu, Xubuntu, etc)
What linuxbabe app's do you use?

Maybe something at this page will help.
It has only 3 search results for the public key your having problems with.
[https://www.linuxbabe.com/?s=752E173A3F8B04F5](https://www.linuxbabe.com/?s=752E173A3F8B04F5)

---

