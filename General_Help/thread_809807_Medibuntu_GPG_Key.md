---
title: "Medibuntu GPG Key"
date: 2008-05-27
forum: General Help
---

### Post by noynac on 2008-05-27
I cannot add the Medibuntu repositories and thought someone might be able to help.

To add Medibuntu, I first went to the following page:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I installed the repo's for Hardy:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

I checked the file, medibuntu.list, and it contained:

[I]## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free[/I]

I loaded synaptic and made sure that the Medibuntu repo was checked.

I then tried to add the GPG key as instructed on the Medibuntu page by entering the following in a terminal window:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

After entering the above, the package lists are updated and I get the following message:

[I]Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems[/I]

As instructed, I ran sudo-apt-get update and received the same error message.

I ran the following by itself in a terminal window:

*sudo apt-get install medibuntu-keyring*

I received:

*medibuntu-keyring is already the newest version*

I loaded synaptic and checked the Authentication tab of Software sources, and it showed Ubuntu Archive Automatic Signing Key and Ubuntu CD Image Automatic Signing Key. It didn't show anything for Medibuntu or anything else. Prehaps I'm missing something here?

I did a google search on the error message but couldn't find anything that helped.

I've had this problem for more than a day, so it's not a server problem. Also, I changed from the US to Main server, but this didn't help either.

Does anyone know what might be the problem? Is the missing public key the one I'm trying to download or does it refer to something else.

Thanks for the help.

---

### Post by noynac on 2008-05-27
I did a bit more searching and found a page that with a recommended command line that appears to have worked. I now have a GPG key for Medibuntu and do not receive any more error messages. 

[https://answers.launchpad.net/medibuntu/+question/22384](https://answers.launchpad.net/medibuntu/+question/22384)

---

