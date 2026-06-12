---
title: "Bug: Due to limited resources (in apt)„Public key is not available“"
date: 2013-12-25
forum: General Help
---

### Post by zika on 2013-12-25
13.10:
```
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://extras.ubuntu.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://download.videolan.org  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9
W: GPG error: http://archive.ubuntu.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://liquorix.net sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EFF4F272FB2CD80
W: GPG error: http://archive.ubuntu.com saucy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://downloads.sourceforge.net all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: GPG error: http://archive.ubuntu.com saucy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com saucy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1EE2FF37CA8DA16B
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0856F197B892ACEA
W: GPG error: http://ppa.launchpad.net saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0856F197B892ACEA
W: GPG error: http://ppa.launchpad.net saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: GPG error: http://ppa.launchpad.net saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542

```
Yes, I've tried on that users machine (among other things)
1. to add all offending keys 
```
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys xxx..xx
```
I get```
:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.GFjbVVpZdC --trustdb-name /etc/apt//trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d//atareao-atareao.gpg --keyring /etc/apt/trusted.gpg.d//canonical-kernel-team-ppa.gpg --keyring /etc/apt/trusted.gpg.d//canonical-qt5-edgers-qt5-proper.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-squeeze-automatic.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-squeeze-stable.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-wheezy-automatic.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-wheezy-stable.gpg --keyring /etc/apt/trusted.gpg.d//decatf-testy.gpg --keyring /etc/apt/trusted.gpg.d//epkg-e18.gpg --keyring /etc/apt/trusted.gpg.d//gezakovacs-ppa.gpg --keyring /etc/apt/trusted.gpg.d//gnome3-team-gnome3-next.gpg --keyring /etc/apt/trusted.gpg.d//gwendal-lebihan-dev-cinnamon-stable.gpg --keyring /etc/apt/trusted.gpg.d//jacob-media.gpg --keyring /etc/apt/trusted.gpg.d//jacob-nemo.gpg --keyring /etc/apt/trusted.gpg.d//joe-yasi-xorg-related.gpg --keyring /etc/apt/trusted.gpg.d//joe-yasi-yasi.gpg --keyring /etc/apt/trusted.gpg.d//jr-ppa.gpg --keyring /etc/apt/trusted.gpg.d//libreoffice-libreoffice-4-0.gpg --keyring /etc/apt/trusted.gpg.d//libreoffice-libreoffice-4-1.gpg --keyring /etc/apt/trusted.gpg.d//libreoffice-libreoffice-prereleases.gpg --keyring /etc/apt/trusted.gpg.d//marutter-rrutter.gpg --keyring /etc/apt/trusted.gpg.d//mc3man-mplayer-test.gpg --keyring /etc/apt/trusted.gpg.d//mc3man-rbaudiocd-fix.gpg --keyring /etc/apt/trusted.gpg.d//mir-team-staging.gpg --keyring /etc/apt/trusted.gpg.d//mir-team-system-compositor-testing.gpg --keyring /etc/apt/trusted.gpg.d//motumedia-libav-daily.gpg --keyring /etc/apt/trusted.gpg.d//mqchael-pipelight-daily.gpg --keyring /etc/apt/trusted.gpg.d//mqchael-pipelight.gpg --keyring /etc/apt/trusted.gpg.d//nilarimogard-webupd8.gpg --keyring /etc/apt/trusted.gpg.d//no1wantdthisname-ppa.gpg --keyring /etc/apt/trusted.gpg.d//oibaf-graphics-drivers.gpg --keyring /etc/apt/trusted.gpg.d//ricotz-ppa.gpg --keyring /etc/apt/trusted.gpg.d//ricotz-unstable.gpg --keyring /etc/apt/trusted.gpg.d//rvm-smplayer.gpg --keyring /etc/apt/trusted.gpg.d//ubuntu-audio-dev-pulse-testing.gpg --keyring /etc/apt/trusted.gpg.d//ubuntu-sdk-team-ppa.gpg --keyring /etc/apt/trusted.gpg.d//ubuntu-unity-daily-build.gpg --keyring /etc/apt/trusted.gpg.d//ubuntustudio-kernel-linux-lowlatency-sru.gpg --keyring /etc/apt/trusted.gpg.d//videolan-stable-daily.gpg --keyring /etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d//zeitgeist-ppa.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
gpg: keyblock resource `/etc/apt/trusted.gpg.d//videolan-stable-daily.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d//zeitgeist-ppa.gpg': resource limit
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```
```
sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys xxx.xx
```
```
:~$ sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys A040830F7FAC5991
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.anfESJ4VWh --trustdb-name /etc/apt//trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d//atareao-atareao.gpg --keyring /etc/apt/trusted.gpg.d//canonical-kernel-team-ppa.gpg --keyring /etc/apt/trusted.gpg.d//canonical-qt5-edgers-qt5-proper.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-squeeze-automatic.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-squeeze-stable.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-wheezy-automatic.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-wheezy-stable.gpg --keyring /etc/apt/trusted.gpg.d//decatf-testy.gpg --keyring /etc/apt/trusted.gpg.d//epkg-e18.gpg --keyring /etc/apt/trusted.gpg.d//gezakovacs-ppa.gpg --keyring /etc/apt/trusted.gpg.d//gnome3-team-gnome3-next.gpg --keyring /etc/apt/trusted.gpg.d//gwendal-lebihan-dev-cinnamon-stable.gpg --keyring /etc/apt/trusted.gpg.d//jacob-media.gpg --keyring /etc/apt/trusted.gpg.d//jacob-nemo.gpg --keyring /etc/apt/trusted.gpg.d//joe-yasi-xorg-related.gpg --keyring /etc/apt/trusted.gpg.d//joe-yasi-yasi.gpg --keyring /etc/apt/trusted.gpg.d//jr-ppa.gpg --keyring /etc/apt/trusted.gpg.d//libreoffice-libreoffice-4-0.gpg --keyring /etc/apt/trusted.gpg.d//libreoffice-libreoffice-4-1.gpg --keyring /etc/apt/trusted.gpg.d//libreoffice-libreoffice-prereleases.gpg --keyring /etc/apt/trusted.gpg.d//marutter-rrutter.gpg --keyring /etc/apt/trusted.gpg.d//mc3man-mplayer-test.gpg --keyring /etc/apt/trusted.gpg.d//mc3man-rbaudiocd-fix.gpg --keyring /etc/apt/trusted.gpg.d//mir-team-staging.gpg --keyring /etc/apt/trusted.gpg.d//mir-team-system-compositor-testing.gpg --keyring /etc/apt/trusted.gpg.d//motumedia-libav-daily.gpg --keyring /etc/apt/trusted.gpg.d//mqchael-pipelight-daily.gpg --keyring /etc/apt/trusted.gpg.d//mqchael-pipelight.gpg --keyring /etc/apt/trusted.gpg.d//nilarimogard-webupd8.gpg --keyring /etc/apt/trusted.gpg.d//no1wantdthisname-ppa.gpg --keyring /etc/apt/trusted.gpg.d//oibaf-graphics-drivers.gpg --keyring /etc/apt/trusted.gpg.d//ricotz-ppa.gpg --keyring /etc/apt/trusted.gpg.d//ricotz-unstable.gpg --keyring /etc/apt/trusted.gpg.d//rvm-smplayer.gpg --keyring /etc/apt/trusted.gpg.d//ubuntu-audio-dev-pulse-testing.gpg --keyring /etc/apt/trusted.gpg.d//ubuntu-sdk-team-ppa.gpg --keyring /etc/apt/trusted.gpg.d//ubuntu-unity-daily-build.gpg --keyring /etc/apt/trusted.gpg.d//ubuntustudio-kernel-linux-lowlatency-sru.gpg --keyring /etc/apt/trusted.gpg.d//videolan-stable-daily.gpg --keyring /etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d//zeitgeist-ppa.gpg --keyserver hkp://subkeys.pgp.net --recv-keys A040830F7FAC5991
gpg: keyblock resource `/etc/apt/trusted.gpg.d//videolan-stable-daily.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d//zeitgeist-ppa.gpg': resource limit
gpg: requesting key 7FAC5991 from hkp server subkeys.pgp.net
```
and it stalls there...
2. to rebuild /var/lib/apt/lists folder
3. y-ppa-manager
4. ...
I suspect that there is something other missing but can not pinpoint what...

Update&#8321;: [https://bugs.launchpad.net/apt/+bug/1263540](https://bugs.launchpad.net/apt/+bug/1263540) ... It seems that I've found reason... ;)
Update&#8322;: Nope, that did not help that machine either... I'm patient and relentless... ;)

---

### Post by donkult2 on 2013-12-25
**DON'T** "apt-key adv --recv-key". Just don't. Each time you do Eve, Mallory & the rest of the malicious attacker gang laught about you and eat all your cookies!

By adding keys the way you tried you are undermining the whole security concept as this is not a secure way of recieving keys for various reasons (like: hkp is a plaintext protocol, short and even long keyids can be forged, …).


That being said, back to the problem at hand: I would bet a few cristmas presents that its the bug you found, based on the armada of PPAs you seem to have activated, I guess you have also deactivated quiet a few over time. Try if you have empty files in /etc/apt/trusted.gpg.d with:
find /etc/apt/trusted.gpg.d -name '*.gpg' -size 0
if the output seems legit you can remove them with
sudo find /etc/apt/trusted.gpg.d -name '*.gpg' -size 0 -delete
as they don't contribute anything (expect increasing the count of files to be opened making it easier to reach the silly limit).

[please don't see this as an invitation to ping bugreports with links to supportforums. I am feeling generous today, but usually those posts are considered offensive and will have the reverse effect]

As I said in the debian bug, 0.9.10 has a better handling of files while deleting keys, so you will be hit by it only with >= 40 sources. Personally I believe that if you have >= 40 sources, you have an addiction problem and should remove some…
How we are going to solve this gnupg interaction problem in the longrun remains to be seen (and I doubt I will think about it before next year, so don't expect a lot of bugtraffic for now).


Best season's greetings

David

---

### Post by zika on 2013-12-25
> **donkult2 said:**
> **DON'T** "apt-key adv --recv-key". Just don't. Each time you do Eve, Mallory & the rest of the malicious attacker gang laught about you and eat all your cookies!

By adding keys the way you tried you are undermining the whole security concept as this is not a secure way of recieving keys for various reasons (like: hkp is a plaintext protocol, short and even long keyids can be forged, &#8230;).


That being said, back to the problem at hand: I would bet a few cristmas presents that its the bug you found, based on the armada of PPAs you seem to have activated, I guess you have also deactivated quiet a few over time. Try if you have empty files in /etc/apt/trusted.gpg.d with:
find /etc/apt/trusted.gpg.d -name '*.gpg' -size 0
if the output seems legit you can remove them with
sudo find /etc/apt/trusted.gpg.d -name '*.gpg' -size 0 -delete
as they don't contribute anything (expect increasing the count of files to be opened making it easier to reach the silly limit).

[please don't see this as an invitation to ping bugreports with links to supportforums. I am feeling generous today, but usually those posts are considered offensive and will have the reverse effect]

As I said in the debian bug, 0.9.10 has a better handling of files while deleting keys, so you will be hit by it only with >= 40 sources. Personally I believe that if you have >= 40 sources, you have an addiction problem and should remove some&#8230;
How we are going to solve this gnupg interaction problem in the longrun remains to be seen (and I doubt I will think about it before next year, so don't expect a lot of bugtraffic for now).


Best season's greetings

DavidSimply put: I do not have empty files in aforementioned folders... I forgot to put that in the list of things I've checked or You could count that in &#8222;4. ...&#8220;...
Yes, my name is Zika and I'm addict... I'll try to remove some or to live with this bug... I am confident that it will not be difficult to increase that limit... Best luck to all that should try that... I have faith in them...
If you take a look into &#8222;bugreports&#8220; You will find that I'm anything but addict in that case... No &#8222;ping&#8220;-ing or anything similar from me. Rest assured that I will not write there again soon... Thank You for You generosity, I'm sure I did not deserve it but nevertheless I've got it.
Best season's greetings To You too...

Update&#8321;: Ups, I forgot to ask the crucial question: As ignorant as I am, I was, obviously making a mistake of importing keys in way I've mentioned and You've (with reason I guess) disputed. What is the right way, please tell me/us not to make such mistake(s) again in the future... Thank You in advance.

Update&#8322;: If I count right I do have only 41... ;) None was deactivated in recent past and when I deactivate them I do not do that through GUI so there is no relict after that.
Even though You can keep Your Christmas presents that You've bet for Yourself. They are Yours and You've probably deserved them so that would be not a nice bet... I'll get mine soon... I hope...
I've erased 4 of them and everything is OK now. Thank You for help and I wait for answer for U&#8321; so I could learn even more from this occasion... All the best...

---

### Post by donkult2 on 2013-12-26
Ubuntu people… way too many PPAs… ;)

Increasing the limit will be difficult. It might be that you can talk gnupg upstream into increasing it to whatever, but it seems to be impossible for them to remove the limit as in gnupg2 the limit will be "1". So the software doing business with gnupg as apt (e.g. in the form of apt-key) have to modify their behavior completely – in the apt-key case we were moving for two years in the exact opposite direction and discover only now, that this is a dead end. The rework will no doubt be ugly… (as apt-key is ugly and we wanted to get right of it in the long run, but with those limitations imposed by gnupg{,2} we have no choice but to keep and even enlarge it).


Regarding importing keys: You generally don't. Before you can import a key into the trusted.gpg keyring you have to make sure that it is actually the key you want. Otherwise an attacker can trick you into installing the wrong key – which means he can in the future trick you into installing modified packages as much as he wants as for apt everything is in proper order as the information is signed with a trusted key (See the apt-secure manpage for details on the chain of trust which ensures that nobody tempers with the stuff you install).

How you can acquire a key in a trusted way depends on the repository in question and a bit on the culture in the community. For PPAs in Ubuntu I assume it is trusting that the information on the https page can be trusted (aka, that apt-add-repository will do the right thing™). In the Debian universe we have certain keys in the main archive (e.g. pkg-mozilla-archive-keyring) from which you can already download packages securely or you are expected to find a trusted path from you to the key (via the web of trust) – but the idea of "there is a PPA for that" isn't as omni-present as in the Ubuntu world I guess.

In both communities usually not that many people care and just "apt-key adv --recv-key" anyway unchecked, which is very sad, as it means that your system is not as secure as it could be, but this behavior is at least good for the criminals who need computers to operate their bot networks even if year X is the year of the Linux Desktop I guess… ;)


Regarding the sources: If you don't remove the repositories via the gui I presume that you don't remove the keys associated but just the repository itself. So you might be able to remove some of the (unused) keys (aka: you are a step before the zero-size files).

As said – and it might just be a culture difference – but I really can't imagine a system which uses >= 40 sources. I am not even using that many applications… (were I would care about the version enough so that I would "need" a fresher source. coreutils e.g. includes probably my most-used applications, but any version is fine)

---

### Post by zika on 2013-12-26
About keys: I did trust keys that are on appropriate sites for ppa's... If they are changed by someone, then I could be tricked... I admit that if that was not cultured enough I'm uncultured addict. Even You write they could be trusted. I will forget about using proscribed command, I promise.
I do remove ppa's with **apt-add-repository -r...** I thought that that is th &#8222;right&#8220; way... If it is left I was/am wrong. 
About my addiction: I'll try to loose some weight in list of ppa's but I would not promise anything...
Anyway I've learned a lot from our talk here and I'm grateful to You for that beside the fact that I thank You for all the work in apt SW...

---

### Post by zika on 2014-02-17
Update&#8321;: There is a neat way to squeeze couple of PPAs more through this keyhole of 40...
Look into /etc/apt/trusted.gpg.d and You might find some pairs or triples of same size. Check them with diff and if they are same You can leave only one... ;)

---

