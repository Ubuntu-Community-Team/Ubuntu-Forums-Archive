---
title: "dpkg-deb:is there a way to control the list of files being package?"
date: 2012-11-26
forum: General Help
---

### Post by stevench2000 on 2012-11-26
Hi everyone,

I am new to dpkg-deb, but I have some experience in packaging files using RPM.
When using RPM, there is a spec file that you can use the %file tag to control the list of files you want to package and their attributes, such as owner, path, permission.

I was still having this mindset when I was trying to learn dpkg-deb, but couldn't find any references related to this 'inventory control'. The usage for the config file used by dpkg-deb seems like similar to the spec file used by RPM but not entirely identical. I am getting lost here and wondering, is there a way in building packages with dpkg-deb to achieve the same goal of controlling these attributes of files?

Take care and regards,
Steve

---

### Post by melfnt on 2013-03-04
up

I have a similar problem too

---

### Post by schragge on 2013-03-04
Normally, you are not supposed to use *dpkg-deb -b* directly to create deb packages. It's only a quick&dirty method for when you're in a hurry. It may work for very simple packages, or if you know all ins and outs of the deb package format very well. There's almost no error-checking when doing *dpkg -b*.

Instead, you should either work with [Quickly]("http://developer.ubuntu.com/get-started/quickly-workflow/") when writing apps, or create a full-fledged debian source as described at  [uwiki]AppReviewBoard/Submissions/PackageQuickStart[/uwiki] and in the [Debian New Maintainers' Guide]("http://www.debian.org/doc/manuals/maint-guide/").

In the latter case, use [debhelper]("http://manpages.ubuntu.com/manpages/precise/en/man7/debhelper.7.html") in your debian source, particularly [dh_install]("http://manpages.ubuntu.com/manpages/precise/en/man1/dh_install.1.html") (or the file debian/*package*.install) and [dh_fixperms]("http://manpages.ubuntu.com/manpages/precise/en/man1/dh_fixperms.1.html").

---

