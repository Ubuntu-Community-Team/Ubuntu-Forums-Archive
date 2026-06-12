---
title: "Software removal and password"
date: 2016-06-30
forum: General Help
---

### Post by bogjumper on 2016-06-30
Good Day

I am not very conversant with Ubuntu  other than to say I have used it on and off since about edition 10. Lately I have used it quite a lot running it in tandem on pc and laptop but GUI.
Anyway yesterday I decided to clear out some apps that I felt I did not need and I had just had a low disk space warning. I found that it was extremely difficult to get rid of some which just refused to budge no matter how many times I removed. I then decided togo to systems and in User change my password which I did. Today I wanted to install a program and the system rejected both my new and old password. Any suggestions other than throw it out the window. Thanks

---

### Post by TheFu on 2016-06-30
I'm going to assume you forgot the new password. If that isn't really what happened, we need lots more data.

If you have physical access to the machine and it isn't whole-drive encrypted, using a liveCD to change any password isn't that hard. Lots of how-tos out there.  The summary of steps is:
* boot from a liveCD that is the same as the installed OS (mainly 32-bit/64-bit and release); don't get hung up on the DE. Doesn't matter.
* setup a chroot for the data on the HDD. You'll be using all the already installed programs; and since you'll be running as root ... any userid can be modified
* change the password for your userid.
* back out of the chroot
* reboot and let the HDD OS boot (not the liveCD).

Login - be happy.

Of course, if you have to type the password to login every time, forgetting the password would be much less likely.
[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/) has a guide.

There are other ways to do this too: [http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

Don't know how well these works on a systemd box. Ought to work, but ... idunno.

---

### Post by bogjumper on 2016-06-30
Hello The Fu
My apologies as I sent that early morning and did not complete properly. So some more info that I hope will help. I do not have a password to sign in. The password I changed was the authentication password to something more easily remembered and the same on both pcs. I should have added that on this laptop I am using Ub 16.04
64 bit and keep up daily with updates. So logging in and using is not a problem but making any changes is as the authenication will not accept either of my passwords or just hit enter. I did think of reinstalling but (a) was worried about losing items thereon and (b) reinstalling all the software.So I thought better ask in case there was a simpler way to resolve. Hope this gives a clearer picture.

Thank you for your reply

Thank you for your help.

---

### Post by Impavidus on 2016-06-30
You rarely run out of disk space because of installing too many applications. The disk space used by most applications is tiny compared to the size of a modern hard drive. Removing software using Ubuntu software or any other interface to the package manager should completely remove the software (you may have to autoremove some additional packages). It is possible that some references to the removed software, like menu entries, remain. If so, you can clear them manually.

I have to ask you, what do you mean exactly by "rejected the password"? Does it say the password is incorrect or does it simply prompt for the password again or give some other error message? In the latter cases, the password is correct, but something else doesn't work.

Here is a more recent tutorial on changing your password, if you lost it: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by bogjumper on 2016-06-30
Thank you Impavidus for your reply and pse see mine. I am dual installed with Win 10 and I gave  20 gigs  and 3 swap. Actually the OS advised yesterday that my 
portion only had 600mbs left and advised some clearance. I am busy at the moment with some photograpic work for an old comrades site and consequently have a lot downloaded. All I can say is that some packages removed for 10-15 seconds and then reappeared again as installed.

Regards

---

### Post by TheFu on 2016-06-30
You need to get the login password back first. Can't do anything else before that is solved. Follow those links and fix that first.

---

### Post by bogjumper on 2016-06-30
Sorry did not find any link.

---

### Post by grahammechanical on 2016-06-30
For those viewing this thread and becoming concerned about what to do if they get in this situation there are is something that can safely be done.

At the Grub boot menu select Advanced options for Ubuntu and then select a kernel with recovery mode. At the recovery menu select clean - try to make free space. That option will run 2 commands - clean & autoremove. On Ubuntu 16.04 the autoremove command will remove all old kernels leaving just the latest 2 kernels in place.

We can also run either of those commands from a terminal. We use either apt-get <command> if we are not on 16.04 or apt <command> if we are on 16.04.

Regards

---

### Post by HermanAB on 2016-06-30
Uninstalling stuff, is a bit like trying to unscramble an egg...

In my experience, it is best to reinstall the whole machine from scratch once a year and never uninstall anything if you can help it.

---

### Post by bogjumper on 2016-07-01
All contributors 
 I tried the Grub recovery with no success Im afraid.Thank you all for your help and Its not causing me any problems just now so I will leave it there. When I upload my photographic stuff I will try The Fus suggestion. If that does not do the trick I will download the latest and reinstall.
Again my thanks

Bogjumper

---

