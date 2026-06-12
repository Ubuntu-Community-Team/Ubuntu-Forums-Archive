---
title: "is Veracrypt available for Ubuntu 24.10?"
date: 2024-11-14
forum: General Help
---

### Post by jgwphd on 2024-11-14
I just installed Ubuntu 24.10 and I have external drives that have been prior encrypted with Veracrypt. I can't seem to find a Veracrypt version for this release and don't want to go back to 23.10 (my last prior Ubuntu release). Does anyone know where I could find a Veracrypt version that works on Ubuntu 24.10 or if I can install another utility will access Veracrypt encrypted devices/files? Any guidance is appreciated. Many Thanks.

---

### Post by 1fallen on 2024-11-14
There is a PPA for it but only LTS versions are supported.
Here:[https://launchpad.net/~unit193/+archive/ubuntu/encryption](https://launchpad.net/~unit193/+archive/ubuntu/encryption)

That said I still have it on 25.04 (Non LTS), **but know this if it breaks your system, I won't be responsible....use at your own risk.**

I will say I had no issue's on 24.10 but again YMMV.
```
apt policy veracrypt
veracrypt:
  Installed: 1.26.14-0vanir1~bpo24.04
  Candidate: 1.26.14-0vanir1~bpo24.04
  Version table:
 *** 1.26.14-0vanir1~bpo24.04 500
        500 https://ppa.launchpadcontent.net/unit193/encryption/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```
I edited the "/etc/apt/sources.list.d/unit193-ubuntu-encryption-noble.sources" to read as noble
```
Types: deb
URIs: https://ppa.launchpadcontent.net/unit193/encryption/ubuntu/
Suites: noble
Components: main
Signed-By: 

```

There are Debs available as well but we won't go down that path. ;)

---

### Post by jgwphd on 2024-11-14
"only LTS versions are supported"  ...I don't remember reading that anywhere (but I do rush through things when I expect them to work after using them for years). I had Veracrypt running on 23.10 without any issues.  What is "25.04"? Also, I have a basic "test" system so I am not too worried about breaking it ...especially since you have it working already on 24.10. I just want access to the encrypted drives. 

Let me verify, ...you are saying to add this repository :[https://launchpad.net/~unit193/+arch...ntu/encryption]("https://launchpad.net/~unit193/+archive/ubuntu/encryption")  to my "other software" in "Software & Updates" and then (I assume) I install as usual (for me) "sudo apt install veracrypt" 

You mentioned "I edited the "/etc/apt/sources.list.d/unit193-ubuntu-encryption-noble.sources" to read as noble" I am not sure what to do here. What is "noble"? Is that noble numbat? Could you be a bit more specific about what I should edit.  

Again Many many thanks!!!!

---

### Post by 1fallen on 2024-11-14
Noble is 24.04 and 24.10 is Oracular you will see that with:
```
sudoedit /etc/apt/sources.list.d/unit193-ubuntu-encryption-noble.sources
```
 look for "oracular" and change to noble. Now update and install:
```
sudo apt update && sudo apt install veracrypt
```

This has nothing to do with your thread but 25.04 is Development Plucky(code name) it still runs fine here.

Your 23.10 must have been an Upgrade to  23.10 vs a new install. Other wise it would have been disabled missing the release file.

There now clear as Mud right? LOL

---

### Post by jgwphd on 2024-11-14
Got it. Thanks. Your right I got to 23.10 with an "upgrade" (I been doing fresh installs rather than upgrades - it's more work but I have been advised by a friend of mine who manages Linux servers that a fresh install is a better path - if you have any insight into this let me know). I always assumed that since it worked at 23.10 that it must be supported by 23.10 ...you know what they say about "assume"  :-)  I'll change "oracular" to "noble" for all occurrences in the file. I assume I should put the file back to oracular when I am done the install (that seems obvious but maybe you know something that I don't). One last question, is this the whole URL with "..." and all? :[https://launchpad.net/~unit193/+arch...ntu/encryption]("https://launchpad.net/~unit193/+archive/ubuntu/encryption") 
Again, I very much appreciate your assistance   :-)

---

### Post by davetheoldcoder on 2024-11-14
I haven't tried it, but there's a Linux Generic Installer veracrypt-1.26.14-setup.tar.bz2 at the official VeraCrypt site [https://www.veracrypt.fr/en/Downloads.html](https://www.veracrypt.fr/en/Downloads.html)

My guess is that's independent of the Ubuntu version.

---

### Post by 1fallen on 2024-11-14
Nope your friend is very wise Fresh is the Best suggestion.

Nope no change back oracular leave it at Noble, if worried about your system after a successful veracrypt install just disable the PPA.
Mine remained the same from 22.04 thru 24.04 with no issues.
The Dependencies are not life threatening:
```
[FONT=monospace][COLOR=#000000]apt depends veracrypt [/COLOR]
veracrypt 
  Depends: dmsetup 
    dmsetup:i386 
  Depends: kmod 
    kmod:i386 
  Depends: sudo 
    sudo-ldap:i386 
    sudo-ldap 
    sudo:i386 
  Depends: libayatana-appindicator3-1 (>= 0.2.92) 
  Depends: libc6 (>= 2.38) 
  Depends: libfuse3-3 (>= 3.2.3) 
  Depends: libgcc-s1 (>= 3.3.1) 
  Depends: libglib2.0-0t64 (>= 2.12.0) 
  Depends: libgtk-3-0t64 (>= 3.0.0) 
  Depends: libstdc++6 (>= 11) 
  Depends: libwxbase3.2-1t64 (>= 3.2.4+dfsg) 
  Depends: libwxgtk3.2-1t64 (>= 3.2.4+dfsg) 
 |Recommends: exfatprogs 
  Recommends: <exfat-utils> 
  Recommends: ntfs-3g 
  Recommends: xdg-utils


```[/FONT]
> is this the whole URL with "..." and all? :[https://launchpad.net/~unit193/+arch...ntu/encryption]("https://launchpad.net/~unit193/+archive/ubuntu/encryption")

That address is for you to view with instructions to add it to your system.
Then if it complains about "no release found" then edit the file as suggested.

I'm a sucker for punishment I always inline upgrade, but at times I have to clear out the left over cob-webs...so not a lot time saved in reality.

Happy to help.

---

### Post by 1fallen on 2024-11-14
> **davetheoldcoder said:**
> I haven't tried it, but there's a Linux Generic Installer veracrypt-1.26.14-setup.tar.bz2 at [https://www.veracrypt.fr/en/Downloads.html](https://www.veracrypt.fr/en/Downloads.html)

My guess is that's independent of the Ubuntu version.
Nope not independent made for Debian/Ubuntu.
The Debs are there as well but not a good suggestion I would offer to anyone but myself, We talk of Deb Hell here in UF all the time.

---

### Post by jgwphd on 2024-11-14
Many many thanks for all the information. This is on my "to do" list next week. I'll update how I did when complete. 

Again. **Many thanks for all the information and guidance**. You are a gentleman and a scholar ....and I am a good judge of character  :-)

---

### Post by jgwphd on 2024-11-25
@1fallen, I am just getting back to this... 

(1) I used the terminal command > sudoedit /etc/apt/sources.list.d/unit193-ubuntu-encryption-oracular.sources and **the file only had a PGP Public Key Block**, nothing else in the file. There was no place to change Oracular to Noble. What am I missing? 

(2) Just for fun  :-)  I also tried renaming that same file replacing oracular with noble in the file name > sources.list.d/unit193-ubuntu-encryption-noble.sources but when I do > sudo apt install veracrypt i get > Unable to locate package veracrypt 
(3) For even more fun, I then added [https://launchpad.net/~unit193/+arch...ntu/encryption]("https://launchpad.net/~unit193/+archive/ubuntu/encryption") to software and updates and I got a message that > Malformed entry 1 in /etc/apt/sources.list.d/unit193-ubuntu-encryption-noble.sources when I tried "sudo apt install veracrypt" again I got "Malformed entry 1 in source file /etc/apt/sources.list.d/unit193-ubuntu-encryption-noble.sources (URI parse)"

What am I missing. I very much appreciate your assistance. I haven't been into this repository / install stuff for awhile so I am very rusty. Maybe I am lucky but things usually just work for me, except this time.

BTW, when I do ...$ sudo apt update I also get the same message
Error: Malformed entry 1 in sources file /etc/apt/sources.list.d/unit193-ubuntu-encryption-noble.sources (URI parse)
Error: The list of sources could not be read.

I put everything back ....I think I went wrong at step 1

---

### Post by davetheoldcoder on 2024-11-25
> **1fallen said:**
> The Debs are there as well but not a good suggestion I would offer to anyone but myself, We talk of Deb Hell here in UF all the time.

What's the problem with .deb's? I prefer installing packages from a repository with synaptic or apt, or (in some cases) with snap, but have occasionally installed a package using a downloaded .deb if the package is not available from a repository.

Veracrypt is one of those occasions, since it's maintained by a third party who seems reliable.

---

