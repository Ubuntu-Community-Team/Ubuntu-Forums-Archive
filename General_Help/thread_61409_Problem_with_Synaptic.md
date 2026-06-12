---
title: "Problem with Synaptic"
date: 2005-08-31
forum: General Help
---

### Post by gez on 2005-08-31
I've just started getting this problem with the Synaptic package manager:

When I start it up I get the message:
"W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)"

I get a very similar message if I try apt-get etc. in a terminal too.

Any ideas?       ](*,) 

G.

---

### Post by Juergen on 2005-08-31
I had this after a problem connecting to the server.
I just did a second reload, or 'apt-get update' (with working connection) and this message went away.

Or did you already try that?

---

### Post by gez on 2005-08-31
Yeah this problems been going on for a few days now, and doing "apt-get update" returns exactly the same error message.

---

### Post by WirelessMike on 2005-08-31
Can you show us a cut-and-paste of your apt sources list?

You can get it by typing into command line:
> sudo nano /etc/apt/sources.list
(of course, you may have already known that)

---

### Post by Juergen on 2005-08-31
What if you remove this repository, do an update, add the repository and then update again?

Or try to find a mirror and use that.
Updates on mirrors might be some hours late, but you will probably have less load on them than on the 'original' Ubuntu ones (and you'll help to reduce the load for the Ubuntu servers...)

The full package list should in both cases (IMHO) be loaded anew.

---

### Post by WirelessMike on 2005-08-31
Your security repository should look something like this:
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
I like to seperate main/restricted entries from universe/multiverse, but I'm probably just being obsessive-compulsive.

If you can edit these lines with nano, the changes will be reflected in Synaptic as soon as you refresh the repositories list.

Just get to the list as stated earlier:
> sudo nano /etc/apt/sources.list
Overwrite your security.ubuntu lines with the ones above, then (CTRL)+(o) then (ENTER) and (CTRL)+(x).  Then refresh the repositories in Synaptic and you shouldn't get that error again (we hope).

---

### Post by gez on 2005-08-31
ok, want sure which bits are relevant so here is my sources.list in its entirity

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by WirelessMike on 2005-08-31
Well that blows my theory out of the water.  Your sources list looks fine, though I'd uncomment the lines for security universe.

Still...  You showed me yours, so I'll show you mine.  Don't know if changing some of yours to look like these will help or not.  If it doesn't, you can always change it back again.

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse

## Uncomment the following to enable hoary backports.
deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras main restricted universe multiverse

## Uncomment the following to install sunjava
deb [http://ubuntu.tower-net.de/ubuntu](http://ubuntu.tower-net.de/ubuntu) warty java
deb [http://ubuntu.tower-net.de/ubuntu](http://ubuntu.tower-net.de/ubuntu) hoary java
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty multiverse
If you change your sources list, remember that it will give you the same error warnings when you first open synaptic, but click "reload" and all should be well.

---

### Post by gez on 2005-08-31
hmm, curious; the problem seems to have stopped, I looked through the Repositories dialog in Synaptic and when I was done it said there were changes and then it was ok: But I didn't change anything and I checked sources.list against sources.list.save and they are identical.

Nevermind, I'm not complaining, thanks for the advice!

G.

---

### Post by WirelessMike on 2005-08-31
How odd...  Oh well.  All's well that ends well, no?

---

