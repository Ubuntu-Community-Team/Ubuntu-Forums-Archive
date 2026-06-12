---
title: "Can't find my keys."
date: 2016-11-22
forum: General Help
---

### Post by moteprime on 2016-11-22
I have an old pgp key i made and synced to ubuntu key servers years ago.
The hole gpg and keys subject are still somewhat hard for me to figure out, but i'm trying.

I have a xxx.pgp file and a xxx.asc file. I have imported them both into seahorse "Password and keys", but they never appears under the Gnupgp keys or anywhere else in seahorse?

Doing a (i put in xxxxxxxxxxxxxxx instead of my full name and mail, it's kinda unique) 

> mads@Ubuntu1604-L450:~$ gpg --list-keys
/home/mads/.gnupg/pubring.gpg
-----------------------------
pub    768D/DDA1745C 2010-04-07
uid                  xxxxxxxxxxxxxxx <xxxxxxx@gmail.com>
sub    768g/B076D60B 2010-04-07

pub   2048R/AEFDA8A6 2015-01-29
uid                  xxxxxxxxxxxxxxx <xxxxxxx@gmail.com>
uid                  [jpeg image of size 3538]
sub   2048R/58B95EAA 2015-01-29

pub   2048R/2D6D2988 2015-01-29
uid                  xxxxxxxxxxxxxxx <xxxxxxx@gmail.com>
sub   2048R/D709773A 2015-01-29


---

### Post by moteprime on 2016-12-06
Bump ?

---

### Post by kinghov on 2016-12-06
[COLOR=#111111][FONT=Ubuntu]Try this, re-download the missing keys from the Ubuntu key server.

[/FONT][/COLOR]NOTE: Your hexadecimal numbers may be different then mine, so make sure to use the hexadecimals numbers in your error, not mine.


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: Failed to fetch [http://ppa.launchpad.net/chromium-da...jaunty/Release](http://ppa.launchpad.net/chromium-da...jaunty/Release)
W: Some index files failed to download, they have been ignored, or old ones used instead.








The fix for this is to re-download the keys using the hexidecimal numbers given in the error .
Type this command into the terminal ("Applications > Accessories > Terminal" OR press "Ctrl-Alt-Del")
Code:


sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys


And then add the hexadecimal numbers to the command (again, these are my keys from my error. Make sure to use your own):


sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6D975C4791E7EE5E 5A9BF3BB4E5E17B5 7FB8BEE0A1F196A8




The output should look like this:


"gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com"


[https://ireportdaily.com/justice-league-2017-soundtrack-complete-song-list](https://ireportdaily.com/justice-league-2017-soundtrack-complete-song-list)

NOTE: Your hexadecimal numbers may be different then mine, so make sure to use the hexadecimals numbers in your error, not mine.

---

### Post by vasa1 on 2016-12-06
Please note that copy/pasting large chunks from elsewhere without attribution isn't decent: [http://naveenubuntu.blogspot.in/2011/08/fixing-gpg-keys-in-ubuntu.html](http://naveenubuntu.blogspot.in/2011/08/fixing-gpg-keys-in-ubuntu.html)

I can't be bothered finding out whether that content is original or not :)

---

### Post by moteprime on 2016-12-06
@kinghov 
I appreciate your help, but it seems the guy you copied from are having problems with the keys to repositores, not GPG keys.

---

### Post by Dennis N on 2016-12-06
You say you have key files, so I would import the keys from the terminal with **gpg --import <key-file-name>**
Did you use this command? If not, perhaps then they will appear for the Seahorse.

---

### Post by moteprime on 2016-12-06
The keys have been imported, i could se them with gpg --list-keys.
I have  found out something though. It seems that Seahorse doesn't use gpg, but gpg2 which are not the same, after importing the keys with gpg2 in terminal, somehow the gpg keyring got 'upgraded' to gpg2. It looks like the four keys in the gpg ring are now deleted and one key showed on in seahorse. The same i can see with gpg2.

---

### Post by dragonfly41 on 2016-12-06
Y PPA Manager is a useful tool .. installed under System Tools.

[https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager](https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager)

Click on Advanced tab for GPG key management.

---

### Post by Dennis N on 2016-12-06
[http://superuser.com/questions/655246/are-gnupg-1-and-gnupg-2-compatible-with-each-other](http://superuser.com/questions/655246/are-gnupg-1-and-gnupg-2-compatible-with-each-other)
explains why some keys won't display from the other version.
But, the versions are interchangeable w.r.t. data, it says.
Good to know.

---

### Post by moteprime on 2016-12-06
Now that i know the source of the problem, i find hundreds of others having this problem.
Some sort of pop-up warning would have been real nice.
 - This is why people don't use encryption, it's just plain difficult.

---

