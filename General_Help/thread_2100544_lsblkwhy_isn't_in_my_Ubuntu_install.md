---
title: "lsblk:why isn't in my Ubuntu install ?"
date: 2013-01-02
forum: General Help
---

### Post by cogset on 2013-01-02
I've seen this utility in other Debian-based distros and I've found its  output more readable than blkid or fdisk -l ,maybe less informative but  IMHO more graphical (so to speak) and easier to read at a quick  glance:it should be part of util-linux package,so is there a reason why  it isn't included in my Ubuntu Lucid installation,and can I install it  somehow ?

---

### Post by andrewruk on 2013-01-02
lsblk was only added in v 2.19 of util-linux (see [http://www.kernel.org/pub/linux/utils/util-linux/v2.19/v2.19-ReleaseNotes](http://www.kernel.org/pub/linux/utils/util-linux/v2.19/v2.19-ReleaseNotes)) and Lucid has v 2.17, so the short answer is that this utility didn't exist when Lucid was released.

---

### Post by cogset on 2013-01-02
Thanks,that would signify that it is not actually possible to install  lsblk in Lucid,since the whole related util-linux package should be  upgraded,right?

---

### Post by dino99 on 2013-01-02
why not upgrading to Precise ?

---

### Post by cogset on 2013-01-02
Two words: Unity,Amazon lens.

---

### Post by Calinou on 2013-01-02
Not only Precise has no Amazon lens, you are also not forced to use Unity.

After upgrading, if you want to use another desktop like the Xfce desktop, just type this in a terminal:
```
sudo apt-get install xubuntu-desktop
```
Then log out and choose Xfce and log in.

---

### Post by Cheesehead on 2013-01-02
A few people I know who do use the Shopping Lens find it quite convenient. And not-scary.

The lens can be easily disabled in User Settings, or uninstalled entirely with a single simple command.

---

### Post by cogset on 2013-01-03
Well this is clearly going off-topic,anyhow :


[LIST]
[*]If I wanted to use Xcfe,wouldn't I be using it right now on Lucid instead of Gnome 2 ?
[*]If  I trusted Amazon,I wouldn't bother uninstalling its search engine  plugin in every Firefox installation I have and then blocking its  omnipresent tracking servers with firewall and hostfile.
[/LIST]
It  really should be discussed in a separate topic I think,but still-while  we're on this-I've read about Canonical being right in partnering with  Amazon as a way to cover some of the expense of developing Ubuntu,which  brings the question:how does Debian,on which Ubuntu itself and a number  of other distros are based,manage to pull it off without even thinking  of such commercial agreements?

---

### Post by Cheesehead on 2013-01-04
> **cogset said:**
> I've read about Canonical being right in partnering with  Amazon as a way to cover some of the expense of developing Ubuntu,which  brings the question:how does Debian,on which Ubuntu itself and a number  of other distros are based,manage to pull it off without even thinking  of such commercial agreements?

The question assumes that Debian and Ubuntu share goals or structure that would permit a single answer to apply to both. Not so. Debian and Ubuntu have very different goals.

Debian is (primarily) a collaboration driven by volunteers. Users are expected to participate - file bugs, test fixes, contribute effort and time. Not oriented to new users. Releases are quality-based, not scheduled. Open governance and discussion. Some applications have uneven quality and amateur design. Nobody can speak authoritatively for the project, nor commit the project to a goal.

Ubuntu is a more centralized project to create a branch of Debian that tries to remain compatible and supportive of Debian, retain much of the open governance, and can create/honor commitments and contracts. Canonical invests in a staff and infrastructure to create and test two releases of Ubuntu each year, plus the various projects it supports (Unity, Upstart, Bazaar, Launchpad, TV, Tablet, Phone, etc.), plus the larger ecosystem projects it contributes code to (Debian, kernel) plus involvement with hardware partners to get Ubuntu pre-installed on OEM systems.

---

### Post by cogset on 2013-01-07
That's very well put,thanks for explaining it-I would however like to see a bit more of this > a branch of Debian that tries to remain compatible and supportive of Debian, retain much of the open governance whereas it seems we're heading in the opposite direction lately.
When someone who is supposed to know what he's talking about comes up with the phrase "we have root" ,as if Ubuntu were no different from Apple and Kindle devices that can be remote-controlled,that doesn't make a good impression,doesn't it ?

---

