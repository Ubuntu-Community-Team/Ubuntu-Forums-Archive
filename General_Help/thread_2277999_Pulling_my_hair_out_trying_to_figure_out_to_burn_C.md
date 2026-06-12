---
title: "Pulling my hair out trying to figure out to burn CDI image in Ubuntu"
date: 2015-05-13
forum: General Help
---

### Post by Hakachukai on 2015-05-13
I'm trying to burn some DreamCast disc images for homebrew stuff.

I've downloaded various versions of the Utopia boot disc and also the DCHakker image.

The images usually come in CDI ( Discjuggler ) or NRG ( Nero ) file formats.

I use cdi2iso and nrg2iso to convert them, but when I use isoinfo to check the resulting iso files they are always invalid! (K3B also fails to read them)
I've been searching the web for hours looking for solutions and tools to help. I keep running into lots of outdated/broken links and redundant information that is not helpful :-(

Has anyone been able to do this successfully? Is the original image even valid? I don't know what the original md5sum is supposed to be, so I have nothing to verify against.
I downloaded the DChakker image from here: [http://theisozone.com/downloads/dreamcast/homebrew-apps/dchakker-usa/](http://theisozone.com/downloads/dreamcast/homebrew-apps/dchakker-usa/)



```
:~/iso/DreamCast$ uname -a
Linux Machine 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux

:~/iso/DreamCast$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
NAME="Ubuntu"
VERSION="12.04.1 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.1 LTS)"
VERSION_ID="12.04"
```

```
:~/iso/DreamCast$ md5sum Dchakker.rar 
ed9c6c90915901259595a7a63d43b02d  Dchakker.rar

:~/iso/DreamCast$ unrar e Dchakker.rar 

UNRAR 4.00 beta 3 freeware      Copyright (c) 1993-2010 Alexander Roshal


Extracting from Dchakker.rar
```

```
:~/iso/DreamCast$ cdi2iso Dchakker.cdi
:~/iso/DreamCast$ isoinfo -i Dchakker.cdi 
CD-ROM is NOT in ISO 9660 format
```

---

### Post by Hakachukai on 2015-05-13
I found additional info while talking on IRC about this issue:
This took place on Freenode #dreamcastdev

<helpful user>: a CDI file is a disc image
 an ISO file is an image of a single data track
you can't burn a dreamcast disc using an ISO file because dreamcast discs are multi-session
 unfortunately your best bet is to find a windows machine and install discjuggler on it

<Hakachukai>: helpful user, ok, thanks for the info! I'm still determined to find a way to do this in Linux because it seems to be a major long time issue that has been haunting people. So basically I need to find something that can burn a multi-session CD in Linux, then I need to find ( or create ) something that can read the multi-session image contained in the CDI file.
Does that sound correct?

---

### Post by Hakachukai on 2015-05-14
Ok, so after a couple of days of research, help from IRC and even reading through some source code... I found the following solution:

Download a tool called cdirip0.63 from here: [http://dcemulation.org/1-files/tools/pc/mac/cdirip-0.6.3.zip](http://dcemulation.org/1-files/tools/pc/mac/cdirip-0.6.3.zip)
It can be compiled for Linux, just make sure that you use the Linux make file.

Once it is compiled you can use it to extract whatever is contained in that CDI image.
Keep in mind that it might be several tracks of different types and formats. Some could be data, some could be audio ( probably other types too )

Once you have your tracks extracted from the CDI image, you can use cdrecord to burn them to CD.

In this case I was working with Dreamcast images, which requires a whole other set of knowledge not relevant to this basic Ubuntu question.
But this answers the basic question of how to burn a CDI image in Ubuntu.

---

