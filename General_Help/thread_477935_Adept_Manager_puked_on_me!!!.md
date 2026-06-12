---
title: "Adept Manager puked on me!!!"
date: 2007-06-18
forum: General Help
---

### Post by Middle_Man on 2007-06-18
okay... i was trying to update my OS. im using Kubuntu edgy and wanted to move to fiesty. i ran across a tut to show me how.

[http://kubuntu.org/announcements/7.04-release.php#upgrade](http://kubuntu.org/announcements/7.04-release.php#upgrade)

i followed it till i got to step 3. i copied
 [http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/](http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/)[COLOR="Red"]edgymain[/COLOR]
into my repository thing. 

now when i try to run Adept Manager it gives me this message. 

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

so i tried running Apt-Setup and Apt-get Update in the command line. neither helped but i am 100% positive its that busted link i put into my repository... how do i fix this? 

this is what i get when i type in apt-get update in the command line.

apt-get update
E: Type 'http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/edgymain' is not known on line 1 in source list /etc/apt/sources.list

Can you please tell me how to fix this and how to get my kubuntu 7 update! many thanks goes in advance. also does anyone have a list of good repository's that i can get and install the following apps.

SongBird
Beryl (its some sort of graphic program)
and thats about it. thanks.

---

### Post by rameshln on 2007-06-19
I too have the same problem for quite sometime. In my case, I tried to install a software called called prozgui and that failed. After that my apt database is some inconsistent state and I got this problem. 

I tried but I can't remove this unclean prozgui installation too.

Looking forward to any reply.

---

### Post by Kodfish on 2007-06-19
you want "deb [http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/edgymain](http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/edgymain) main backports" instead of [http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/edgymain](http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/edgymain)

---

