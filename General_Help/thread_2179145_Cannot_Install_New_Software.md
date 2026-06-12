---
title: "Cannot Install New Software"
date: 2013-10-06
forum: General Help
---

### Post by BlacklightHalo on 2013-10-06
While trying to install new software from Ubuntu Software center in KDE, I am denied and given the following error where normally I would be asked for my administrative password:

[ATTACH=CONFIG]246790[/ATTACH]

This is happening in Kubuntu 13.04 on an HP E2 Vision desktop computer. Could anyone give me some ideas as to how I might fix this?

Thank you,

-Val

---

### Post by Bashing-om on 2013-10-06
BlacklightHalo; Hi !

Command line tools will yield better indications of where the problem lies:
Please post the outputs - Between Code (#) Tags - of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
As a good place to start troubleshooting.

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by BlacklightHalo on 2013-10-10
Bashin-om, thanks for your reply.

```
Err http://packages.medibuntu.org raring/free amd64 Packages                                        
  404  Not Found
Err http://packages.medibuntu.org raring/non-free amd64 Packages                                    
  404  Not Found
Err http://packages.medibuntu.org raring/free i386 Packages                                         
  404  Not Found
Err http://packages.medibuntu.org raring/non-free i386 Packages                                     
  404  Not Found
Fetched 1,555 kB in 12s (120 kB/s)                                                                  
W: GPG error: http://www.openprinting.org lsb3.1 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A4B44C2D2A2203E
W: Failed to fetch http://packages.medibuntu.org/dists/raring/free/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/dists/raring/non-free/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/dists/raring/free/binary-i386/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/dists/raring/non-free/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

^This is the result of sudo apt-get update.

sudo apt-get updgrade seems to have gone straight through with no problems. I'm seeing no error messages, etc.

---

### Post by Bashing-om on 2013-10-10
BlacklightHalo; Hi !

The medibuntu repository is no longer maintained. Sad, perhaps, it made things a lot easier in may respects.
see:
[http://ubuntuforums.org/showthread.php?t=2174110](http://ubuntuforums.org/showthread.php?t=2174110)
To your issue;
Uncheck that source - Software Sources -> Other Software, is the simplest way.
Reboot and then see what the new status is in terminal,
Terminal codes once more:
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]workie great last long time
[/INDENT][/INDENT]

---

### Post by BlacklightHalo on 2013-10-10
Done. At this point, sudo apt-get update returns,

```
W: GPG error: http://www.openprinting.org lsb3.1 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A4B44C2D2A2203E


```

---

### Post by Bashing-om on 2013-10-10
BlacklightHalo; hey,
As the source :
[www.openprinting.org](www.openprinting.org)
is a trusted site, you may authenticate the software request by:
- copy and paste to preclude typos - individual lines as separate commands -
```

gpg --keyserver keyserver.ubuntu.com --recv 7A4B44C2D2A2203E
gpg --export --armor 7A4B44C2D2A2203E | sudo apt-key add -

``` using this forum as the key-server entity, which I expect the forum server to hold the key.

This is a case of ubuntu protecting you .. making you aware of what software you are installing. 

[INDENT][INDENT]ain't ubuntu wonderful
[/INDENT][/INDENT]

---

### Post by edwinpallens on 2013-12-17
I still getting the GPG Error how can I find what is this and how I can take it out

---

### Post by monkeybrain20122 on 2013-12-17
To fix the GPG error:

[http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)

The first option is easiest. Install launchpad-getkeys and just run it in the terminal.

---

