---
title: "Can't install acroread even with multiverse enabled"
date: 2006-11-16
forum: General Help
---

### Post by beastly on 2006-11-16
Hi all,

I am trying to install Acrobat Reader onto my Edgy system (x86-64 version). I have edited the apt sources.list file to include multiverse yet it can't find the package. I tried searching for acroread using dpkg-query -l and synaptic to no avail. Why doesn't this package appear in the repositories even though there are plenty of posts saying it should be in multiverse?

BTW I have run apt-get update after changing the sources.list file.

```
~>sudo apt-get install acroread
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package acroread
```


Here is my sources.lst file:

```
~>cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted
 
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted
 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe
 
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
 
deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse
 
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
 
deb http://archive.canonical.com/ubuntu edgy-commercial main
 
#deb http://packages.freecontrib.org/plf/ edgy free non-free
#deb-src http://packages.freecontrib.org/plf/ edgy free non-free

```

Any thoughts? Would I be better off just directly installing a .deb instead?

Thanks.

---

### Post by taurus on 2006-11-16
Why don't you install automatix2 and use it to install acrobat reader then!!!

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by darrenm on 2006-11-16
Have you done an apt-get update since?

---

### Post by beastly on 2006-11-16
> **taurus said:**
> Why don't you install automatix2 and use it to install acrobat reader then!!!

[http://www.getautomatix.com](http://www.getautomatix.com)

I used Automatix to install a load of stuff, but it hasn't installed acroread even though I selected it, presumably because it simply scripts a call to "apt-get install acroread"!

Yes I have run apt-get update after every change to sources.list. I even tried removing all the entries from sources.list, running apt-get update, then replacing the original sources file and re-running apt-get update to try and flush out any issues, but it has made no difference.

Is everyone else still able to access acroread from the repos? Anyone on an amd64 system (not sure if it makes any difference)?

Cheers.

---

### Post by taurus on 2006-11-16
I didn't have any problem installing acroread using automatix2!  When you install automatix2 on your machine, it will add more repos to your /etc/apt/sources.list so look in there to see if that's the case...

---

### Post by beastly on 2006-11-16
It did add the repos, see my sources.list above - multiverse is definitely there.

I just had a browse directly through the repo, compare:

[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)

with:

[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages.gz)

The latter has no acroread package, whereas the former does. This would explain the problem - assuming my amd64 install only looks in the amd64 branch of the repo, then apt is correct in reporting that it can't find the package, because it doesn't exist!

I'm suprised it hasn't been ported to the 64 bit repo yet, and even more surprised that no-one else seems to have noticed!

---

### Post by beastly on 2006-11-16
A little digging and it's starting to make sense now. There is no 64 bit compatible build of acroread available by the looks of it. It is possible to make it work with a bit of effort, I'll give it a shot later.

For anyone else interested, I've found this web page to be quite informative:
[http://wiki.debian.org/DebianAMD64Faq](http://wiki.debian.org/DebianAMD64Faq)

---

### Post by carl.alv on 2007-03-28
I have exactly the same problem beastly, did you manage to install acroread???

---

### Post by Vermind on 2007-03-30
Hello,
If You are still reading this, 
These steps made acroread work for me:
1. download the latest acroread from an Ubuntu i386 repository (this is for dapper) [acroread i386 package]("http://security.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.06_i386")
2. install it, overriding default arch
[FONT="Courier New"]sudo dpkg -i --force-architecture acroread*.deb[/FONT]
3. edit the startup script, adding the stuff in the debian howto mentioned earlier in this thread:
[FONT="Courier New"]sudo gedit /usr/bin/acroread[/FONT]
look for this line (line 756 in my version):
[FONT="Courier New"]exec "$ACRO_EXEC_CMD" ${1+"$@"}[/FONT]
replace it with:
[FONT="Courier New"]GCONV_PATH=/usr/lib32/gconv LD_PRELOAD=/usr/lib32/libpangohack.so.0.0 GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders32 exec "$ACRO_EXEC_CMD" ${1+"$@"}[/FONT]
[edited, added this step]
Actually, acroread works now, but it doesn't open any files with figures... So I had to do the last step from the debian page too:
4. [FONT="Courier New"]sed 's:/usr/lib/:/usr/lib32/:' < /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders32[/FONT]
5. Try running acroread.

---

