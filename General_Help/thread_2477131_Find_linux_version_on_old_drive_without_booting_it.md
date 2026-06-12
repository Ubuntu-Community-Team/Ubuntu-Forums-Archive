---
title: "Find linux version on old drive without booting it."
date: 2022-07-15
forum: General Help
---

### Post by vidtek on 2022-07-15
I have some old drives lying around and wanted to know how to find the installed linux versions.

Googling brought many results for a booted system, and to discover a windows version from a running linux system but virtually nothing for finding out what linux version is on these old drives without firing them up and booting them.  True debian has /etc/debian_version  in my case it gave:  bookworm/sid - not really much help.  

I found:

 **/var/log/installer/version ** 

gave me the information I wanted.  In this case: ubiquity 22.04.15  (Jammy)

Hope this helps others.

Tony****

---

### Post by Holger_Gehrke on 2022-07-15
'/var/log/installer/version' is the name and version of the installer program which may or may not have anything to do with the OS release. '/etc/lsb_release' will give you distribution id, version, codename and description (but **not** the flavour). '/var/log/installer/media-info' will give you a description of the media the OS was installed from which does include the name of the flavour.

Holger

---

### Post by vidtek on 2022-07-15
Thank you for your reply Holger.  This particular drive had a blank /etc/ lsb_release file, so not a lot of good there.
/var/log/installer/media-info was missing altogether.

---

### Post by Impavidus on 2022-07-15
You can also try the software sources. Read /etc/apt/sources.list. Assuming it was up-to-date the last time it was used and doesn't use mixed repositories (which would be a really bad idea), the version of an OS is the version of its sources.

Or you can check /etc/issue.

---

### Post by deadflowr on 2022-07-15
There should be an /etc/os-release file with the same general information as the /etc/lsb_release file.
/etc/os-release is a symlink to the true file in /usr/lib/os-release.

The installer/version showing ubiquity actually matching the released version is rather new.
They changed that around 16.10.
Older versions used a more sequential string.
Example is on an /var/log/installer/version I have for a 16.04.3 install (it's been upgraded and is currently 20.04.4) the ubiquity string is "ubiquity 2.21.63.4"
So that string doesn't tell you anything useful about what OS is installed or what it was at install time.

---

### Post by yancek on 2022-07-15
You could try:  cat /etc/*release* which should provide detailed info.  Output on my laptop shown below.  Make sure you are in the correct filesystem, mount the / partition or do a chroot.

```
 cat /etc/*release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.4 LTS"
NAME="Ubuntu"
VERSION="20.04.4 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.4 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
 
```

---

### Post by vidtek on 2022-07-15
Deadflowr - You nailed it for me.  

That's a nice quick and easy way to find the flavour, no booting, messing about with chroots, a quick file inspection and there it is. thank you.

Tony.

---

### Post by vidtek on 2022-07-15
Thanks for the reply, this method is what I was trying to avoid.  Check out deadflowr's post.

Tony.

---

### Post by vidtek on 2022-07-16
Impavidus - thanks for the reply, I'll check it out.

Tony.

---

### Post by ActionParsnip on 2022-07-16
```
 
cat /etc/os-release

``` 
Will work on most Linux flavours to show you what you are logged in to

---

