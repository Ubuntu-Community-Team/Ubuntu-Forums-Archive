---
title: "firefox quitting unexpectedly after recent Ubuntu updates!!"
date: 2005-07-22
forum: General Help
---

### Post by bpilgrim1979 on 2005-07-22
Hello, I updated firefox with the apt-get/Synaptic updates that came out a few days ago.  Now firefox crashes unexpectedly!!

I had a number of extensions installed and finally I had to delete my entire profile and start with a new profile.  Only then would Firefox even start.

Now Firefox is extremely touchy and often quits unexpectedly when I click Tools > Extensions or try to install a new update.

What is going on?!  Firefox stability is absolutely essential!!

---

### Post by manicka on 2005-07-22
[QUOTE=bpilgrim1979]Hello, I updated firefox with the apt-get/Synaptic updates that came out a few days ago.  Now firefox crashes unexpectedly!!

I had a number of extensions installed and finally I had to delete my entire profile and start with a new profile.  Only then would Firefox even start.

Now Firefox is extremely touchy and often quits unexpectedly when I click Tools > Extensions or try to install a new update.

What is going on?!  Firefox stability is absolutely essential!![/QUOTE]
 There is a problem with firefox and the recent updates and a solution is being worked on.
I'd suggest installing 1.0.6 that is available in backports-staging

---

### Post by bpilgrim1979 on 2005-07-22
[QUOTE=manicka]There is a problem with firefox and the recent updates and a solution is being worked on.
I'd suggest installing 1.0.6 that is available in backports-staging[/QUOTE]

Thanks for quick reply.

But oh man, don't mess with Firefox!  Especially since it's completely integrated into Ubuntu...

```
# apt-get -s remove mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  epiphany-browser mozilla-firefox mozilla-firefox-gnome-support
  ubuntu-desktop yelp
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Remv epiphany-browser [1.6.1-0ubuntu2]
Remv ubuntu-desktop [0.43]
Remv mozilla-firefox-gnome-support [1.0.2-0ubuntu5.4]
Remv yelp [2.9.3cvs20050222-0ubuntu4]
Remv mozilla-firefox [1.0.2-0ubuntu5.4]
```

I don't want to mess around with any backports.  Is there a way to revert to previous package with apt-get?  Or force install the old apt-get package??

---

### Post by manicka on 2005-07-22
[QUOTE=bpilgrim1979]Thanks for quick reply.

But oh man, don't mess with Firefox!  Especially since it's completely integrated into Ubuntu...

I don't want to mess around with any backports.  Is there a way to revert to previous package with apt-get?  Or force install the old apt-get package??[/QUOTE]
 Yes, choose the package in synaptic, then choose Packgage--> Force Version. If an older version is available you can choose it here and it should downgrade.

As a side note, I've never had any problems with packages from backports. They are very stable

---

### Post by bpilgrim1979 on 2005-07-22
okay, downgrading worked.

...and all is well again in ubuntu.

---

### Post by manicka on 2005-07-23
Very good, things should be fixed with Firefox fairly soon. Seeing that I can't talk you into backports, just give it another go in a few days.

---

