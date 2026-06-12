---
title: "Need help with ecryptfs"
date: 2015-12-26
forum: General Help
---

### Post by nicholas18 on 2015-12-26
I've been trying to install and use ecryptfs multiple times this morning. Never seems to quite work (I want an encrypted folder within my home directory that contains audio and written files). I have followed the following guides:

[https://help.ubuntu.com/lts/serverguide/ecryptfs.html](https://help.ubuntu.com/lts/serverguide/ecryptfs.html)

and to uninstall

[http://askubuntu.com/questions/128583/ho...te-private]("http://askubuntu.com/questions/128583/how-can-i-completely-remove-ecryptfs-from-my-system-and-delete-private")

Now the closest I got was that /srv when unmounted ws gibberish, when remounted said:

This file has been deprecated. Please add custom options for cron to
# /etc/init/cron.conf and/or /etc/init/cron.override directly. See
# the init(5) man page for more information.

Did I mess anything up? Can I just uninstall again? I just want an encrypted folder I can put **** in, (was it supposed to be /srv?) in my home folder. 

Thank You in advance for your time

---

### Post by deadflowr on 2015-12-26
You can ignore the instructions of doing it with sudo stuff /srv, if you simply want to have it in your home folder.
Just run:
```
ecryptfs-setup-private
```
And you'll create a new folder in your home folder called Private.
The community wiki is probably more apt for what you want to do:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by matt_symes on 2015-12-26
Hi

> **nicholas18 said:**
> I've been trying to install and use ecryptfs multiple times this morning. Never seems to quite work (I want an encrypted folder within my home directory that contains audio and written files). I have followed the following guides:

[https://help.ubuntu.com/lts/serverguide/ecryptfs.html](https://help.ubuntu.com/lts/serverguide/ecryptfs.html)

and to uninstall

[http://askubuntu.com/questions/128583/ho...te-private]("http://askubuntu.com/questions/128583/how-can-i-completely-remove-ecryptfs-from-my-system-and-delete-private")

Now the closest I got was that /srv when unmounted ws gibberish, when remounted said:

This file has been deprecated. Please add custom options for cron to
# /etc/init/cron.conf and/or /etc/init/cron.override directly. See
# the init(5) man page for more information.

Did I mess anything up? Can I just uninstall again? I just want an encrypted folder I can put files in, (was it supposed to be /srv?) in my home folder. 

Thank You in advance for your time

I just followed the instructions on the LTS page you linked to above, and they work in 16.04 and i suspect they'll work in 14.04.

You can create the folder in your home directory. It doesn't have to be /srv.

What exactly are you having problems with ? What version of Ubuntu are you using ?

Kind regards

---

### Post by DuckHook on 2015-12-26
I have an ecryptfs subdirectory on my /home directory called "Private". It was set up using the ecryptfs-setup-private utility, instructions [here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory").

Note that you followed highly generalized instructions for encrypting *any* directory, which is do-able, but overly-complicated for your needs. Moreover, such general instructions tend to be confusing because they require setting up either a passphrase file on a USB key (which is the method described in your link) or else a lot of manual configuration to register the passphrase in PAM (which is not even covered in the aforementioned link), which are both convoluted and difficult for new users. The ecryptfs-setup-private utility was designed to transparently create a "Private" directory and&#8213;most relevant to new users&#8213;automatically mount and decrypt the "Private" directory upon login. Just make sure that the ecrypt passphrase is *exactly* the same as your login passphrase, and you should have no problems. It must be *exactly* the same. Linux is case sensitive.

After the "Private" directory is created, you can put all of your sensitive info within it and symlink needed files back to the expected directories. This is the easiest, no-muss, no-fuss way to use ecryptfs.

EDIT

Oops. Ninja'ed by deadflowr, who suggests same solution.

---

