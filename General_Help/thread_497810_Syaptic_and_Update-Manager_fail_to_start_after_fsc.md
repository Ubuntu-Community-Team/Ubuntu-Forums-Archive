---
title: "Syaptic and Update-Manager fail to start after fsck"
date: 2007-07-10
forum: General Help
---

### Post by toagu on 2007-07-10
I had an abnormal shutdown and next time I booted Ubuntu (Fiesty Fawn 7.04) it asked me to do a manual fsck. It threw a bunch of errors to which the only unintelligent answer I could give was "y" (yes)  :(

Im guessing that as a result there are obviously files messed up, which is what is causing the syaptic / update-manager error. The exact error is:

[I]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/I]

Everything else seems to be running fine for the moment ! Perhaps because I had a separate /home partition that was not effected ......

Is there any way to recover from this or is the only safe option to reinstall Fiesty Fawn back from the CD ? 

In case its only the later, is there any precaution I can / need to take ? Is there any way in which I can avoid re-downloading updates and other installed packages or at least get a list of installed package that I can work off after reinstallation ? (Of course - Id rather fix than reinstall if there is a way.... )

TIA

---

### Post by StefanoCole on 2007-07-11
Well, in the directory /var/cache/apt/archives/ you should find the packages you downloaded for installation.

Stefano

---

### Post by tcpip4lyfe on 2007-07-11
Just a thought. If you can get a terminal, check your /etc/apt/sources.list for duplicate sources.  If you can't, boot to the liveCD and mount you HD and check it that way.

This guy was having the same error.  

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/121189](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/121189)

Good luck bro.

---

### Post by toagu on 2007-07-11
Stefano / tcpip4lyfe,
Thanks for your replies....

The systems seems to be working fine other than apt / synaptic / update-manager. So I was able to check sources.list -- there are no duplicates in there -- just the standard ones (restricted, universe, multiverse) plus ones added by Automatix. I even tried 'apt-get clean' - even that fails with the same error :(

I guess I should go down the reinstall route only. But just curious - if it again messes up and insists on a manual fsck - is there something else I can do other than blindly reply "y"es ?
Or maybe some disk maintenance that I can do / need to be careful about so that I can avoid getting into the fsck situation in the first place ? 
(BTW, its an ext3 partition - I forgot to mention earlier)

Thanks again....

---

