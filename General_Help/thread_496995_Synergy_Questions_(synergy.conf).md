---
title: "Synergy Questions (synergy.conf)"
date: 2007-07-09
forum: General Help
---

### Post by synthsrkl on 2007-07-09
sorry if i'm being a bit stupid here, but once i create this synergy.conf file, where do i save it?

also where and how do i define these names that are in the synergy.conf file (as in the names you call your server and client....surely somewhere you must assign the name to an ip?)

also how have you set up your notepad (if you used that as the other computer) to your home network? as in does it work nicely with wireless?

---

### Post by jedi22 on 2007-08-24
Why make a conf file?  Just use the GUI "quicksynergy" from and/remove programs.  I use it works great for me.

---

### Post by apetresc on 2007-08-24
> **synthsrkl said:**
> also where and how do i define these names that are in the synergy.conf file (as in the names you call your server and client....surely somewhere you must assign the name to an ip?)
I double jedi22's suggestion of using QuickSynergy. As for your second question, the names are resolved like this:
1) Is the name the same as the hostname of a machine on the local network? If so, resolve to that.
2) If not, then the host's synergy CLIENT must set that name in their configuration file. That is how it knows.

As a guy who has three computers hooked up to synergy at once, I can tell you this is an awesome tool and I wish you lots of luck using it :)

---

### Post by jedi22 on 2007-08-25
There is a GUI interface for OS X and can be downloaded at:
[http://software.landryhetu.com/synergy/](http://software.landryhetu.com/synergy/)

---

### Post by goodtimetribe on 2007-09-26
> **AdrianP said:**
> I double jedi22's suggestion of using QuickSynergy. As for your second question, the names are resolved like this:
1) Is the name the same as the hostname of a machine on the local network? If so, resolve to that.
2) If not, then the host's synergy CLIENT must set that name in their configuration file. That is how it knows.

As a guy who has three computers hooked up to synergy at once, I can tell you this is an awesome tool and I wish you lots of luck using it :)

great... so you're going to be my expert :)

i just got 2. I've used it successfully with two windows boxes, so I *think* i've got it configured correctly. i'm not broadcasting my machine names, i forgot why... saw a solution once, got it bookmarked, yet, on the two machines configured by IP using quicksynergy on Kubuntu Feisty Fawn,  it don't work. i remember on my XP machines i had to disable it in my firewall. any chance i've gotta blow open a hole in moblock for it? if so what port?

kud0ez

Looking forward to getting this to work. The original poster never described their experience.

---

### Post by High Camp on 2007-09-26
Hi All

Sorry to butt in on the posts but I too am having problems with Synergy that I'm hoping someone can assist is solving. I've had it running on M$ but cannot get it running on Linux. I'm running Xubuntu if that makes any difference.

1. I tried quicksynergy. On the server I put in the server dialog the network name of client. In the client dialog I put the name of the server. No Luck. I changed those to their respective IP addresses and still no luck. I then switched the two, again with no luck.

2. I followed this tutorial ([http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/](http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/)) substituting Linux info for the M$ info. I got the server working but I could not get the client working becuase you have to supply the server name surrounded by <> and Terminal interprets that as a new line.

P.S. I found I had to remove quicksynergy to follow the tut because it messes with the synergy running in the terminal. 

Any help is much MUCH appreciated, thanks.

EDIT: I followed this tut as well ([https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto))

---

### Post by High Camp on 2007-09-26
Never mind, I got it working. It turns out with quicksynergy I had to specify the client name in the server dialog on the server and the server ip in the client dialog on the client (if that makes any sense).

Thanks for at least reading this,

---

### Post by goodtimetribe on 2007-09-26
Yup, that threw me at first glance too, but that's how i've got it set now. and it still doesn't work.

---

### Post by High Camp on 2007-09-26
Are you sure you've got the right local ip's?

---

### Post by goodtimetribe on 2007-09-27
I know the two IP's are the IP's for the machines x.100 and x.101, i could try swapping them. i will try and then report back.

---

