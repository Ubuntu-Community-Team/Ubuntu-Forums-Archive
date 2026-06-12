---
title: "Ubuntu Click package format questions"
date: 2013-10-14
forum: General Help
---

### Post by JayArtist on 2013-10-14
Hi,

I've just read that 13.10 will be including a new package fromat called "Click". I've been trying to find more detail on it online, but there's not a lot of info just now. so I've a couple of questions for those that might know ;)

1) Currently backing up indivudual packages to distribute to other ubuntu machines is tricky, will this fix the issue?
e.g. Image you have 30 Ubuntu PCs and want to add Gimp, you don't have a network for all the PCs, nor an Internet connection - would the Click format allow you to just copy Gimp to a pendrive and copy it to the other mahcines without missing dependencies?

2) Is this new format only for new software, or will old software, such as Gimp 2.8.3 for example be moved to this format? Or more likely will there probably be a transitional time over several years till developers move over to this package method?

Cheers, Jay.

---

### Post by slickymaster on 2013-10-14
As far as I've been able to understand it the proposed features of this new package installer/format would be no dependencies between applications (packages would only depend upon the base system and ship everything they need bundled within the package), each package would install to its own directory, root support wouldn't always be required and the entire package format would be purely declarative.

Don't know if you already saw this, but it's a good read on the subject: [https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037074.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037074.html)

---

### Post by grahammechanical on 2013-10-14
Click packaging will not solve the first requirement of the two that you listed. It is not meant to do that. Click packaging is meant for developers wanting to provide applications for the Ubuntu phone/tablet platform. So, I don't think that Ubuntu 13.10 will include a new package format called "Click." 

Developers who install the Ubuntu Software Development Kit (SDK) then we will be able to package their applications that they developing using the Ubuntu SDK with "Click." It works in a very simple fashion. It is expected that applications packaged by Click will be able to run on both the phone/tablet platform and the desktop platform. All this is very much under development. Developers will first need to get their applications accepted in the Ubuntu Software 
Centre. I think that users installing software through the Software Centre will notice any difference.

Regards.

---

