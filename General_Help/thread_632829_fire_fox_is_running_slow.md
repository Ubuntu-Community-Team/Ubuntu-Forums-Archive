---
title: "fire fox is running slow"
date: 2007-12-05
forum: General Help
---

### Post by szwety on 2007-12-05
i'm semi new to ubuntu linux, but have used a couple other distros.  something i've run into on this distro of linux (ubuntu 7.10) is that firefox runs extremely slow, especially when it comes to flash sites...  i might have installed flash wrong, could that be an issue?

i tried uninstalling and reinstalling fire fox but that didn't help as it didn't uninstall the plugins..  any help with this problem?  or is that just how it has to be when you use ubuntu..

i'm running a dell d800 1.7ghz intel inside pentium m with 512mb of ram,  i never had this problem using *cough*windows*cough*

---

### Post by LaRoza on 2007-12-05
It may be your specs. Firefox is known for being slow, especially over time. I use Opera, and do not have this problem. [http://www.opera.com/](http://www.opera.com/)

---

### Post by -grubby on 2007-12-05
> **LaRoza said:**
> It may be your specs. Firefox is known for being slow, especially over time. I use Opera, and do not have this problem. [http://www.opera.com/](http://www.opera.com/)

Firefox ran fine on my 500MHZ 256MB RAM machine. Poppycock. It seems that the build from the mozilla site is faster....but you have to compile it
EDIT: maybe this will help, but you can type about:config in the address bar and search for "ipv6" and double click on "network.dns.disableIpV6"

---

### Post by rfruth on 2007-12-05
Tried a different profile [http://kb.mozillazine.org/Profile_folder_-_Firefox]("http://kb.mozillazine.org/Profile_folder_-_Firefox")

---

### Post by szwety on 2007-12-05
yeah... i agree with the whole poppycock bit...  they don't have a deb package from the site??  also i've looked around and found that people were having problems with slow flash in firefox, but they were using older versions of ubuntu... i haven't really read anything about problems with this version...

---

### Post by -grubby on 2007-12-05
> **szwety said:**
> yeah... i agree with the whole poppycock bit...  they don't have a deb package from the site??

yep, no .deb, let me search a bit more to see

---

### Post by szwety on 2007-12-05
> **LaRoza said:**
> It may be your specs. Firefox is known for being slow, especially over time. I use Opera, and do not have this problem. [http://www.opera.com/](http://www.opera.com/)

the only issue i have with opera is that i can't seem to get flash installed... i downloaded the flash tarball from the site, but it wanted to install it into usr/lib/mozilla... and then i tried to install it as root, and it gave me the option to install it into a different directory but said that the directory wasn't real...

---

### Post by szwety on 2007-12-06
strangely enough,  it only seems to be freeznig when i try to view a myspace profile... weird...

---

### Post by LaRoza on 2007-12-06
> **szwety said:**
> the only issue i have with opera is that i can't seem to get flash installed... i downloaded the flash tarball from the site, but it wanted to install it into usr/lib/mozilla... and then i tried to install it as root, and it gave me the option to install it into a different directory but said that the directory wasn't real...

Odd. I have had no problems with Flash, I used "sudo aptitude install flashplugin-nonfree" and have no problems with flash in Opera.

---

### Post by LaRoza on 2007-12-06
[QUOTE=nathangrubb;3900225]Firefox ran fine on my 500MHZ 256MB RAM machine. Poppycock. It seems that the build from the mozilla site is faster....but you have to compile it
/QUOTE]

I am not saying Firefox doesn't work, just that Firefox running slow is nothing new. "Running fine" is relative to what one is used to. Firefox on my computer (on either OS) is slow to me, because I am used to a faster speed.

"Poppycock" is hardly a constructive word to use in this setting.

The newest versions of Firefox may have fixed this, and I have heard good things about it.

---

### Post by szwety on 2007-12-07
so if i want to uninstall flash it'd just be "sudo aptitude remove flashplugin-nonfree"?

would that remove the plugin from firefox too?

---

### Post by szwety on 2007-12-07
actually how would i go about removing flash, and 100% of firefox? like all the plugins the extensions everything?  because i've never had this problem before, and i think it's just a problem with the way i installed flash.

---

### Post by MarilenCorciovei on 2007-12-10
I had similar problems and I found out the solution was[ to disable ipv6]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/what-was-killing-my-gutsy/")

add blacklist ipv6 to /etc/modprobe.d/blacklist

---

