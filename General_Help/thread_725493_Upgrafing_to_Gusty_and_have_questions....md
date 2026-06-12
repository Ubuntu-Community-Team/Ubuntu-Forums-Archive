---
title: "Upgrafing to Gusty and have questions..."
date: 2008-03-15
forum: General Help
---

### Post by misternewbie on 2008-03-15
I am about to upgrade to Gutsy from Feisty and have some concerns. I have an ATI X1300 graphic card and effects are working fine (Compiz Fusion). If I upgrade to Gutsy will it still work? I also installed some applications and hardwares on Feisty, will i have to reinstall them or will they still be installed after I upgraded?

---

### Post by mssever on 2008-03-15
For hardware compatibility issues, download the live CD and test it. For software, assuming you installed from a .deb, the upgrade tool might ask to uninstall some specific software. Write down what it uninstalls. If you need it after the upgrade, then reinstall it. Most of what it uninstalls you won't need.

---

### Post by Bruce M. on 2008-03-15
> **misternewbie said:**
> I am about to upgrade to Gutsy from Feisty and have some concerns. I have an ATI X1300 graphic card and effects are working fine (Compiz Fusion). If I upgrade to Gutsy will it still work? I also installed some applications and hardwares on Feisty, will i have to reinstall them or will they still be installed after I upgraded?

Depends on how you are going to upgrade.

If you are thinking about using the "Upgrade Manager" - backup everything first.  It may not work. I was lucky and it worked for me twice from 6.06 to 7.04 to 7.10.  All programs where there and upgraded.

If you get the Live CD you can test it  and see it it's going to work, not doing the install right away.

If you use the Live CD or better yet, the Alt CD to do a clean install, again back up everything you want especially your /home folder. You will have to reinstall any programs that are not part if the package install doing it this way.

Any further questions just ask.
Bruce

---

### Post by misternewbie on 2008-03-15
> **Bruce M. said:**
> Depends on how you are going to upgrade.

If you are thinking about using the "Upgrade Manager" - backup everything first.  It may not work. I was lucky and it worked for me twice from 6.06 to 7.04 to 7.10.  All programs where there and upgraded.

If you get the Live CD you can test it  and see it it's going to work, not doing the install right away.

If you use the Live CD or better yet, the Alt CD to do a clean install, again back up everything you want especially your /home folder. You will have to reinstall any programs that are not part if the package install doing it this way.

Any further questions just ask.
Bruce

I am going to do it by "upgrade". My concern is my drivers, etc. I want effects on my computer, therefore i want to keep my graphic cards settings and XGL. Will it all be gone? Or will the stay?

---

### Post by NightwishFan on 2008-03-15
I believe everything stays. I have upgraded from Gutsy to Hardy without issue more than once.

---

### Post by misternewbie on 2008-03-15
I just tried it and it said that it will remove some applications (compiz, awn, etc) =/.

---

### Post by davarino on 2008-03-15
A silly question for me to ask you...

Why update to Gus the Gibbon when Howard the Heron is coming out in a month?

Upgrading *usually* goes well, but my personal experience has been that problems do occur much more than people imagine. (Check some of the "dissatisfaction polls" in the forums to see what I mean.)

I would suggest that you sit tight unitl Heron is proved to be worth "upgrading" to... which is probably going to be a couple of weeks after it is released. (Don't ever install a new release until you see that others have had almost unanimous success.)

In the meantime, why not just install tarballs for whatever software you feel that you are really lacking? It's easy, and it is much less likely to break your system.

---

### Post by misternewbie on 2008-03-15
> **davarino said:**
> A silly question for me to ask you...

Why update to Gus the Gibbon when Howard the Heron is coming out in a month?

Upgrading *usually* goes well, but my personal experience has been that problems do occur much more than people imagine. (Check some of the "dissatisfaction polls" in the forums to see what I mean.)

I would suggest that you sit tight unitl Heron is proved to be worth "upgrading" to... which is probably going to be a couple of weeks after it is released. (Don't ever install a new release until you see that others have had almost unanimous success.)

In the meantime, why not just install tarballs for whatever software you feel that you are really lacking? It's easy, and it is much less likely to break your system.

Oh I see, i guess I'll wait until Heron comes out, but my question with upgrading is that will remove my GLX and compiz fusion or awn?

---

### Post by mssever on 2008-03-15
> **davarino said:**
> A silly question for me to ask you...

Why update to Gus the Gibbon when Howard the Heron is coming out in a month?

Upgrading *usually* goes well, but my personal experience has been that problems do occur much more than people imagine. (Check some of the "dissatisfaction polls" in the forums to see what I mean.)

I would suggest that you sit tight unitl Heron is proved to be worth "upgrading" to... which is probably going to be a couple of weeks after it is released. (Don't ever install a new release until you see that others have had almost unanimous success.)

In the meantime, why not just install tarballs for whatever software you feel that you are really lacking? It's easy, and it is much less likely to break your system.

The reason it's removing Compiz, is probably because Gutsy involves a switch to Compiz Fusion.

As far as upgrading goes, you won't be able to upgrade to Hardy unless you're running Gutsy. So I don't think that the advice to wait for Hardy is valid. Upgrading can be problematic at times, but I've upgraded my desktop from Dapper => Edgy => Feisty => Gutsy. My laptop has followed nearly the same path, but I had problems during the Feisty upgrade that forced a reinstall. Those problems weren't due to the upgrade per se, but to other deep problems I had with my machine.

Also, I don't advise installing tarballs if you can help it. When you move away from the package manager, you can easily end up with maintainability problems; that's why package managers were created in the first place.

---

### Post by mssever on 2008-03-15
> **misternewbie said:**
> will remove my GLX and compiz fusion or awn?
Maybe, and maybe not. But your configuration will be preserved, so all you have to do is reinstall.

---

### Post by misternewbie on 2008-03-15
> **mssever said:**
> Maybe, and maybe not. But your configuration will be preserved, so all you have to do is reinstall.

I guess I will just have to keep tracked of the softwares which have been removed, allowing me to install it after the upgrade. I think I will wait for Heron's release before upgrading. Thanks.

---

### Post by Bruce M. on 2008-03-16
> **misternewbie said:**
> I guess I will just have to keep tracked of the softwares which have been removed, allowing me to install it after the upgrade. I think I will wait for Heron's release before upgrading. Thanks.

OK, then you will **_*NOT*_** be able to use the *Upgrade Manager*

My personal advice is:

[LIST=1]
[*]Backup your important files ... if you have two HD's put them on the second drive. Check out QuickStart in my signature, it makes the backups a snap.
[*] Create a [seperate partition for **/home**]("http://www.psychocats.net/ubuntu/separatehome")
[*] Backup again after creating the separate /home partition
[*] Get an **ALT CD** for Gutsy be it: Ubuntu (GNOME), Xubuntu (Xfce), Kubuntu (KDE).
[*] Do a clean install, selecting the same partition information you had when you created a seperate /home partition.
[/LIST]

My system as an example:

[LIST=1]
[*]First HD:
[LIST]
[*]W2K: sda1 - not relevant here
[*]Ubuntu: sda2 - extended partition for Ubuntu - 65 G partitioned as:
[/LIST]
[LIST=a]
[*]Root:  sda5 - Mount Point: [SIZE="3"]**/**[/SIZE] - 20G
[*]home: sda7 - Mount Point: [SIZE="3"]**/home**[/SIZE] - 40G
[*]swap: sda6 - swap - 1G
[/LIST]
[*]Second HD:
[LIST]
[*]sdb1 - formatted - ext3 for Ubuntu's use only (all my personal important files)
[/LIST]
[/LIST]

Hope this helps.
Bruce

---

### Post by misternewbie on 2008-03-16
> **Bruce M. said:**
> OK, then you will **_*NOT*_** be able to use the *Upgrade Manager*

My personal advice is:

[LIST=1]
[*]Backup your important files ... if you have two HD's put them on the second drive. Check out QuickStart in my signature, it makes the backups a snap.
[*] Create a [seperate partition for **/home**]("http://www.psychocats.net/ubuntu/separatehome")
[*] Backup again after creating the separate /home partition
[*] Get an **ALT CD** for Gutsy be it: Ubuntu (GNOME), Xubuntu (Xfce), Kubuntu (KDE).
[*] Do a clean install, selecting the same partition information you had when you created a seperate /home partition.
[/LIST]

My system as an example:

[LIST=1]
[*]First HD:
[LIST]
[*]W2K: sda1 - not relevant here
[*]Ubuntu: sda2 - extended partition for Ubuntu - 65 G partitioned as:
[/LIST]
[LIST=a]
[*]Root:  sda5 - Mount Point: [SIZE="3"]**/**[/SIZE] - 20G
[*]home: sda7 - Mount Point: [SIZE="3"]**/home**[/SIZE] - 40G
[*]swap: sda6 - swap - 1G
[/LIST]
[*]Second HD:
[LIST]
[*]sdb1 - formatted - ext3 for Ubuntu's use only (all my personal important files)
[/LIST]
[/LIST]

Hope this helps.
Bruce

Why won't I be able to use the update manager?

---

### Post by Bruce M. on 2008-03-16
> **misternewbie said:**
> Why won't I be able to use the update manager?

To use the update manager you MUST follow the chain so to speak:

Dapper > Edgy > Feisty > Gutsy > Hardy

You'd have to use it to get Gutsy then use it again to get Hardy.

Read some of these:

[LIST]
[*][install vs upgrade]("http://www.google.com/custom?hl=en&client=google-coop-np&cof=AH%3Aleft%3BS%3Ahttp%3A%2F%2Fcrunchbang.org%2Fubuntu-search-engine%2F%3BCX%3AUbuntu%2520Search%2520Engine%3BL%3Ahttp%3A%2F%2Fcrunchbang.org%2Fimages%2Fbashful%2Fgoobuntu.gif%3BLH%3A100%3BLP%3A1%3BLC%3A%230000CE%3BVLC%3A%2352188C%3BGALT%3A%23009900%3B&adkw=AELymgW8uam0NNm8AfsLYbEF80DBYeZ6xzNbliGXPbdAa2I5BtTdcxdeOht_AFeAQOmj4_JqV3wI3YT4bftV-X7AzTCzB_jlWBZnnP7TKcxvMXu-Wig8T40&q=install+vs+upgrade&btnG=Search&cx=012285703143635244993%3Ai9yr8qlpb18")
[*][upgrade vs install]("http://www.google.com/custom?hl=en&client=google-coop-np&cof=AH%3Aleft%3BS%3Ahttp%3A%2F%2Fcrunchbang.org%2Fubuntu-search-engine%2F%3BCX%3AUbuntu%2520Search%2520Engine%3BL%3Ahttp%3A%2F%2Fcrunchbang.org%2Fimages%2Fbashful%2Fgoobuntu.gif%3BLH%3A100%3BLP%3A1%3BLC%3A%230000CE%3BVLC%3A%2352188C%3BGALT%3A%23009900%3B&adkw=AELymgW8uam0NNm8AfsLYbEF80DBYeZ6xzNbliGXPbdAa2I5BtTdcxdeOht_AFeAQOmj4_JqV3wI3YT4bftV-X7AzTCzB_jlWBZnnP7TKcxvMXu-Wig8T40&q=upgrade+vs+install&btnG=Search&cx=012285703143635244993%3Ai9yr8qlpb18")
[/LIST]

---

### Post by misternewbie on 2008-03-16
> **Bruce M. said:**
> To use the update manager you MUST follow the chain so to speak:

Dapper > Edgy > Feisty > Gutsy > Hardy

You'd have to use it to get Gutsy then use it again to get Hardy.

Read some of these:

[LIST]
[*][install vs upgrade]("http://www.google.com/custom?hl=en&client=google-coop-np&cof=AH%3Aleft%3BS%3Ahttp%3A%2F%2Fcrunchbang.org%2Fubuntu-search-engine%2F%3BCX%3AUbuntu%2520Search%2520Engine%3BL%3Ahttp%3A%2F%2Fcrunchbang.org%2Fimages%2Fbashful%2Fgoobuntu.gif%3BLH%3A100%3BLP%3A1%3BLC%3A%230000CE%3BVLC%3A%2352188C%3BGALT%3A%23009900%3B&adkw=AELymgW8uam0NNm8AfsLYbEF80DBYeZ6xzNbliGXPbdAa2I5BtTdcxdeOht_AFeAQOmj4_JqV3wI3YT4bftV-X7AzTCzB_jlWBZnnP7TKcxvMXu-Wig8T40&q=install+vs+upgrade&btnG=Search&cx=012285703143635244993%3Ai9yr8qlpb18")
[*][upgrade vs install]("http://www.google.com/custom?hl=en&client=google-coop-np&cof=AH%3Aleft%3BS%3Ahttp%3A%2F%2Fcrunchbang.org%2Fubuntu-search-engine%2F%3BCX%3AUbuntu%2520Search%2520Engine%3BL%3Ahttp%3A%2F%2Fcrunchbang.org%2Fimages%2Fbashful%2Fgoobuntu.gif%3BLH%3A100%3BLP%3A1%3BLC%3A%230000CE%3BVLC%3A%2352188C%3BGALT%3A%23009900%3B&adkw=AELymgW8uam0NNm8AfsLYbEF80DBYeZ6xzNbliGXPbdAa2I5BtTdcxdeOht_AFeAQOmj4_JqV3wI3YT4bftV-X7AzTCzB_jlWBZnnP7TKcxvMXu-Wig8T40&q=upgrade+vs+install&btnG=Search&cx=012285703143635244993%3Ai9yr8qlpb18")
[/LIST]

Oh I see, I guess I'll just get Gusty now and upgrade to Hardy when it is released.

---

### Post by davarino on 2008-03-22
> **mssever said:**
> 
As far as upgrading goes, you won't be able to upgrade to Hardy unless you're running Gutsy. So I don't think that the advice to wait for Hardy is valid. Upgrading can be problematic at times, but I've upgraded my desktop from Dapper => Edgy => Feisty => Gutsy. 

Is that strictly true that you can't move up to Hardy unless you have Gutsy? I'm asking because I was very much under the impression that **L**ong **T**erm **S**upport for *Dapper* would include the ability to upgrade to the next LTS version relatively easily. (I am aware that if you choose the non-LTS route you have to upgrade through each avatar until you get where you want to.)

---

### Post by mssever on 2008-03-23
> **davarino said:**
> Is that strictly true that you can't move up to Hardy unless you have Gutsy? I'm asking because I was very much under the impression that **L**ong **T**erm **S**upport for *Dapper* would include the ability to upgrade to the next LTS version relatively easily. (I am aware that if you choose the non-LTS route you have to upgrade through each avatar until you get where you want to.)

AKAIK, you can upgrade directly from Dapper to Hardy.

(I wonder how many people are still using Dapper? It was fine as a server platform, but on the desktop, Ubuntu has advanced so far that I can't imagine using Dapper anymore.)

---

### Post by davarino on 2008-03-24
Good question about how many are still using Dapper.

I am still using it and am aware of the changes that have taken place... but I have personally experienced the chagrin of "major updating issues".

The past two x.10 versions have had widespread problems with updating. The x.04 versions have seemed to hold together better (except for Dapper, which needed to go to 6.06 in order to really run tight).

My computer is part of my livelihood, so I'm not going to take chances on "upgrading" when more than half of my previous attempts have resulted in serious downtime.

I'll wait until upgrading makes real sense to me rather than the upgrading being simply a systemwide tweak. Tweaks introduce twice as much variance as "use without change" - the variance *may* be good, but it may be bad. :)

---

