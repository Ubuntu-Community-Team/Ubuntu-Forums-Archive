---
title: "Basing a commercial product on Dapper"
date: 2006-09-04
forum: General Help
---

### Post by jmillikin on 2006-09-04
I'm creating a software product, which will be pre-installed to a laptop and shipped to customers. I'd like to base it on Ubuntu (specifically, Dapper), since I've got the most experience with it at the moment. I have some questions about the GPL, installation media, etc.

First, it's my understanding that the GPL requires source code to be made available. I don't want to run a ubuntu mirror, so does that mean I must bundle all source code for every package on the shipped machine? If so, is there an easy way to download the source code for every package installed?

Second, I would like it to be possible for customers to upgrade their system by inserting a CD-ROM, rebooting, and following a few instructions. Is there an existing piece of software that can do that, or should I start learning how to build a custom boot CD? I'll be packaging the custom software as a series of .deb packages. Ideally, it would be possible to bundle all upgraded .debs on the CD and just install those so it would be possible to test releases for compatibility problems.

Lastly, which installation disk should I use? It seems that the Alternate install CD is the way to go (creating pre-configured OEM systems, setting up automated deployments), but I really only need components for a server (the product is largely web-based). Does the Alternate CD give me the option of which set of packages to install?

---

### Post by skymt on 2006-09-04
* Making source code available can mean anything from hosting it on a public server to sending it to people who ask. Minimum compliance (as I see it; I'm not a lawyer) means giving any differences in code to anyone who asks for it. (EDIT: See [this FAQ](http://www.gnu.org/licenses/gpl-faq.html#DistributeWithSourceOnInternet), specifically the question directly linked to.)

* There is software to build custom live CDs, but I don't think any of it uses Ubuntu as a base.

* It depends on the market. It would probably be easiest to use the text-based alternate installer, assuming the user isn't easily scared.

---

### Post by jmillikin on 2006-09-04
> **skymt said:**
> * Making source code available can mean anything from hosting it on a public server to sending it to people who ask. Minimum compliance (as I see it; I'm not a lawyer) means giving any differences in code to anyone who asks for it. (EDIT: See [this FAQ](http://www.gnu.org/licenses/gpl-faq.html#DistributeWithSourceOnInternet), specifically the question directly linked to.)

* There is software to build custom live CDs, but I don't think any of it uses Ubuntu as a base.

* It depends on the market. It would probably be easiest to use the text-based alternate installer, assuming the user isn't easily scared.

I'm not really trying for minimum compliance, but rather minimum effort. If there's a few lines I can type to download all required sources (think apt-get source *), that would be perfect.

I'll try the alternate installer, then. Only people who'll ever see that screen will be techs anyway, not customers.

---

### Post by skymt on 2006-09-04
Minimum compliance is also minimum effort. You don't need to include all the source. Users probably wouldn't want you to, as that would fill up a lot of disk space. It depends on your market, as always, but I can't imagine many people who want the entire source code for every package in a distribution installed by default. I can't think of a way to do it without a script that parses apt-get output and does an apt-get source for each package. Or downloads the source index file and does an FTP fetch for each file.

---

### Post by David Corrales on 2006-09-04
Just a tip. You can use **dpkg --get-selections** to get an easily parseable list of all installed packages :)

---

### Post by peabody on 2006-09-04
To my knowledge, most of the source code isn't on the Ubuntu Live CD either.  The reason Canonical is still compliant is because they run source code repos of the distro.  If all the software you include is available from the source code repos, you'd be set as far as compliance is concerned.

If you are including custom debs however, you will need some way to offer source code for those debs.  The miminum effort to my knowledge only requires that you mail the source code to people who request it via mail.

---

### Post by jmillikin on 2006-09-05
I'm already including the source code for our product (which is under the GPL). I'm worried about this scenario:

User gets system with libfoo 2.4 installed. After two years, the user finds a problem in libfoo and needs the source code, but it is no longer on the Ubuntu mirrors because it's too old. It's my understanding that I would at that point have to provide the source - unless Canonical keeps source copies of all versions?

---

### Post by peabody on 2006-09-05
> **jmillikin said:**
> I'm already including the source code for our product (which is under the GPL). I'm worried about this scenario:

User gets system with libfoo 2.4 installed. After two years, the user finds a problem in libfoo and needs the source code, but it is no longer on the Ubuntu mirrors because it's too old. It's my understanding that I would at that point have to provide the source - unless Canonical keeps source copies of all versions?

Well, keep a backup copy of all the source packages :).  You only need to provide source code for up to five years I believe.

---

