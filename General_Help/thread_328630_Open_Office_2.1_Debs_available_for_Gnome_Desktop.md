---
title: "Open Office 2.1 Debs available for Gnome Desktop"
date: 2006-12-31
forum: General Help
---

### Post by tomcat1965 on 2006-12-31
Hi,as I've been seeing alot of posts about getting .deb's for Open Office 2.1 which everyone seems to want due to the font appearance and bugs in 2.04 I have made some debs available via torrent at [http://linuxtracker.org/torrents-details.php?id=3349&hit=1]("http://linuxtracker.org/torrents-details.php?id=3349&hit=1") 

Hope this helps some people. I have tested and installed from them and so far so good.....

First mark all entries relating to OO 2.04 for complete removal via Synaptic...and remove!

I installed to "/opt/openoffice.org2.1" ...best place I think.

From the terminal type "sudo chmod 777 *.deb" 

Then type"sudo dpkg -i *.deb"

After that there is a package to install the menu's in the right place...YAY!.....

Type "cd desktop-integration" then

Type"sudo dpkg -i openoffice.org-debian-menus*.deb"

Now you will have all the apps under the Applications>Office menu.

Or you could just install Gnome Office with Abi-word ....no font problems and it starts fast.

---

### Post by K.Mandla on 2007-01-05
(Moved to General Help. ;) )

---

### Post by rdoolen on 2007-01-05
Will this ever apear in Synaptic or apt-get etc. for Dapper?

---

### Post by mexlinux on 2007-01-06
Is this openoffice.org official?
Or oo-go.org build?

---

### Post by elfgoh on 2007-01-06
Hmmm, I read that there's a vulnerability affecting all version of OOo except 2.1. [http://www.itwire.com.au/content/view/8399/53/](http://www.itwire.com.au/content/view/8399/53/)

Does this mean that OOo 2.1 will be backported to edgy?

---

### Post by jeremy on 2007-01-06
That would be nice, however, there may only be a patched 2.04.

---

### Post by elfgoh on 2007-01-08
Hmmm... ic.... Would it make sense to try and use the OOo debs in Feisty branch, if it&#347; already there?

---

### Post by Enverex on 2007-01-11
May I ask why why 2.1 won't be available for Edgy? (sorry, I came from another distro and I'm not familiar with the whole "not upgrading" thing).

---

### Post by andreas64 on 2007-01-12
Hi,

you'll never get newer versions of programs as long as you stay with the same Ubuntu-version. There will only be security updates. If you want the newest stuff, you have to upgrade to the next Ubuntu-version ( e. g. Feisty in April ).

Andreas

---

### Post by Enverex on 2007-01-12
Oh... damn, that's a little annoying... guess there is a price to pay for everything.

---

### Post by Tanker Bob on 2007-01-12
Has/can anyone do this for Kubuntu desktop?

---

### Post by Delkster on 2007-01-12
> **Enverex said:**
> May I ask why why 2.1 won't be available for Edgy? (sorry, I came from another distro and I'm not familiar with the whole "not upgrading" thing).

New upstream releases (e.g. Gaim 1.5 > 2.0) aren't generally included in the updates for a stable distribution. New releases may fix bugs but can sometimes also have new ones, so once the distro has been made stable and problems ironed out, it doesn't make much sense to take the chance of introducing new ones with maintenance updates.

Moreover, since security and bug fix udates are for maintenance and people expect them to only fix things, not change the features of their system, it wouldn't be a good idea to change the UI or the features offered by applications with those updates. Security updates may even be downloaded and applied automatically, and in those cases it would be particularly unhelpful to cause the UI to change all of a sudden with no reason apparent to the user.

New upstream releases for some packages may be added to the stable distro in the backports repository, so if you want some applications to be the latest and greatest you may want to take a look there.

---

### Post by bobfrommarketing on 2007-02-02
Sorry, but I don't get this whole torrent thing.. isn't it supposed to start downloading or something? All it does is show a dialog that ticks off time. 
Status 0.0 of 123.4mb, time elapsed 23 minutes 43 seconds

---

### Post by gary_emms on 2007-02-03
Is there a GB English version available yet?

---

### Post by hammadr89 on 2007-03-05
When I set anything OO related to be removed in the synaptic manager, it says it will also have to remove "ubuntu desktop". So how can I go ahead there?

---

