---
title: "Updated hplip, now it can't find scanner"
date: 2015-05-24
forum: General Help
---

### Post by Ralph L on 2015-05-24
I am running ubuntu 12.04 and have an HP 7520 all in one printer scanner copier.  I did an update a couple months ago that updated hplip and now it can't find the scanner.  
When I try xsane I get "no devices available".  When I try Simple scan I get "no scanner detected".  I have tried re-installing the printer, but it doesn't help.  Printer works fine.  [https://answers.launchpad.net/hplip/+question/233482](https://answers.launchpad.net/hplip/+question/233482) says that upgrading to hplip 3.13.8 fixed his similar problem.  My questions are:
1.  What is the correct way to upgrade to hplip 3.13.8?  Synaptic says hplip 3.12.2-1 is the latest version in the 12.04 repository, so I would installing something that is not officially available for 12.04.  In the past I have had problems, when I installed packages newer than the repository package.  For example, in such cases synaptic doesn't seem to know that I have installed a later version and incorrectly lists the installed version.  Any instructions on how to do this correctly would be appreciated.
2.  If anybody has had this same problem, please tell me how you fixed it.

Thank you

---

### Post by Geoffrey_Arndt on 2015-05-24
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

Current version is 3.15.4 - - the above link has a deb download (that I recommend using "gdebi" installer for).    Or there are instructions for manual install of the install script on the link page.

Re install of latest packages, . . . only do when no other choice.   Best way is to use PPA's.    Some updates are provided by Canonical such as Firefox updates, and LibreOffice, but in general, stay within the current version for your distro.

As a last resort, save your data, and install 14.04 LTS or 15.04 (which will have the latest HPLip and CUPS packages.

---

### Post by Ralph L on 2015-05-26
Geoffrey_Arndt:  Thanks for the response.  I found this site which described how to use backports: [http://askubuntu.com/questions/10082/which-is-the-best-way-to-install-new-hplip-versions](http://askubuntu.com/questions/10082/which-is-the-best-way-to-install-new-hplip-versions). I went to Synaptic>Settings>Repositories>Updates and checked the box "Unsupported updates (precise-backports).  Then I entered the following code into Terminal:```
sudo apt-get --target-release precise-backports install hplip
```This installed hplip 3.13.9, which fixed my problem.  I am uncertain of installing software that is not in a repository (in this case a precise repository).  Doesn't this mess up Synaptic to have something installed by other than Synaptic (or Ubuntu Software Center)?????  Any advice on this would be appreciated for future problems of this sort.

---

### Post by dino99 on 2015-05-26
'synaptic' is the 'apt' gui frontend (also like  USC) and use xapian's index to communicate

---

