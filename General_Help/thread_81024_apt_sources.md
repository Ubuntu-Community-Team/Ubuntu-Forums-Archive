---
title: "apt sources"
date: 2005-10-23
forum: General Help
---

### Post by drolyk on 2005-10-23
Which sources I need to set in /etc/apt/sources.list to be able get latest updates ?

---

### Post by Iandefor on 2005-10-23
You need the backport repositories. For more information, go to [here]("https://wiki.ubuntu.com/UbuntuBackports")

---

### Post by mbourd25 on 2005-11-01
But what is a good source.list we can use to retrieve the latest software in Kubuntu. I was looking at updating Amarok using Adept but it didn't find it. I had to download the deb files for that and update it that way. It not hard to do but still it should be in the repositories.

Thanks.

---

### Post by N6546R on 2005-11-01
My understanding is that Ubuntu/Kubuntu is intended as a stable snapshot, updated every six months. The price we pay for stability is that the snapshot doesn't significantly change for six months.

Between releases you can certainly build and install whatever you want, but probably you aren't going to see updated applications in the mainstream repositories.

Perry

[QUOTE=mbourd25]But what is a good source.list we can use to retrieve the latest software in Kubuntu. I was looking at updating Amarok using Adept but it didn't find it. I had to download the deb files for that and update it that way. It not hard to do but still it should be in the repositories.

Thanks.[/QUOTE]

---

### Post by Iandefor on 2005-11-03
> But what is a good source.list we can use to retrieve the latest software in Kubuntu. I was looking at updating Amarok using Adept but it didn't find it. I had to download the deb files for that and update it that way. It not hard to do but still it should be in the repositories.

Thanks.

N6546R hit the nail on it's head. Each release of Ubuntu is a stable snapshot of all the packages in it as of the release date- meaning that by the time Dapper is released, all the packages in Breezy will be out of date by a half-year. However, if you want the latest bleeding-edge software, you can use the backports repositories, which, as far as I know, are not up for Breezy, although they should be soon.

---

### Post by ecobuntu on 2005-11-03
[QUOTE=Iandefor]N6546R hit the nail on it's head. Each release of Ubuntu is a stable snapshot of all the packages in it as of the release date- meaning that by the time Dapper is released, all the packages in Breezy will be out of date by a half-year. However, if you want the latest bleeding-edge software, you can use the backports repositories, which, as far as I know, are not up for Breezy, although they should be soon.[/QUOTE]


You could also run Dapper!  Or you could run Debian Sid.  All distributions are like this.  But in all honesty, what makes Amarok 1.3.5 that much better than 1.3.4 for example?  Not much.

---

