---
title: "ppa issues"
date: 2015-04-12
forum: General Help
---

### Post by ubunt72 on 2015-04-12
I use Ubuntu GNOME.   I just ran sudo apt-get update and I got some errors.   But, I'm not sure how to fix them.   I have run into ppa problems in the past.  But, I just left it alone.  But, I'd like to know what's wrong and how I can fix it.   There's 'how-tos' out there to set up the ppas I used - that's why they are there.   But, for some reason, it is not working.   

Here's the problem areas:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages               
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages
  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tsvetko.tsvetkov/trusty-backports/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/tsvetko.tsvetkov/trusty-backports/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tsvetko.tsvetkov/trusty-backports/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/tsvetko.tsvetkov/trusty-backports/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

I wanted to use the mint program, 'mintstick' instead of Startup USB Creator or Unetbootin - I had a OS/partition of LMDE for a while and the mint usb creator program was way more reliable - although, it doesn't use persistence.  But, I never had a problem with it.   The only steps to install it in Ubuntu seems to be adding the ppa from 'trusty-backports' as shown above.   Obviously, it didn't work for me.  

Anything I can do to remedy the situation other than not using it? :)   Thanks in advance.  

Why is the other ppa packages not found?    I'd like to fix that at least.

---

### Post by dragonfly41 on 2015-04-12
Y PPA Manager might help .. recently I had similar error messages and Y PPA Manager cleaned up PPA (I think I had some missing keys).

If you can't install Y PPA Manager by terminal here is a thread giving the deb download link.

[http://askubuntu.com/questions/556451/cant-install-y-ppa-manager-via-terminal](http://askubuntu.com/questions/556451/cant-install-y-ppa-manager-via-terminal)

---

### Post by mc4man on 2015-04-12
When you use apt (add-apt-repository) to add a ppa it uses the distribution you are on for the source entry(s). If the ppa doesn't have packages for that distribution then you get the 404 error

So you can - 
1. open Software & Updates > Other Software. Click on the ppa in question entry(s) > edit & change the Distribution entry from utopic to trusty (ck. twice to make sure it changed.
Then reload sources & see if the trusty package of what you want will install & if it does, does it work.

2. open Software & Updates > Other Software. Remove the ppa's entries., reload sources.
3. get the source to your app, rebuild for 14.10

Keep in mind that 14.10 is just about End Of Life so unless you want to stick with a dead release you'll be moving on the the next short lived release (15.04) or go back to 14.04 anyway...

---

