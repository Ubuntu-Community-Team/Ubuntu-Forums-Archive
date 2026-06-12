---
title: "Libreoffice 5.3.0"
date: 2017-02-02
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-02-02
I'm trying to upgrade Libreoffice to 5.3.0 so I went to their website and downloaded the rpm.  Can someone please tel  me how to install it?

```
/Downloads/LibreOffice_5.3.0.3_Linux_x86-64_rpm# ./ installbash: ./: Is a directory
root@bubba-110-194:/home/bubba/Downloads/LibreOffice_5.3.0.3_Linux_x86-64_rpm# ./install


This script is for installation without administrative rights only
Please use rpm to install as root


User Mode Installation script for developer and knowledgeable early access tester


This installation method is not intended for use in a production environment!
Using this script is unsupported and completely at your own risk


Usage: ./install [-lU] <rpm-source-dir> <office-installation-dir>
    <rpm-source-dir>: directory *only* containing the Linux rpm packages to be installed
                      or language pack shell script containing the rpm packages
    <office-installation-dir>: directory to where the office will get installed.
```

---

### Post by vasa1 on 2017-02-02
You should have downloaded the deb!

Also, installing software from anywhere other than the Software Center isn't advisable unless you know what you're doing.

---

### Post by shane_faulkinbury2 on 2017-02-02
I would, but the problem with the Software Center is they don't tell you what version you're getting!

---

### Post by howefield on 2017-02-02
> **shane_faulkinbury2 said:**
> but the problem with the Software Center is they don't tell you what version you're getting!

Click on the icon of the relevant software package in the Software Centre and you'll get the details of the package including the version number. Sometimes you have to scroll down to see it.

---

### Post by oldrocker99 on 2017-02-02
Go here:[https://www.libreoffice.org/download/libreoffice-fresh/?type=deb-x86_64&version=5.3.0&lang=en-US](https://www.libreoffice.org/download/libreoffice-fresh/?type=deb-x86_64&version=5.3.0&lang=en-US) and download the .tar.gz file.
Then (assuming you're in the download folder):```
tar -xvf LibreOffice_5.3.0_Linux_x86-64_deb.tar.gz
```

This will extract the into a folder, containing a DEBS folder, which  is what you want. From that folder, enter```
sudo dpkg -i lib*
```.

That will install the whole suite.

Just so you know, **ALL** installation packages for Ubuntu are .deb files, not .rpm files.

---

### Post by vasa1 on 2017-02-02
> **shane_faulkinbury2 said:**
> I would, but the problem with the Software Center is they don't tell you what version you're getting!
I don't use any Software Center and so cannot comment.

```
apt-cache policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:5.1.4-0ubuntu1
  Version table:
     1:5.1.4-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     1:5.1.2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```

---

### Post by shane_faulkinbury2 on 2017-02-02
Thanks for the deb idea!  Downloaded an installing now.  Question about the language pack though.  Will it be English or do I need to change that?

---

### Post by ajgreeny on 2017-02-02
Is it essential that you have the very latest version of LO for some reason?

One way to get a newer version than is generally available in the repos is to enable the PPA which will give you LO-Version: 5.2.5.1.
Go to [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa) for all the details and how to enable it.  

No doubt that ppa will very soon have the 5.3 version.

I've been using this ppa for a long time with no problems, but bear in mind that the packages are not as fully tested as those from the standard repos so bugs may be present.

---

### Post by shane_faulkinbury2 on 2017-02-02
Thanks AJ!

---

### Post by ajgreeny on 2017-02-03
Lo and behold! Today doing my daily updates, LO-5.3.0 arrived in that ppa.

It seems to work just as well as the previous version did, but then, in my experience, all versions have worked brilliantly for my purposes for many years.

---

### Post by vasa1 on 2017-02-03
> **ajgreeny said:**
> Lo and behold! Today doing my daily updates, LO-5.3.0 arrived in that ppa.

It seems to work just as well as the previous version did, but then, in my experience, all versions have worked brilliantly for my purposes for many years.So have you gone the ribbon route? When I update, I'll probably prefer the "single toolbar" option. That way, I hope to get at least one more row of data on my laptop!

---

### Post by ajgreeny on 2017-02-05
What is the ribbon route?

I have not used MS Office since the Office-97 version, long before the ribbon layout that everyone moaned about, so I am not totally sure what you mean, but here is what my toolbars look like; exactly what they were like in all previous LO versions.  This may look very old-fashioned to some users but it suits me and my way of working.

Having played around with the View ->Toolbar Layout menu options I see there are several layouts available, most of which look horribly clumsy to me when compared with what I use, and I don't really know which of those is the Ribbon layout, or if you get to it some other way entirely.

---

### Post by howefield on 2017-02-05
> **ajgreeny said:**
> Having played around with the View ->Toolbar Layout menu options I see there are several layouts available, most of which look horribly clumsy to me when compared with what I use, and I don't really know which of those is the Ribbon layout, or if you get to it some other way entirely.

One has to enable "experimental features" from the Options > Libreoffice > Advanced menu, then restart Libreoffice and select View > Toolbar Layout > Notebookbar.

I tried it and found it a bit ugly, but you know what they say about beauty :)

---

### Post by ajgreeny on 2017-02-05
> **howefield said:**
> One has to enable "experimental features" from the Options > Libreoffice > Advanced menu, then restart Libreoffice and select View > Toolbar Layout > Notebookbar.

I tried it and found it a bit ugly, but you know what they say about beauty :)
Thanks howefield.
I did a quick search after my post above and found out what it was, having not even realised there was that alternative toolbar-layout.

Having tried it myself I agree with you that it is both ugly and difficult to use (for me at least), so I have gone back to my old default view.

It took me a while to figure out how to get out of that "Notebookbar" view as I could not find the View menu item again.
For anyone else in the same situation and wanting to return to default view, just click on the Document icon to the left of the **File** tab and you can enable the menubar again and go bnack to normal.

---

