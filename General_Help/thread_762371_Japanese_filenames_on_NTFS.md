---
title: "Japanese filenames on NTFS"
date: 2008-04-22
forum: General Help
---

### Post by HyperHacker on 2008-04-22
I can't seem to rename files to Japanese names on an NTFS volume. I get the error: Failed to rename "xxxx.flac". Invalid or incomplete multibyte or wide character.

Couple names I've tried:
&#38632;&#12354;&#12364;&#12426;.flac
7&#20154;&#12398;&#40614;&#12431;&#12425;&#28023;&#36042;&#22243; - Family &#65374;7&#20154;&#12398;&#40614;&#12431;&#12425;&#28023;&#36042;&#22243;&#31687;&#65374;.flac

I can create them on EXT3 volumes.

---

### Post by Rocket2DMn on 2008-04-22
I don't have an immediate answer for you, but I think the problem may be with mount options that you used.  If the drive is internal and has an fstab entry, it might have mount options that look like this:
```
defaults,locale=en_US.utf8
```
It may help to change that to something like
```
defaults,locale=ja_JP.utf8
```
I am unsure on the exact syntax or naming of that.  You can use this to check what's already available on your system:
```
locale -a
```
It seems like you may need to install a locales package and generate the settings yourself - see [http://ntfs-3g.org/support.html#locale](http://ntfs-3g.org/support.html#locale)

If the drive is external, you need to mount it with the locale=(whatever) option, see [http://linux.die.net/man/8/ntfs-3g](http://linux.die.net/man/8/ntfs-3g)

---

### Post by HyperHacker on 2008-04-22
It does have an entry:
UUID=3946E0111DAD4874 /media/hda9     ntfs    defaults,umask=007,gid=46 0       1
Changing the default to Japanese doesn't seem like a good idea, there are a lot of files with English names and only a couple with Japanese names. Wouldn't that cause trouble with the English ones? Especially since this partition is used by Windows too.

```
hyperhacker@Mercury:~$ locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
ja_JP.utf8
POSIX
```

---

### Post by tomcheng76 on 2008-04-22
Try
> 
UUID=3946E0111DAD4874 /media/hda9 ntfs-3g defaults,locale=en_US.utf8,umask=007,gid=46 0 1

The above QUOTE is one line only

btw, i hate UUID, i suggest changing "UUID=3946E0111DAD4874" to /dev/hda9

---

### Post by Rocket2DMn on 2008-04-22
> **HyperHacker said:**
> It does have an entry:
UUID=3946E0111DAD4874 /media/hda9     ntfs    defaults,umask=007,gid=46 0       1
Changing the default to Japanese doesn't seem like a good idea, there are a lot of files with English names and only a couple with Japanese names. Wouldn't that cause trouble with the English ones? Especially since this partition is used by Windows too.

```
hyperhacker@Mercury:~$ locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
ja_JP.utf8
POSIX
```

I'm not 100% sure, it may depend on the encoding of the Japanese locale, if it allows for western characters or not.  You can add the "ro" option to the fstab entry which will mount it as read only, that might be a good way to test it out without putting the filesystem at risk.
```
UUID=3946E0111DAD4874 /media/hda9     ntfs    defaults,umask=007,gid=46,locale=ja_JP.utf8,ro 0       1
```
I think it should be OK because utf8 is backwards compatible with ascii, which includes all the western alphanumeric characters.
Be sure to remove the "ro" option when you're good to go.

> **tomcheng76 said:**
> Try

The above QUOTE is one line only

btw, i hate UUID, i suggest changing "UUID=3946E0111DAD4874" to /dev/hda9

UUIDs can be annoying when you're trying to figure out what is what, but it can be useful in multiple drive systems that runs the risk of having the device recognition changing between boots.  It's really a matter of preference, both will work, I just make an effort to use UUID when possible/appropriate.

---

