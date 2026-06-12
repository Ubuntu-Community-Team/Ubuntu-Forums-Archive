---
title: "Unrecoverable error when updating Lubuntu 13.03"
date: 2014-03-19
forum: General Help
---

### Post by Chris62 on 2014-03-19
Hi,

Could anyone help me with this, please?

I ran Update Manager to get the latest updates for Lubuntu 13.04 and got the following error:

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-i386_Packages, E:The package lists or status file could not be parsed or opened

When it says it is "unrecoverable", that surely does not mean that there is no solution other than a re-installation does it?
I had a look in /var/lib/apt/lists but there was no /packages.mediabuntu.org_dists_precise  etc.

Any help would be greatly appreciated

---

### Post by bapoumba on 2014-03-19
The medibuntu repositories no longer exist. You need to uncheck the repositories from software sources for ex.
You can install the ubuntu-restricted-extras package and once done install libdvdcss2 by running ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Chris62 on 2014-03-20
Many thanks bapoumba; the "unresolvable problem" has now been resolved and I have been able to do the update. It said after that, that there was also an upgrade that could be done so I did that as well but it has brought another problem. 

Although I used my WiFi to do both the update and the upgrade, after I rebooted the computer the WiFi  ceased to work. It appears to be connected in that the little icon at the top right is there and it gives the name of the network, but it will not connect to anything when I run Firefox. The WiFi card is working properly, as it works OK with another distro. I have Mint installed on my laptop and Lubuntu is on an external USB hard drive and until I did the upgrade Lubuntu ran without problems when the external drive was plugged into the laptop.

Have you any ideas as to where I should start to look to see why I can no longer connect to the internet?

---

### Post by bapoumba on 2014-03-20
For the wifi problem, you should post a new thread in Networking and Wireless : [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
Detail your network connexion as much as you can. It could also be a good idea to run the wireless script and post the output : [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

---

### Post by Bashing-om on 2014-03-20
Chris62; Hey, 

In addition, Lubuntu 13.04 is no longer supported, It is past it End Of Life !
[https://www.facebook.com/Lubuntu.Official.Page/posts/10152238662641694?stream_ref=10](https://www.facebook.com/Lubuntu.Official.Page/posts/10152238662641694?stream_ref=10)

Highly recommended to upgrade to a supported version, then see what the situation is.

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

### Post by Chris62 on 2014-03-21
Thanks again, bapoumba.

I just thought you might be interested to know that I have sorted out the WiFi problem. I realised eventually that Lubuntu had two kernels installed and after I removed the earlier one the WiFi worked without my doing anything else,so I did not need to start another thread.

Bashing-om. I did not realise that Lubuntu 13.04 was no longer supported. When the Update Manager said that there was a new release, I assumed that it was the latest. It just shows; one can look at a screen and not "see" it sometimes. Thanks anyway

---

### Post by bapoumba on 2014-03-21
Good to see you got it solved :)
Please mark your thread as such, thanks : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

