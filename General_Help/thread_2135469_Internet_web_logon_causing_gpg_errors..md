---
title: "Internet web logon causing gpg errors."
date: 2013-04-14
forum: General Help
---

### Post by prc292 on 2013-04-14
Has anyone else heard of this problem. Im on a public wifi connection at school and it requires a web logon to access the internet,  im getting gpg errors when attempting to update. 

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

tried switching update servers but did not help

tried this:

sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update

no luck.

any ideas or need more info let me know. Really appreciate any help with this.

---

### Post by prshah on 2013-04-14
> **prc292 said:**
> Im on a public wifi connection at school and it requires a web logon to access the internet,  im getting gpg errors when attempting to update. 

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


Please see [http://ubuntuforums.org/showthread.php?t=802156](http://ubuntuforums.org/showthread.php?t=802156) (esp. the post on broken proxies) for a possible solution.

---

