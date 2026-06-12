---
title: "Error Updating: &quot;ubuntu update encounter a section with no package header&quot;"
date: 2013-09-01
forum: General Help
---

### Post by canciondegozo on 2013-09-01
Hi, My computer is giving me this error message:
[ATTACH=CONFIG]245914[/ATTACH]
I have Ubuntu [COLOR=#4E5665][FONT=lucida grande]12.04 LTS. I [/FONT][/COLOR]asked a friend who knows Ubuntu (I'm a clueless blonde, myself) to help and he told me to open the terminal try [COLOR=#4E5665][FONT=lucida grande]sudo rm /var/lib/apt/lists/* -vf and then [/FONT][/COLOR][COLOR=#4E5665][FONT=lucida grande]sudo apt-get update. 
That gave me this error:
[/FONT][/COLOR][COLOR=#4E5665][FONT=lucida grande]Reading package lists... Error![/FONT][/COLOR]
[COLOR=#4E5665][FONT=lucida grande]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error:[/FONT][/COLOR][http://cr.archive.ubuntu.com]("http://cr.archive.ubuntu.com/")[COLOR=#4E5665][FONT=lucida grande] precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/FONT][/COLOR]

[COLOR=#4E5665][FONT=lucida grande]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error:[/FONT][/COLOR][http://extras.ubuntu.com]("http://extras.ubuntu.com/")[COLOR=#4E5665][FONT=lucida grande] precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/FONT][/COLOR]

[COLOR=#4E5665][FONT=lucida grande]W: Failed to fetch [/FONT][/COLOR][http://cr.archive.ubuntu.com/ubuntu/dists/precise/Release](http://cr.archive.ubuntu.com/ubuntu/dists/precise/Release)[COLOR=#4E5665][FONT=lucida grande] [/FONT][/COLOR]

[COLOR=#4E5665][FONT=lucida grande]W: Failed to fetch [/FONT][/COLOR][http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)[COLOR=#4E5665][FONT=lucida grande] [/FONT][/COLOR]

[COLOR=#4E5665][FONT=lucida grande]W: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT][/COLOR]
[COLOR=#4E5665][FONT=lucida grande]E: Encountered a section with no Package: header[/FONT][/COLOR]
[COLOR=#4E5665][FONT=lucida grande]E: Problem with MergeList /var/lib/apt/lists/cr.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages[/FONT][/COLOR]
[COLOR=#4E5665][FONT=lucida grande]E: The package lists or status file could not be parsed or opened.[/FONT][/COLOR]
[COLOR=#4E5665][FONT=lucida grande]bubblytica@bubblytica:~$

My friend says to tell you I already tried the solution at [/FONT][/COLOR][http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742). 
Please help me. 
Thank you!

---

### Post by Bashing-om on 2013-09-01
canciondegozo; Welcome to the forum .

Authorization verification is not related to the prior error. For this situation try:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192

```
 See if that resolves the problem also with the "MergeList /var/lib/apt/lists/cr.archive.ubuntu.com_ubuntu_dists_precise_multive rse_binary-amd64_Packages" error.
Else will have to use other means to address the gpg-error-badsig key verification.
Maybe also that the server/mirror there in Costa Rica has a problem ?? Let's see what results from obtaining the keys from our server.

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

