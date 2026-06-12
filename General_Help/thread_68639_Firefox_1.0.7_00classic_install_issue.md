---
title: "Firefox 1.0.7 00classic install issue"
date: 2005-09-23
forum: General Help
---

### Post by Rory on 2005-09-23
I just got notification from Ubuntu update notifier that a new version of Firefox is available.  It would not install it, choking on a 00classic file.  I removed the file via terminal and tried to install again.  

I continue to get this log:
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox

But, now my Firefox 1.0.6 browser won't open, so I'm stuck with nothing.

Can anyone help?

Thanks,
Rory

---

### Post by Pluk on 2005-09-23
although i would not recommend it.. but i fixed it with the following :)

cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb

using the --force-overwite is risky since you dont know for sure if the package is broken.. it might break the program. since its just a browser i didnt really care but i wouldnt use this myself on packages your whole system rely on, .. so do this at your own risk!

---

### Post by Rory on 2005-09-23
Thanks for the solution.  I'll keep it in my back pocket for now until I see if I can find a safer way.  And thanks for the "informed consent" by pointing out the risk to your solution. Appreciate it.  :)

Anyone else have a solution?   I wonder why it's doing this.  

Thank you.

Rory

---

### Post by Yoshimitsu8 on 2005-09-23
I did the update and now I can't run firefox 1.0.6 either and it gives me the same overwrite error. I tried taking off all the firefox packages in synaptic and then addeding 1.0.7 but didn't change anything. Any other solutions besides the force overwrite?

---

### Post by Yoshimitsu8 on 2005-09-23
Here is a link to the fix, thank God for people that are smart on here :)
[http://ubuntuforums.org/showthread.php?t=68530&page=2&pp=10&highlight=firefox+1.0.7](http://ubuntuforums.org/showthread.php?t=68530&page=2&pp=10&highlight=firefox+1.0.7)

---

### Post by Rory on 2005-09-23
Not impressed by the Ubuntu QA process here, given Firefox is such a broadly used package.  Disappointing, to say the least.

---

### Post by Rory on 2005-09-23
This is what I did, based on a post in another thread, which I needed to vary slightly to get back up.  Can't promise you this won't kill your bookmarks, etc, but I seem to have kept everything, no thanks to these package maintainers.

Steps:
Kill your firefox-bin process (ctrl+esc)

From terminal:
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
and, if asked
sudo apt-get -f install

I finished with:
sudo apt-get install mozilla-firefox

Do Above At Own Risk!  Hope it works for you!

And I'm back.  Serves me right.  Next time I update a browser in Ubuntu, I'll backup my bookmarks and settings first.  Grr.....

Good luck!

---

### Post by Ozitraveller on 2005-09-23
I tried that and did a reboot and now I'm getting this message. See attached.



then I tried :
From terminal:
sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
and, if asked
sudo apt-get -f install

and it said that firefox wasn't installed, so I did a re-install thru synaptic, but sudo apt-get install mozilla-firefox would have done too.

But it works now! Yeah!!!

---

### Post by Rory on 2005-09-23
Can you Remove (not Complete Remove, which will kill bookmarks, settings, etc.) 1.0.6 via Synaptic and then install 1.0.7?  

Also, see the other thread noted in this thread.  That could help and posting there if you don't get a good solution here.  Sorry it didn't work for you!  :(

---

