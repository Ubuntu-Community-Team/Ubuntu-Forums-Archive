---
title: "NIS user login problem with gdm (gutsy)"
date: 2007-10-16
forum: General Help
---

### Post by garymansell on 2007-10-16
Hi,

I am having trouble configuring my gutsy install to allow nis user logins.

I can su to a NIS user OK and can ssh to the local machine as a NIS user OK but I cannot seem to login via gdm as a NIS user.

My NIS user's uid is 6912 so should not be a problem as it is over 1000

my nsswitch.conf looks like this:

passwd:         files nis
group:          files nis
shadow:         files nis

hosts:          files nis dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

automount:      nis


Any Ideas???

Regards

---

### Post by jimbudler on 2007-10-16
gdm starts earlier than NIS and autofs. After rebooting there are no NIS users available.

I usually wait for GDM to come up, listing local users, and then ctrl-alt-backspace to restart the Xserver and GDM.

NIS logins are then available. 

jim

---

### Post by garymansell on 2007-10-17
This makes no difference for me.

I can login as a local user and check that NIS is working OK by su'ing to the NIS user or ssh'ing to the local user, then I logout and try and login as the NIS user via GDM and still no joy....

Here are the entries in /var/log/auth.log

Oct 17 11:52:51 grma-lap gdm[19392]: pam_unix(gdm:auth): check pass; user unknown
Oct 17 11:52:51 grma-lap gdm[19392]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct 17 11:52:51 grma-lap gdm[19392]: gkr-pam: error looking up user information for: grma

Anyone able to help????

Rgds

Gary

---

### Post by benhall on 2007-10-19
I think this is a gutsy bug- I've just updated two autofs/nis machines from feisty and I'm experiencing the same problem. I can ssh in, but I cannot get access to nfs mounted home directories immediately after reboot. Restarting autofs fixes both issues- I'll submit a bug report.

---

### Post by chem on 2007-10-19
I have the exact same problem as the original poster (down to the /var/log notes), and unless I can find a solution soon, this is crippling enough to go back to Fedora.

---

### Post by benhall on 2007-10-24
As I mentioned, you can restart or reload autofs on each client to rectify the issue after boot. You could do this manually, or you could move the autofs to start later in the boot process.

Looking at some of the present bugs in NIS, it's not clear to me whether the bug has been reported or not. I have added a note to one about autofs, but I'm going to have to look into it more. I think that bug 26717 is most relevant

[https://bugs.launchpad.net/ubuntu/+source/nis/+bug/26717](https://bugs.launchpad.net/ubuntu/+source/nis/+bug/26717)

Edit:

To confirm that the autofs reload fixes the same problem as others are describing, I get the same errors in /var/log/auth.log as described above by garymansell

---

### Post by benhall on 2007-10-24
Could anyone confirm if this issue is specific to upgrades, or if freshly installed machines are affected?

---

### Post by maethor on 2007-10-25
*To confirm that the autofs reload fixes the same problem as others are describing, I get the same errors in /var/log/auth.log as described above by garymansell*

I've got the exact same problem on 2 machines upgraded to gutsy from feisty.

---

### Post by benhall on 2007-10-25
OK, I think I have a workaround. I think that the bug has already been reported, and is not the one I indicated above, but rather

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/152794](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/152794)

My workaround has been to disable wired roaming in network manager, and manually set it to DHCP. This fix probably applies to most NIS setups, but any other workarounds would be welcome!

---

