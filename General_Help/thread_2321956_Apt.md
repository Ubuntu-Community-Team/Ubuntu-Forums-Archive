---
title: "Apt"
date: 2016-04-25
forum: General Help
---

### Post by nabz0r on 2016-04-25
Hi,
I am getting the following, is it normal? How to fix it?

 W: GPG error: [http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1G7L3K23KUP1P123
W: The repository 'http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10  Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: There is no public key available for the following key IDs:
1G7L3K23KUP1P123

---

### Post by vasa1 on 2016-04-25
Are you trying to download something related to the Arc theme?

Please provide the actual command you ran and not just the resulting output.

Did you read the instructions provided at [http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme](http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme) ?

And which version of Ubuntu are you on? The Arc theme won't work for 14.04.

---

### Post by nabz0r on 2016-04-25
I have downloaded the theme but I removed it and after that I tried to update and I got that message.
Yeah, read the instructions and I have used that theme before in my 15.10. I now use 16.04, how to get rid of that?

---

### Post by oldos2er on 2016-04-25
You can add the key with ```
wget http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/Release.key

sudo apt-key add Release.key
```

---

