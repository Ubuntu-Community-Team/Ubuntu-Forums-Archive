---
title: "Problem verifying iso"
date: 2015-04-26
forum: General Help
---

### Post by tech291083 on 2015-04-26
Hi,

I have been a fan of Linux for quite some time now and Ubuntu has become one of my favourite Linux distros. But for the last one year or so, particularly after downloading and installing the below mentioned 4 versions of Ubuntu 14.04 LTS on one of my hard drives one by one, I have not had time to learn more about it. Now I am back and eager to learn again. 

Ubuntu 14.04 LTS Desktop version 32 bit
Ubuntu 14.04 LTS Desktop version 64 bit
Ubuntu 14.04 LTS Server version 32 bit
Ubuntu 14.04 LTS Server version 64 bit

As I turned my attention to downloading the latest version of Ubuntu again, I just realised that I had a text file with all the instructions on how to verify a downloaded Ubuntu iso, written in an easy to understand manner for myself and many of my Linux loving fans. And now that very file is missing from my pc, probably hiding somewhere, leaving me angry. I am feeling a little frustrated now as I just finished downloading the latest version of Ubuntu Server edition 32 bit ie ubuntu-14.04.2-server-i386.iso from the page below. 

[http://releases.ubuntu.com/14.04.2/](http://releases.ubuntu.com/14.04.2/)

All I remember about verifying a downloaded Ubuntu iso is checking the following checksums in a terminal by executing the following commands (after cd to the downloaded iso folder).

md5sum ubuntu-14.04.2-server-i386.iso
sha1sum ubuntu-14.04.2-server-i386.iso
sha256sum ubuntu-14.04.2-server-i386.iso

They all matched the checksums listed on the site here on 3 separate pages,

[http://releases.ubuntu.com/14.04.2/MD5SUMS](http://releases.ubuntu.com/14.04.2/MD5SUMS)
[http://releases.ubuntu.com/14.04.2/SHA1SUMS](http://releases.ubuntu.com/14.04.2/SHA1SUMS)
[http://releases.ubuntu.com/14.04.2/SHA256SUMS](http://releases.ubuntu.com/14.04.2/SHA256SUMS)

I was all happy after execuring the above 3 commands and about to write the iso to a CD, until I came across the very page that taught me the whole thing about iso image verification. Now, I am trying to follow the instruction on this very page only,

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

But I am stuck on step 1 itself, which reads:

> 
1. Download SHA256SUMS and SHA256SUMS.gpg, or MD5SUMS and MD5SUMS.gpg


I have been able to download the .gpg files immediately for each of the checksum there ie md5sum, sha1sum and sha256sum and saved them to the same folder where the iso image is. Then, I executed the following commands, but gor errors.


```

[john@localhost Linux Distros]$ cd Ubuntu\ Server\ 14.04.2/

[john@localhost Ubuntu Server 14.04.2]$ ls
MD5SUMS.gpg  SHA1SUMS.gpg  SHA256SUMS.gpg  ubuntu-14.04.2-server-i386.iso

[john@localhost Ubuntu Server 14.04.2]$ gpg --verify MD5SUMS.gpg MD5SUMS
gpg: can't open signed data `MD5SUMS'
gpg: can't hash datafile: file open error

[john@localhost Ubuntu Server 14.04.2]$ gpg --verify SHA1SUMS.gpg SHA1SUMS
gpg: can't open signed data `SHA1SUMS'
gpg: can't hash datafile: file open error


[john@localhost Ubuntu Server 14.04.2]$ gpg --verify SHA256SUMS.gpg SHA256SUMS
gpg: can't open signed data `SHA256SUMS'
gpg: can't hash datafile: file open error


```

I am wondering as to what I am verify the .gpg files against? How do I download md5sums, sha1sums and sha256sums, as there are only web pages? Please guide me. Thanks.

---

### Post by sudodus on 2015-04-26
It seems you have only the gpg files and the iso file.

Did you download the file MD5SUMS? (And/or the files SHA1SUMS and SHA256SUMS?) You need that file (those files) too for the gpg command to work.

The signature is in the gpg file and the sums that you want to verify are in the file MD5SUMS (and/or the files SHA1SUMS and SHA256SUMS).

---

### Post by Holger_Gehrke on 2015-04-26
The 'MD5SUMS.gpg','SHA1SUMS.gpg' and 'SHA256SUMS.gpg' files contains encrypted digests for the file 'MD5SUMS', 'SHA1SUMS' and 'SHA256SUMS'. You are missing the files 'MD5SUMS','SHA1SUMS' and 'SHA256SUMS'. By importing the key as described in the page [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto) and checking the *SUMS file against *SUMS.gpg you're making sure that the check sums in the file haven't been manipulated. After verifying the check sums with the key you check the iso against the check sums.

---

### Post by tech291083 on 2015-04-26
> **sudodus said:**
> It seems you have only the gpg files and the iso file.

Did you download the file MD5SUMS? (And/or the files SHA1SUMS and SHA256SUMS?) You need that file (those files) too for the gpg command to work.

The signature is in the gpg file and the sums that you want to verify are in the file MD5SUMS (and/or the files SHA1SUMS and SHA256SUMS).

I am a little confused here? Where do I download the *SUMS from? Now, I just read on the same page ie the following page, this line

> Just download the two files from any of the mirrors. 


[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

Now how do I find the mirrors? OK, Here they are, but I checked a few of them and they all seem to have the same directory structure as the official Ubuntu site, I failed to locate *SUMs.txt files on any of the mirrors. All of them that I checked seem to contain a web page for each of the three checksums ie md5sum, sha1sum and sha256sum, this is I am very much aware of. Where can I find *SUMS.txt files to verify against .gpg files if that is the case. Thanks.

---

### Post by coffeecat on 2015-04-26
There's a bit of a labyrinth in the community help pages with regard to ISOs, hashes and relevant material. I start here when recommending links:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Which leads to:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Which in turn leads to:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

That last hasn't been updated with the 15.04 hashes yet, but it should have the 14.04 hashes you need.

---

### Post by Holger_Gehrke on 2015-04-26
> **tech291083 said:**
> I failed to locate *SUMs.txt files on any of the mirrors. All of them that I checked seem to contain a web page for each of the three checksums ie md5sum, sha1sum and sha256sum, this is I am very much aware of. Where can I find *SUMS.txt files to verify against .gpg files if that is the case. Thanks.

Not "*SUMs.txt", just "*SUMS" ...

If you look at the very top of the directory listing at [http://releases.ubuntu.com/14.04.2/](http://releases.ubuntu.com/14.04.2/) you'll see MD5SUMS as the very first entry, SHA1SUMS as the fifth and SHA256SUMS as the seventh. Just download those files (in ff: right click on the file, "save target as" (or something to that effect, re-translated from German); these aren't web-pages but simple text files.

---

### Post by tech291083 on 2015-04-26
> **Holger_Gehrke said:**
> Not "*SUMs.txt", just "*SUMS" ...

If you look at the very top of the directory listing at [http://releases.ubuntu.com/14.04.2/](http://releases.ubuntu.com/14.04.2/) you'll see MD5SUMS as the very first entry, SHA1SUMS as the fifth and SHA256SUMS as the seventh. Just download those files (in ff: right click on the file, "save target as" (or something to that effect, re-translated from German); these aren't web-pages but simple text files.

Oh, thank God, at last, you got my point. I was looking for *SUMS.txt files. There was not clear guidelines saying one can just right click and save these SUMS in web pages as txt files. 

Ok, then here in the attached image you will see that I have done the same. I am using Fedora 20 right now, so my screenshot might look a bit different to you, apologies for that. Here I first go to

[http://releases.ubuntu.com/14.04.2/](http://releases.ubuntu.com/14.04.2/)

Then save each of the SUMS pages as text files as shown in the attached screen shots. Please have a look a them. Thanks. Now please tell me the steps.

Meantime, I did the following which I always do and all the 3 SUMs seem to match. I want to learn how to verify the signature using gpg command, so please feel free to guide me. That page ie - [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)   - confuses me a bit (although my fault). Thanks.

```
[john@localhost Linux Distros]$ cd Ubuntu\ Server\ 14.04.2/
[john@localhost Ubuntu Server 14.04.2]$ ls
MD5SUMS      SHA1SUMS      SHA256SUMS      ubuntu-14.04.2-server-i386.iso
MD5SUMS.gpg  SHA1SUMS.gpg  SHA256SUMS.gpg


[john@localhost Ubuntu Server 14.04.2]$ md5sum ubuntu-14.04.2-server-i386.iso 
6478187442f331631b65f886cdd229ce  ubuntu-14.04.2-server-i386.iso


[john@localhost Ubuntu Server 14.04.2]$ sha1sum ubuntu-14.04.2-server-i386.iso 
80b1a915f42cc298855bd4e298f5bfbeb61d800e  ubuntu-14.04.2-server-i386.iso


[john@localhost Ubuntu Server 14.04.2]$ sha256sum ubuntu-14.04.2-server-i386.iso 
76524ab9502a34b983ed56af2d5a72835ce41aec1e2b4c0cb7788ef596958ed6  ubuntu-14.04.2-server-i386.iso



```

---

### Post by tech291083 on 2015-04-26
Here are the screen shots, thanks.

---

### Post by Holger_Gehrke on 2015-04-26
Well, the next step according to [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto) is to check the public key signature:```

gpg --verify SHA256SUMS.gpg SHA256SUMS

```
This will give you an error because you don't have the key and tell you the id of the key you need.
So next you get the key:```

gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 0x"the id of the key you got in the previous step"

```
This will download the public CD signing key (and will probably output some warnings about the key not being signed by anyone trustworthy, gpg is based on the "web of trust" model; if you don't normally use gpg, you don't have any keys that are considered trustworthy on the keyring; gpg uses public key cryptography, keys always exist in pairs - one public and one secret; anything encrypted with one of the keys can be decrypted with the other. For signing, a hash of the data to be signed is generated and encrypted with the secret key; the receiver of the data takes the data and the encrypted hash , generates a hash of the data too, decrypts the received hash and compares it to the hash he calculated; if the two match, the data wasn't changed.) 
So now you can verify the checksum files ```

gpg --verify MD5SUMS.gpg MD5SUMS
or
gpg --verify SHA1SUMS.gpg SHA1SUMS
or
gpg --verify SHA256SUMS.gpg SHA256SUMS

```

If everything works as expected, gpg should tell you that the signature is correkt (and repeat any warnings about the key not being trustworthy ...). So now we know the sums haven't been manipulated after the signature was made. We can now use the sums to verify the iso.
```

md5sums -c MD5SUMS

```
This will check all the files in the MS5SUMS file against the sums stored in the file (and give you tons of errors for all the iso files you don't have ...).

---

### Post by phyrius2 on 2016-01-23
Sorry to necro this thread, but I wasn't sure a new thread was warranted.  I'm stuck on the first step identified by Holger_Gehrke (and thanks, Holger, for the very detailed walkthrough! much appreciated.) I have verified that I do have the sha256sum and sha256sum.gpg files in the same directory as my iso download. However, typing this

```
gpg --verify SHA256SUMS.gpg SHA256SUMS
```

I get this

```
gpg: can't open 'SHA256SUMS.gpg'
gpg: verify signatures failed: file open error
```

What to do? My understanding is I need this step to identify the key I need for verification. :?

---

