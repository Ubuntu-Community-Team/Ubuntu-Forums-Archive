---
title: "My Sources list is a mess. Everytime I update &amp;&amp; upgrade I get multiple errors"
date: 2022-10-31
forum: General Help
---

### Post by mikber18 on 2022-10-31
Hello, 

Please could you help me. I feel like this should really not be happening. Every time I do sudo apt update && sudo apt upgrade I get a million error messages. 

Whilst I can just ignore them and carry on, I want to understand what the message is and actually, how to fix it so its not so messy. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291208&stc=1[/IMG]

Please help, 
Many Thanks

---

### Post by QIII on 2022-10-31
Hello.

Would you please copy and paste the entire text and post it between code tags?  That will make it much easier for us to help.  Your image may be difficult for some to make out.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

That said, it appears that you may have a sources.list that is a mess of repeated sources.

Please also post the results of 

```
cat /etc/apt/sources.list
```

---

### Post by ActionParsnip on 2022-10-31
What is the output of:
```

cat -n /etc/apt/sources.list

```
and
```

cat -n /etc/apt/sources.list.d/nala-sources.list

```

Remember to use code tags to separate the text

---

### Post by oldos2er on 2022-10-31
When you run ```
sudo apt update
``` APT checks both /etc/apt/sources.list and any *.list files in /etc/apt/sources.list.d/. If the same repository is referenced in both those places you will see the warning ```
...is configured multiple times...
``` telling you where.

---

### Post by mikber18 on 2022-10-31
> **QIII said:**
> Hello.

Would you please copy and paste the entire text and post it between code tags?  That will make it much easier for us to help.  Your image may be difficult for some to make out.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

That said, it appears that you may have a sources.list that is a mess of repeated sources.

Please also post the results of 

```
cat /etc/apt/sources.list
```

```

 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease
  The following signatures couldn't be verified because the public key is not 
available: NO_PUBKEY 76F1A20FF987672F
&#9581;&#9472; Updating Package List &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;
&#9474;No Change: https://ppa.launchpadcontent.net/papirus/papirus/ubuntu jammy InRe…&#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-security InRelease [110 …&#9474;
&#9474;No Change: https://ppa.launchpadcontent.net/yktooo/ppa/ubuntu jammy InRelease &#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packag…&#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packa…&#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-1…&#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 D…&#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64…&#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-backports/universe amd64…&#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-security/main amd64 DEP-…&#9474;
&#9474;Updated:   http://gb.archive.ubuntu.com/ubuntu jammy-security/universe amd64 …&#9474;
&#9474;Fetched 1.8 MB in 0s (0 Bytes/s)                                              &#9474;
&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;
Warning: Target Translations (restricted/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target Translations (restricted/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Error: The repository 'https://dl.winehq.org/wine-builds/ubuntu jammy InRelease' is not signed.
Warning: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: GPG error: https://dl.winehq.org/wine-builds/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Warning: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Translations (multiverse/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target Translations (multiverse/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:3
Warning: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list.d/nala-sources.list:5
Warning: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:26 and /etc/apt/sources.list.d/nala-sources.list:5

```





```

 1    # deb cdrom:[Ubuntu 22.04 LTS _Jammy Jellyfish_ - Release amd64 (20220419)]/ jammy main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://gb.archive.ubuntu.com/ubuntu/ jammy main restricted
     6    # deb-src http://gb.archive.ubuntu.com/ubuntu/ jammy main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://gb.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    11    # deb-src http://gb.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://gb.archive.ubuntu.com/ubuntu/ jammy universe
    17    # deb-src http://gb.archive.ubuntu.com/ubuntu/ jammy universe
    18    deb http://gb.archive.ubuntu.com/ubuntu/ jammy-updates universe
    19    # deb-src http://gb.archive.ubuntu.com/ubuntu/ jammy-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://gb.archive.ubuntu.com/ubuntu/ jammy multiverse
    27    # deb-src http://gb.archive.ubuntu.com/ubuntu/ jammy multiverse
    28    deb http://gb.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    29    # deb-src http://gb.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://gb.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    37    # deb-src http://gb.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    38    
    39    deb http://gb.archive.ubuntu.com/ubuntu/ jammy-security main restricted
    40    # deb-src http://security.ubuntu.com/ubuntu jammy-security main restricted
    41    deb http://gb.archive.ubuntu.com/ubuntu/ jammy-security universe
    42    # deb-src http://security.ubuntu.com/ubuntu jammy-security universe
    43    deb http://gb.archive.ubuntu.com/ubuntu/ jammy-security multiverse
    44    # deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse
    45    
    46    # This system was installed using small removable media
    47    # (e.g. netinst, live or single CD). The matching "deb cdrom"
    48    # entries were disabled at the end of the installation process.
    49    # For information about how to configure apt package sources,
    50    # see the sources.list(5) manual.

```

```

cat -n /etc/apt/sources.list.d/nala-sources.list
     1    # Sources file built for nala
     2    
     3    deb http://gb.archive.ubuntu.com/ubuntu/ jammy restricted multiverse
     4    
     5    deb http://gb.archive.ubuntu.com/ubuntu/ jammy restricted multiverse
     6    
     7    

```

---

### Post by mikber18 on 2022-10-31
I feel like my list has reduced although still not fixed

```
 Err:9 http://mirror.deace.id/ubuntu jammy InRelease                                        
  400  Bad Request [IP: 185.53.177.54 80]
Hit:10 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu jammy InRelease                    
Get:11 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease [8,041 B]
Hit:12 https://ppa.launchpadcontent.net/yktooo/ppa/ubuntu jammy InRelease                      
[COLOR=#ff0000]Err:11 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Reading package lists... Done[/COLOR]
E: Failed to fetch http://mirror.deace.id/ubuntu/dists/jammy/InRelease  400  Bad Request [IP: 185.53.177.54 80]
E: The repository 'http://mirror.deace.id/ubuntu jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
[COLOR=#ff0000]W: GPG error: https://dl.winehq.org/wine-builds/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu jammy InRelease' is not signed.
[/COLOR]N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by mikber18 on 2022-11-01
This issue is now resolved in that I have removed Nala completely, which was causing the duplicate and all sorts of errors I was getting. Thank you all for your help.

---

