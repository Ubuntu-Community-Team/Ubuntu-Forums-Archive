---
title: "Tp upgrade or not to upgrade"
date: 2024-08-18
forum: General Help
---

### Post by kinddolphin8827 on 2024-08-18
In several other threads on this forum that all non gnome variations of Ubuntu are only supported for three years post release. Does this mean that I have to upgrade  to the next release on release day?

---

### Post by Dennis N on 2024-08-18
Well, for flavors of Ubuntu, it's 3 years support for LTS releases, like Xubuntu 20.04 and 22.04. For non-LTS, like Xubuntu 22.10, the support is 9 months. LTS releases are 2 years apart, with non-LTS releases 6 months apart between LTS releases.
To answer your question:
On release date of an LTS, you have a year to upgrade to it from the previous LTS.
On release date of a non-LTS, you have 3 months to upgrade from the previous non-LTS.
OK?

---

### Post by guiverc on 2024-08-18
I'll provide my 2c, but note this is just how I personally see it, and I'll use Lubuntu 20.04 LTS as example here.

Lubuntu 20.04 LTS was released in 2020-April (*hence 20.04*) along with Ubuntu 20.04 LTS, however being a *flavor* of Ubuntu Desktop, came with only three years of *supported* life. This support ended back in 2023, as is shown by official Lubuntu annoucements

- [https://lubuntu.me/lubuntu-20-04-lts-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-20-04-lts-end-of-life-and-current-support-statuses/)
- [https://discourse.lubuntu.me/t/lubuntu-20-04-lts-is-end-of-life/4190](https://discourse.lubuntu.me/t/lubuntu-20-04-lts-is-end-of-life/4190)

Hence at back on 1 May 2023, a Lubuntu 20.04 LTS release was no longer supported by the Lubuntu team. In the *Lubuntu.*forum post you'll note suggestion (*and reference back to a prior warning notice*) at using 

```

ubuntu-security-status

``` 

to confirm your system [security] status, where you should note some of your system packages (*including most of the critical packages*) are still supported by Ubuntu until 2025.

ie.   as I see it; what was a Lubuntu 20.04 LTS system that ended support back end-April-2023 is now a Ubuntu 20.04 LTS system where the LXQt desktop is used (ie. *its no longer Lubuntu as Lubuntu no longer support it but the Ubuntu base is still supported; so I think of it as a Ubuntu system*), thus the user could keep using it until the release reaches *end of standard support* end of *April 2025*.

Such users just shouldn't be asking the Lubuntu team for support on the EOL release of Lubuntu 20.04 LTS, as for what security considerations they use (eg. *the LXQt or Lubuntu desktop is no longer managed/updated by the Lubuntu team; thus there maybe increased security risks because of this if contrasted to say Ubuntu Desktop's GNOME*), that is a decision they can make themselves.

Your question about "*have to upgrade  to the next release on release day*" sorry I don't understand or see a connection, as RELEASES and END OF SUPPORT are actually different days, both of which are managed by the *Ubuntu Release Team*, with *flavor* teams using the same identical dates, being warned & alerted to changes/schedules well in advance.

If using my example [(Lubuntu 20.04 LTS) the warning notices for that coming EOL actually went out ~six weeks prior to the EOL notice]("https://discourse.lubuntu.me/t/lubuntu-20-04-lts-is-nearing-its-eol-end-of-life/4087"); as ~six weeks is the same warnings used in most Ubuntu Release team notices; six weeks gives end-users time to plan & action their *release-upgrade* if they've not already done so.  These *EOL warning* notices shouldn't be needed though; eg. 20.04 due to its format (*year. month of 2020.April*) lets you easily know when EOL is; eg. 20+3=2023.April for *flavors like Lubuntu*, and 20+5=2025.April for EOSS of Ubuntu Desktop/Server etc.

---

### Post by werewulf75 on 2024-08-20
Here's my 2 quid's worth (I don't come cheap! :P ). Alongside my main OS of vanilla Ubuntu 22.04 LTS I also multi-boot Ubuntu Unity 22.04 LTS and Ubuntu Mate 22.04 LTS. The last two will reach EOL three years from April 2022, i.e. April 2025. I shan't upgrade them until at least May 2025. (I'm never in a rush to upgrade.) Or I may just attach them to Ubuntu Pro EMS - free for personal use and up to five systems - which gives a total of ten years support. Then again, the problem with that is that only the Ubuntu core and apps will be updated, and not the WM/DE, which could present security issues, so I'm not fully committed yet.

---

### Post by Rubi1200 on 2024-08-20
And I'll throw something out to consider: switch to a distro that uses a rolling release model.

Then, no need to debate whether to upgrade or not since it is an ongoing process.

That's one of the many things I love about Linux; we can choose which road to drive down.

---

