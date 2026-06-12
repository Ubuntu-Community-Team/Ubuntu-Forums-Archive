---
title: "Emergency! Must downgrade OOo Impress.... Help!"
date: 2007-05-30
forum: General Help
---

### Post by GSF1200S on 2007-05-30
I wouldnt normally be so urgent, but Im really pushing it on time. I have a presentation tomorrow, and im using Openoffice impress. Everything would be fine, but I cant change the template/background on a slide without OOo impress crashing. This happens 100% of the time.

I cant download the packages from OOo website as the linux versions are RPM packages (dont have time to mess with alien right now), and for the life of me I cant figure out how to get an older version of OOo installed. I really should of done this presentation sooner, but I never really expected a crashing problem- Ive spent the last 2 1/2 hours trying to find ANY solution.

If you either know how to make this crashing go away or a way to downgrade to an older version, your help would be greatly appreciated. Im going to continue writing my presentation with identical slides until someone has a solution...

Thanks in advance...

---

### Post by geira on 2007-05-30
Instead of downgrading, how about setting up a minimal virtual SuSE/Red Hat machine to install OOo on?

---

### Post by GSF1200S on 2007-05-30
> **geira said:**
> Instead of downgrading, how about setting up a minimal virtual SuSE/Red Hat machine to install OOo on? 

Considering my DVD drive is broken and wont burn anything, getting the install done would be hard. I have VirtualBox, but I would have to mount the distro's .ISO file as a disc drive and run that to install the OS. As far as I know, theres no 'Daemon Tools' for Linux. I know you can mount .ISO's with the CLI, but I dont know if VirtualBox will recognize it as a disc drive.

Thanks very much for the idea, but unfortunately I dont have the time (right now; presentation in hours) for a distro download/install/mount/ and then install OOo after finding an older version, etc...

I will be doing this soon in my free time. Its time like this when I realize the importance of other options...

---

### Post by yota on 2007-05-30
Hi,

if you wanto to downgrade you can download and install the previous version from this url:

[http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.0.4-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.0.4-0ubuntu3_i386.deb)

the same folder contains other components and versions as well.
But if you are in a hurry maybe it's better not to mess up with something that is not guaranted to work (edgy's software on feisty); probably the best solution is a livecd with oo2 preinstalled (such as edgy live or knoppix) with virtualbox that can directly handle an iso image as a virtual cdrom drive.

Hope this helps!

---

### Post by FuturePilot on 2007-05-30
Impress seems to be awfully buggy in Feisty. There's a bunch of bug reports on Launchpad.
You could either download the RPMs from the OO.org website and use Alien to install them. There's a few How To's around here about that. Or someone else said that the latest OO.org Debian builds work fine.

---

