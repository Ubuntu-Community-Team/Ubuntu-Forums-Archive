---
title: "Question on PPAs and Synaptic Download Manager"
date: 2014-09-11
forum: General Help
---

### Post by shag00 on 2014-09-11
In the short time I have been a Ubuntu user I think I have come to terms with PPAs and Synaptic. I have run into an unexpected issue where the Launch Pad web page tells me of a new release dated 10-9-14 (yesterday) has successfully been built but when I launch Synaptic its latest version is dated 02-08-14 and yes I have reloaded (several times) Synaptic to update it, the existing installed version was installed via Synaptic. I have checked the sources and they are OK. Is it right to believe that if a package is shown on Launch Pad that it should be downloadable by Synaptic or am I missing something.

Ubuntu 14.04

---

### Post by Bucky Ball on 2014-09-11
> **shag00 said:**
> Is it right to believe that if a package is shown on Launch Pad that it should be downloadable by Synaptic ...


No. It's complicated. You might find the newest release in 14.10 ... if it's stable and integrates with everything else, or in 14.04 LTS eventually. The change is not immediate. It doesn't enter the official Ubuntu repos immediately on release. You may be able to install a PPA of the software you're after which would then update you to the latest release when a new one happened, but I tend to try and avoid third-party PPAs myself. They can be problematic and cause conflicts.

---

### Post by shag00 on 2014-09-11
Thanks Bucky but it appears I have not communicated my problem clearly, the release I want is listed on the Launch Pad web page [https://launchpad.net/~videolan/+archive/ubuntu/master-daily](https://launchpad.net/~videolan/+archive/ubuntu/master-daily) for VLC 14.04. I have the repository address in Synaptic (as it gives me an earlier version which I previously installed), my query is why the new version in not updated/available in Synaptic. 

I am not asking anything in relation to official Ubuntu repos.

Looks like my error as the package was not successfully built.

---

### Post by Bucky Ball on 2014-09-11
All good. Good luck. 

(Just FYI, I am running 2.1.4-0ubuntu14.04.1 installed directly from Synaptics, no PPAs. Just straight from the repos. ;))

---

