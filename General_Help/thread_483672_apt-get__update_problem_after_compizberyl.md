---
title: "apt-get / update problem after compiz/beryl"
date: 2007-06-25
forum: General Help
---

### Post by Salazar420 on 2007-06-25
I've recently been messing around with compiz and beryl. That, in turn, had me messing with various aspects of video drivers, etc. Well now I'm having problems with my updater and apt-get as well. My system updater has an error message that states: ' Error: BrokenCount > 0'

Here are the results of my attempts at a 'sudo apt-get update' and 'sudo aptitude update':
> 
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

And here is 'sudo aptitude update':

> Fetched 10.7kB in 1s (6393B/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

I also just realized that my terminal is no longer scrolling correctly. I truly hope that I won't be forced to reinstall yet again. Any help is much appreciated. Thanks.

---

### Post by FuturePilot on 2007-06-25
I'm not sure about the BrokenCount > 0 error but the other ones just mean that you are missing the gpg key for those third party repos you added. You'll have to go back and retrace the instructions you followed to install Beryl to see if there was any mention of adding a gpg key for those repos. Or sometimes you can browse the repo through you browser and there will be instructions on there for adding the keys.

---

### Post by Salazar420 on 2007-06-25
Oh yes, the repositories. I remember now. I could've swore to have added the key thing but oh well. I'll retrace my steps and remove the third party repositories -- see how that works out. Thanks for the enlightenment!

---

