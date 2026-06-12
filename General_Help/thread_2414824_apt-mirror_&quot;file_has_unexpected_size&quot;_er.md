---
title: "apt-mirror: &quot;file has unexpected size&quot; error"
date: 2019-03-15
forum: General Help
---

### Post by digikar on 2019-03-15
I have been trying to set up a local Ubuntu Bionic (18.04) repository using [FONT=courier new]apt-mirror[/FONT] and [FONT=courier new]apache2[/FONT]. I have cloned the remote repo to my HDD, and set up over the local server with symlinks and all. However, when I run [FONT=courier new]sudo apt update[/FONT], I end up with the following error messages:


```

Reading package lists... Done
W: The repository 'http://localhost/apt-mirror/security.ubuntu.com/ubuntu bionic-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://localhost/apt-mirror/security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-i386/Packages  404  Not Found [IP: 127.0.0.1 80]
E: Failed to fetch http://localhost/apt-mirror/dists/bionic/universe/binary-amd64/Packages.xz  File has unexpected size (1799853 != 8569560). Mirror sync in progress? [IP: 127.0.0.1 80]
   Hashes of expected file:
    - Filesize:8569560 [weak]
    - SHA256:39ec12bac1f788ae649d32c138898d49fdec15eee020a9c72ae92a622fb662a0
    - SHA1:93f9e6e9daf1fced3066bb7ea7441f43bac08a62 [weak]
    - MD5Sum:7d4be564b69453633c376bef445ecc26 [weak]
   Release file created at: Thu, 26 Apr 2018 23:37:48 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Indeed, when I compare http://localhost/apt-mirror/dists/bionic/universe/binary-amd64/ with [http://in.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-amd64/](http://in.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-amd64/), I find that [FONT=courier new]Packages.xz[/FONT] file at the two places has different size. Further the [FONT=courier new]dists/bionic/Contents-amd64.gz[/FONT] also has different size. And Archive Manager is unable to extract either of these local copies of the files, indicating that they are corrupted.

Admittedly, I have restarted apt-mirror multiple times - could that have caused the corruption? But this error is not fixed even after running apt-mirror multiple times, 

What could be causing this error, and how do I proceed to fix it?

Following is my /etc/apt/mirror.list:
```

############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############


deb http://in.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse
deb-amd64 http://in.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse
deb-i386 http://in.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse


deb http://in.archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-amd64 http://in.archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-i386 http://in.archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse


deb http://in.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-amd64 http://in.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-i386 http://in.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


# deb http://security.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse


clean http://in.archive.ubuntu.com/ubuntu/


```

---

### Post by digikar on 2019-03-15
Okay, I wonder why I didn't try this before: the simple fix was to manually replace the [COLOR=#000000]http://localhost/apt-mirror/dists/bionic/universe/binary-amd64/Contents.xz file with the appropriate file.[/COLOR]

---

