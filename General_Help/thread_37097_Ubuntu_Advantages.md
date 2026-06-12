---
title: "Ubuntu Advantages"
date: 2005-05-25
forum: General Help
---

### Post by biguns on 2005-05-25
I am switching from Gentoo to Ubuntu. *I can’t believe they actually sent me the disk for free… *

I know there are many differences/advantages between the many different Linux Distros, I just wanted to know what kinds of differences I can expect with Ubuntu. 

Of particular interest is the “**sudo**” command. As I troll the forums, I see this everywhere. I assume this is based on an Ubuntu philosophy. Can anyone point me in the right direction?

---

### Post by sapo on 2005-05-25
a gentoo user said it yesterday to me:

"I m starting to like ubuntu, it just works, dont ask anything, my sound and everything is working without editing any configs.. i hope ubuntu could someday replace windows, cause it is in the right path...."

 :wink: 

You will notice that ubuntu is very simple to use.. and if you dont make mistakes everythiung will work perfectly (you will make mistakes for sure as a new user.. so dont mind)

But what i like in ubuntu is its "simplicity" everything here works and thats all i need... to hell with a lot of complicated stuff to make simple things  :grin:

---

### Post by SamH on 2005-05-25
One of my favorite things is the apt package management.  I've used Gentoo and found lots I liked.  The Portage package management was pretty nice.  However, apt is IMHO absolutely the best Linux package manager devised so far.

It works easily from the command line, or you can use Synaptic, the GUI frontend for it.  Either way it is EASY!  No dependency hell.   \\:D/

---

### Post by biguns on 2005-05-25
Why does Ubuntu use sudo so much? I have user Redhat, Mandrake and Gentoo and it is not used so much there.

---

### Post by soce_32 on 2005-05-25
sudo allows the root account to be disabled.  Any time sudo is called, the the actions are logged.  This creates accountability, and *generally* prevents users from operating as the system administrator unnecessarily.  Users with sufficient permissions in the sudoers file can `sudo su` and get a root terminal going, but this shouldn't be needed very often.  The sudoers file sets up which users can use which commands, so admin privileges can be assigned as needed if that's what your environment calls for.  

For an install and go distro, it is a very good thing to have the root account disabled to prevent people from logging in or doing general tasks as root.

---

### Post by biguns on 2005-05-25
I knew there had to be a reason...and I knew it was going to be a good one.

Thanks

---

