---
title: "getting a copy that the md5 match"
date: 2015-08-01
forum: General Help
---

### Post by zeppy2 on 2015-08-01
I have been browsing for a while I want to put xubuntu on a laptop that I have but every version of 14.04.2 that I have downloaded I can't get the Md5 to match up or even be close. it would be great to get a little insite on this if they have to match and or what the risk is if they don't. do I need to do anything with it from going from an Iso to burning it onto a dvd.

---

### Post by QIII on 2015-08-01
Where are you downloading the images from?

---

### Post by NoWayWin8 on 2015-08-01
What utility are you using to check the md5 hashes?

The 32-bit and 64-bit Xubuntu 14.04.2 iso's have these md5 hashes:
```
6f68eb856e2e9c5e5bbde71d9f6502db *xubuntu-14.04.2-desktop-amd64.iso
b840066af2797fa8c973d99110c64c91 *xubuntu-14.04.2-desktop-i386.iso
```
What hashes are you getting?

---

### Post by howefield on 2015-08-01
> **zeppy2 said:**
> I have been browsing for a while I want to put xubuntu on a laptop that I have but every version of 14.04.2 that I have downloaded I can't get the Md5 to match up or even be close.

For a higher chance of an accurate download, try downloading via the torrent links at [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) 

> it would be great to get a little insite on this if they have to match and or what the risk is if they don't. do I need to do anything with it from going from an Iso to burning it onto a dvd.

Yes, they need to match, the risk is that you will have a non bootable/install image.

---

### Post by Lars Noodén on 2015-08-01
> **howefield said:**
> Yes, they need to match, the risk is that you will have a non bootable/install image.

Or that the image is bootable but contains hostile modifications.  These days MD5 should be abandoned for that kind of verification because it is now feasible for smaller shops to generate MD5 collisions.  Ubuntu should be labeling these images with SHA256 instead, as well as in other uses, and deprecate MD5.  I'm not sure where to file the feature request though.  

Here is a description of generating a collision for photos, but ISO images would also be vulnerable as well as .deb packages.  
[http://natmchugh.blogspot.com/2015/02/create-your-own-md5-collisions.html](http://natmchugh.blogspot.com/2015/02/create-your-own-md5-collisions.html)

That said, MD5 is what we have at the moment and it can show whether or not there were accidental errors in the copy.

---

### Post by zeppy2 on 2015-08-01
I have tried xubuntu.org/get xubuntu. I have tried xubuntu.org, linux.softpedia. everyone that I have downloaded the Md5 hash has been way off if anybody knows of a reliable place to download from please give me a little insite I greatly appreciate it.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Lars Noodén on 2015-08-01
Which method are you using to download?  If you use a torrent, it should do checksumming along the way so that when it is finished it will be an accurate copy.  

[http://torrent.ubuntu.com/xubuntu/releases/trusty/release/desktop/xubuntu-14.04.2-desktop-amd64.iso.torrent](http://torrent.ubuntu.com/xubuntu/releases/trusty/release/desktop/xubuntu-14.04.2-desktop-amd64.iso.torrent)
[http://torrent.ubuntu.com/xubuntu/releases/trusty/release/desktop/xubuntu-14.04.2-desktop-i386.iso.torrent](http://torrent.ubuntu.com/xubuntu/releases/trusty/release/desktop/xubuntu-14.04.2-desktop-i386.iso.torrent)

Those are from the [Xubuntu](http://xubuntu.org/getxubuntu/#lts) page.

---

### Post by Lars Noodén on 2015-08-01
> **zeppy2 said:**
> [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Those are probably not authoritative.

Try these:

[http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/14.04/release/](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/14.04/release/)

or from another mirror:

[http://xubuntu.org/getxubuntu/mirrors/](http://xubuntu.org/getxubuntu/mirrors/)

Edit: these are even signed so you can verify the signature to be really sure

---

### Post by mystics on 2015-08-01
> **Lars Noodén said:**
> Ubuntu should be labeling these images with SHA256 instead, as well as in other uses, and deprecate MD5.  I'm not sure where to file the feature request though.

Actually, Xubuntu does offer SHA1 and SHA256 checksums along with the MD5 one, at least if you go to one of the mirror sites on their site.

But as for the original question, it isn't surprising that the md5sums aren't coming close. In a vast majority of cases, even minor changes to the file will cause drastic changes to the md5sum. For instance, if I create a file called hello.txt and originally write:

```
Hello World
```

simply changing it to:

```
Hello World!
```

Will cause a very different output (the top one is the original, while the bottom one is the one with the exclamation mark):

```

mystics@XMac:~$ md5sum hello.txt 
e59ff97941044f85df5297e1c302d260  hello.txt
mystics@XMac:~$ md5sum hello.txt 
8ddd8be4b179a529afa5f2ffae4b9858  hello.txt

```

As you can see, maybe only one or two characters match.

In other words, you don't try to make them close. If *any* change is made to the file, then it normally will be drastically different, and in your case, this change could simply be some data loss due to a bad connection. Actually, it would be much more worrisome if they were near-identical, because then someone has likely put in effort to make them look the same by exploiting weaknesses with the MD5 checksum, and those people probably have malicious intent for their files. (Note: Not all malicious files will have near-identical or identical checksums. It's just a sign of someone putting in more effort.)

But as long as you're using the sources Lars gave you, then things should work. If they don't, then it is probably just a bad connection and you should try again later.

---

### Post by NoWayWin8 on 2015-08-02
> **zeppy2 said:**
> I have tried xubuntu.org/get xubuntu. I have tried xubuntu.org, linux.softpedia. everyone that I have downloaded the Md5 hash has been way off if anybody knows of a reliable place to download from please give me a little insite I greatly appreciate it.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
I'll ask again:

[b]1. What utility are you using to check the md5 hashes?
2. What hashes are you getting?[/b]

If you answer these questions accurately your problem will be quickly solved.

---

