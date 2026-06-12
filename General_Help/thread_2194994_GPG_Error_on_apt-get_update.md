---
title: "GPG Error on apt-get update"
date: 2013-12-21
forum: General Help
---

### Post by johnnydoe on 2013-12-21
I am getting the following error when doing sudo apt-get update

```
W: GPG error: http://ppa.launchpad.net saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DF9B28CA252A784
W: GPG error: http://ppa.launchpad.net saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886


```

I've tried importing keys, but get a timeout error every time.

Any suggestions?

---

### Post by raja.genupula on 2013-12-21
From Old : [http://ubuntuforums.org/archive/index.php/t-2017180.html](http://ubuntuforums.org/archive/index.php/t-2017180.html) Look at Matt post over there. 

He got the good shot.

---

### Post by johnnydoe on 2013-12-21
I tried Matt's suggestion:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4DF9B28CA252A784
```

It timed out and I don't know all of the mirrors to try...I did try the .mit mirror and it was unsuccessful.

I then tried the suggestion mentioned further down on that page:

```
$ sudo -i

    # apt-get clean

    # cd /var/lib/apt

    # mv lists lists.old

    # mkdir -p lists/partial

    # apt-get clean

    # apt-get update
```

I got the same error as mentioned in my original post.

---

### Post by johnnydoe on 2013-12-22
i am still unsure as how to solve this problem.

Thanks for your support.

---

### Post by claracc on 2013-12-22
Here, [http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey), you have a link, propossing various workarounds to import public key for ppa.

I think answer 23 can help you to fix your problem.

---

### Post by oldos2er on 2013-12-22
```
sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys 4DF9B28CA252A784

sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys C2518248EEA14886
```

---

