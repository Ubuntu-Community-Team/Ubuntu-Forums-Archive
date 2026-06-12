---
title: "Who's in charge of the Thunderbird package?"
date: 2019-09-13
forum: General Help
---

### Post by brent on 2019-09-13
The Thunderbird package was rumored to be (at long last) updated to v68 early september, but that time is about to pass, making the delay between the original v68 from Mozilla and availability in Ubuntu pass the half year mark. I can't find out who's in charge of the Thunderbird package, so I could ask what the hold-up in, and hopefully an ETA. A lot has improved for the best, and plugins are starting to move to a 68 minimum. Meanwhile, Mozilla has already provided a first point-release.

Hope anyone knows more about what's going on.

---

### Post by SeijiSensei on 2019-09-13
[https://packages.ubuntu.com/bionic/thunderbird](https://packages.ubuntu.com/bionic/thunderbird)

---

### Post by SeijiSensei on 2019-09-13
[https://packages.ubuntu.com/bionic/thunderbird](https://packages.ubuntu.com/bionic/thunderbird)

Even on 19.04 I have 60.8.0.

---

### Post by PaulW2U on 2019-09-13
According to the [Thunderbird 68.1 Release Notes]("https://www.thunderbird.net/en-US/thunderbird/68.1.0/releasenotes/") the new version is only being offered as a direct download from [thunderbird.net]("https://www.thunderbird.net/") and not as an upgrade from earlier versions. Could that be the reason we haven't yet seen an update in the Ubuntu repositories?

I think we will have to wait until Thunderbird 68.2 is released. Just my opinion. Don't quote me. :)

---

### Post by walts48 on 2019-09-13
The Thunderbird build of 60.9.0 from the Thunderbird Council, independent from the Mozilla Corporation since about 2012, isn't getting updated to version 68.0 until version 68.2.0 as I now understand it. I expect Ubuntu and other Linux distributions to do the same.

The Thunderbird Council did release 68.1.0 as an update to version 68.0.

I know they still have a lot of old Mozilla cruft in some areas. That might be because the Mozilla Foundation (not the developers of the fine web browser, that is the Mozilla Corporation) is the legal and financial home for Thunderbird.

If you are in a hurry to use 68.1.0 go to [https://www.thunderbird.net/en-US/thunderbird/all/](https://www.thunderbird.net/en-US/thunderbird/all/)

---

### Post by brent on 2019-09-13
> **PaulW2U said:**
> 
I think we will have to wait until Thunderbird 68.2 is released. Just my opinion. Don't quote me. :)

When v68.0 just came out, the same stories we're spread about 68.1. I'd just like to have some comment from an actual package maintainer. The listed team on packages.ubuntu.com is not very specific ;)

Not sure what their sources are, but [https://www.omgubuntu.co.uk/2019/08/thunderbird-68-new-release](https://www.omgubuntu.co.uk/2019/08/thunderbird-68-new-release) mentiones early september in the update.

@walts48: the listed maintainer is not the Thunderbird council: could you link to them or where their role is defined. And where do you get your info?

---

### Post by mc4man on 2019-09-13
The only 68 version in Debian is in the experimental repo which Ubuntu won't pull from.
If adventurous you could try the snap from the edge channel. 
It would likely have to be set up from scratch due to the confinement bs.

---

### Post by brent on 2019-09-13
Getting TB68 isn't the issue, it's wether or not it's still coming in the official packages, as some sources claim, or if the package is practically or officially orphaned.

---

### Post by TheFu on 2019-09-13
I'm on an LTS.  I don't want a new version. I want the deployed version, but with security fixes. Nothing more. 
I suppose if I were on the bleeding edge, a case could be made for inflicting the newest version.  We are LTS-only people.

---

### Post by Yellow Pasque on 2019-09-13
> **brent said:**
> Getting TB68 isn't the issue, it's whether or not it's still coming in the official packages, as some sources claim, or if the package is practically or officially orphaned.

The package is not orphaned in any way in Debian or Ubuntu. You'll have to wait for 68.2 (assuming TB doesn't delay it further). Asking the maintainer(s) will not make it come any faster. 
You'll probably see 60.9 before 68.x, because 60.9 is a security update and already in Debian unstable.

---

### Post by NM5TF on 2019-09-13
just downloaded v68.1 in my Arch distro from the repos....haven't noticed any differences yet...

---

### Post by PaulW2U on 2019-09-14
This morning a build of Thunderbird 68.0  was uploaded to the -proposed repository for the current development release, eoan. I’m posting from a mobile so not really in a position to easily check the position for the supported releases of Ubuntu.  An obvious indication that the new version is being prepared for release. 

As with anything Ubuntu related it’ll be released when the appropriate developers deem it to be ready.

---

### Post by walts48 on 2019-09-14
> **brent said:**
> 

@walts48: the listed maintainer is not the Thunderbird council: could you link to them or where their role is defined. And where do you get your info?

I don't have the maintainers information. I think the TB developers were looking for that also. Not sure they found it,

I get my information from following Mozilla and Thunderbird too closely with mailing list subscriptions, newsgroup subscriptions, news feeds, IRC channels, and volunteer help with the developers of Thunderbird, testing these releases as release candidates before they become available to the general public.

[https://wiki.mozilla.org/Thunderbird:Home](https://wiki.mozilla.org/Thunderbird:Home)

We could use more help doing testing.

---

### Post by deadflowr on 2019-09-14
The maintainer is the Ubuntu Mozilla Team.
[https://launchpad.net/~mozillateam]("https://launchpad.net/~mozillateam")

---

